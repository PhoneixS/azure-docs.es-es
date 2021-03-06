---
title: Migración de recursos de IaaS de la implementación clásica a Azure Resource Manager con la CLI de Azure | Microsoft Docs
description: Este artículo le guía por los pasos de migración de recursos compatible con la plataforma desde el modelo de implementación clásica hasta Azure Resource Manager mediante la CLI de Azure.
services: virtual-machines-linux
documentationcenter: ''
author: cynthn
manager: timlt
editor: ''
tags: azure-resource-manager

ms.service: virtual-machines-linux
ms.workload: infrastructure-services
ms.tgt_pltfrm: vm-linux
ms.devlang: na
ms.topic: article
ms.date: 07/19/2016
ms.author: cynthn

---
# Migración de recursos de IaaS de la implementación clásica a Azure Resource Manager con la CLI de Azure
En estos pasos se describe cómo utilizar los comandos de la interfaz de la línea de comandos (CLI) de Azure para migrar recursos de infraestructura como servicio (IaaS) del modelo de implementación clásica al modelo de implementación de Azure Resource Manager. El artículo requiere la [CLI de Azure](../xplat-cli-install.md).

> [!NOTE]
> Todas las operaciones que se describen aquí son idempotentes. Si tiene un problema diferente de una función no admitida o un error de configuración, se recomienda que vuelva a intentar la operación de preparación, anulación o confirmación. De ese modo, la plataforma intentará de nuevo la acción.
> 
> 

## Paso 1: Preparación para la migración
Estos son algunos de los procedimientos recomendados a la hora de evaluar la migración de recursos de IaaS desde el modelo clásico a Resource Manager:

* Consulte la [lista de configuraciones o características no admitidas](virtual-machines-windows-migration-classic-resource-manager.md). Si tiene máquinas virtuales que usan configuraciones o características no admitidas, se recomienda esperar a que se anuncie dicha compatibilidad. Como alternativa, puede quitar esa característica o salir de esa configuración para habilitar la migración si se ajusta a sus necesidades.
* Si tiene actualmente scripts automatizados que implementan la infraestructura y las aplicaciones, intente crear una configuración de prueba similar usando esos scripts para la migración. También puede configurar entornos de ejemplo mediante el Portal de Azure.

## Paso 2: Establecimiento de la suscripción y registro del proveedor
Para los escenarios de migración, debe configurar el entorno para el modelo clásico y el de Resource Manager. [Instale la CLI de Azure](../xplat-cli-install.md) y [seleccione la suscripción](../xplat-cli-connect.md).

Inicie sesión en su cuenta.

    azure login

Seleccione la suscripción de Azure con el siguiente comando.

    azure account set "<azure-subscription-name>"

> [!NOTE]
> El registro es un paso que solo se realiza una vez pero que es necesario antes de intentar la migración. Si no se registra, verá el siguiente mensaje de error:
> 
> *BadRequest : Subscription is not registered for migration.* 
> 
> 

Regístrese con el proveedor de recursos de migración mediante el comando siguiente. Tenga en cuenta que, en algunos casos, se agota el tiempo de espera de este comando. Sin embargo, el registro se realizará correctamente.

    azure provider register Microsoft.ClassicInfrastructureMigrate

Espere cinco minutos a que finalice el registro. Puede comprobar el estado de la aprobación con el siguiente comando. Asegúrese de que RegistrationState sea `Registered` antes de continuar.

    azure provider show Microsoft.ClassicInfrastructureMigrate

Ahora cambie CLI al modo `asm`.

    azure config mode asm

## Paso 3: Verificación para garantizar que dispone de suficientes núcleos de máquina virtual de Azure Resource Manager en la región de Azure de su VNET o implementación actual
Para este paso debe cambiar a modo `arm`. Para ello, ejecute el siguiente comando.

```
azure config mode arm
```

Puede utilizar el siguiente comando de CLI para comprobar la cantidad de núcleos que tiene actualmente en Azure Resource Manager. Para más información acerca de las cuotas de núcleos, consulte [Límites y Azure Resource Manager](../azure-subscription-service-limits.md#limits-and-the-azure-resource-manager).

```
azure vm list-usage -l "<Your VNET or Deployment's Azure region"
```

Una vez comprobado este paso, puede volver a cambiar a modo `asm`.

    azure config mode asm


## Paso 4: Opción 1: Migración de máquinas virtuales de un servicio en la nube
Obtenga la lista de servicios en la nube mediante el siguiente comando y seleccione luego el servicio en la nube que quiera migrar. Tenga en cuenta que si las máquinas virtuales del servicio en la nube están en una red virtual o tienen roles web o de trabajo, recibirá un mensaje de error.

    azure service list

Ejecute el siguiente comando para obtener el nombre de la implementación del servicio en la nube desde la salida detallada. En la mayoría de los casos, el nombre de la implementación es el mismo que el nombre del servicio de nube.

    azure service show <serviceName> -vv

Prepare las máquinas virtuales del servicio en la nube para la migración. Tiene dos opciones para elegir.

Si quiere migrar las máquinas virtuales a una red virtual creada en una plataforma, use el siguiente comando.

    azure service deployment prepare-migration <serviceName> <deploymentName> new "" "" ""

Si quiere migrar a una red virtual existente en el modelo de implementación de Resource Manager, utilice el siguiente comando.

    azure service deployment prepare-migration <serviceName> <deploymentName> existing <destinationVNETResourceGroupName> subnetName <vnetName>

Una vez finalizada la operación de preparación, puede consultar la salida detallada para obtener el estado de migración de las máquinas virtuales y asegurarse de que están en estado `Prepared`.

    azure vm show <vmName> -vv

Compruebe la configuración de los recursos preparados mediante la CLI o el Portal de Azure. Si no está preparado para la migración y desea volver al estado anterior, utilice el siguiente comando.

    azure service deployment abort-migration <serviceName> <deploymentName>

Si la configuración preparada parece correcta, puede continuar y confirmar los recursos mediante el siguiente comando.

    azure service deployment commit-migration <serviceName> <deploymentName>



## Paso 4: Opción 2: Migración de máquinas virtuales de una red virtual
Seleccione la red virtual que quiere migrar. Tenga en cuenta que si la red virtual contiene roles web o de trabajo, o bien máquinas virtuales con configuraciones no admitidas, recibirá un mensaje de error de validación.

Obtenga todas las redes virtuales de la suscripción con el siguiente comando.

    azure network vnet list

El resultado tendrá un aspecto similar al siguiente:

![Captura de pantalla de la línea de comandos con todo el nombre de red virtual resaltado.](./media/virtual-machines-linux-cli-migration-classic-resource-manager/vnet.png)

En el ejemplo anterior, **virtualNetworkName** es todo el nombre **"Group classicubuntu16 classicubuntu16"**.

Prepare la red virtual de su elección para la migración mediante el siguiente comando:

    azure network vnet prepare-migration <virtualNetworkName>

Compruebe la configuración de las máquinas virtuales preparadas mediante la CLI o el Portal de Azure. Si no está preparado para la migración y desea volver al estado anterior, utilice el siguiente comando.

    azure network vnet abort-migration <virtualNetworkName>

Si la configuración preparada parece correcta, puede continuar y confirmar los recursos mediante el siguiente comando.

    azure network vnet commit-migration <virtualNetworkName>

## Paso 5: Migración de una cuenta de almacenamiento
Cuando haya terminado de migrar las máquinas virtuales, se recomienda migrar la cuenta de almacenamiento.

Prepare la cuenta de almacenamiento para la migración mediante el siguiente comando.

    azure storage account prepare-migration <storageAccountName>

Compruebe la configuración de la cuenta de almacenamiento preparada mediante la CLI o el Portal de Azure. Si no está preparado para la migración y desea volver al estado anterior, utilice el siguiente comando.

    azure storage account abort-migration <storageAccountName>

Si la configuración preparada parece correcta, puede continuar y confirmar los recursos mediante el siguiente comando.

    azure storage account commit-migration <storageAccountName>

## Pasos siguientes
* [Migración compatible con la plataforma de recursos de IaaS del modelo clásico al de Azure Resource Manager](virtual-machines-windows-migration-classic-resource-manager.md)
* [Profundización técnica en la migración compatible con la plataforma de la implementación clásica a la de Azure Resource Manager](virtual-machines-windows-migration-classic-resource-manager-deep-dive.md)

<!---HONumber=AcomDC_0907_2016-->