---
title: "Depuración de una aplicación web de Java en Azure mediante Eclipse | Microsoft Docs"
description: "En este tutorial se muestra cómo utilizar el kit de herramientas de Azure para Eclipse con el objetivo de crear una aplicación web de Java que se ejecute en Azure."
services: app-service\web
documentationcenter: java
author: selvasingh
manager: wpickett
editor: 
ms.assetid: 321d2d19-9ce0-4165-8555-b6b15e671393
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: Java
ms.topic: article
ms.date: 12/22/2016
ms.author: asirveda;robmcm
translationtype: Human Translation
ms.sourcegitcommit: ff60ebaddd3a7888cee612f387bd0c50799496ac
ms.openlocfilehash: 8a4f22442d030dae602171555bafb3733d61ebd7


---
# <a name="debug-a-java-web-app-on-azure-in-eclipse"></a>Depuración de una aplicación web de Java en Azure mediante Eclipse
En este tutorial se muestra cómo depurar una aplicación web de Java que se ejecuta en Azure mediante el [kit de herramientas de Azure para Eclipse]. Por simplicidad, en este tutorial se utilizará un ejemplo básico de Java Server Page (JSP), pero los pasos serían similares para depurar un servlet de Java en Azure.

Cuando haya terminado este tutorial, la aplicación se parecerá a la que se muestra en la siguiente ilustración al depurarla en Eclipse:

![][01]

## <a name="prerequisites"></a>Requisitos previos
* Un kit para desarrolladores de Java (JDK) de la versión 1.8 o superior.
* Eclipse IDE para Java EE Developers, Indigo o superior. Se puede descargar en <http://www.eclipse.org/downloads/>.
* Una distribución de un servidor web basado en Java o un servidor de aplicaciones, como Apache Tomcat o Jetty.
* Una suscripción a Azure, que se puede adquirir en <https://azure.microsoft.com/es-es/free/> o <http://azure.microsoft.com/pricing/purchase-options/>.
* El kit de herramientas de Azure para Eclipse. Para más información, consulte [Instalación del kit de herramientas de Azure para Eclipse].
* Un proyecto web dinámico creado e implementado en el Servicio de aplicaciones de Azure; por ejemplo, consulte [Creación de una aplicación web Hello World para Azure en Eclipse].

## <a name="to-debug-a-java-web-app-on-azure"></a>Pasos para depurar una aplicación web de Java en Azure
Para completar los pasos de esta sección puede usar un proyecto web dinámico existente que ya haya implementado como aplicación web de Java en Azure, descargar un [proyecto web dinámico de ejemplo] y seguir los pasos de [Creación de una aplicación web Hello World para Azure en Eclipse] para implementarla en Azure. 

1. Abra Eclipse.
2. Configure los tiempos de espera para la depuración remota:
   
   1. Haga clic en el menú **Windows** (Ventanas) de Eclipse y, luego, en **Preferences** (Preferencias).
   2. Expanda el nodo **Java** y seleccione **Debug** (Depurar).
   3. Configure los valores **Debugger timeout (ms)** (Tiempo de espera del depurador [ms]) y **Launch timeout (ms)** (Tiempo de espera de inicio [ms]) en `120000`.
      
       ![][02]
   4. Haga clic en **OK** (Aceptar) para cerrar el cuadro de diálogo **Preferences** (Preferencias).
3. En la vista del Explorador de proyectos de Eclipse, haga clic con el botón derecho en el proyecto web dinámico que ha implementado en Azure. Cuando aparezca el menú contextual, seleccione **Debug As** (Depurar como) y, después, haga clic en **Azure Web App** (Aplicación web de Azure).
   
    ![][03]
4. Si es la primera vez que depurando el proyecto web dinámico, se abrirá el cuadro de diálogo **Debug Configurations** (Configuraciones de depuración). Puede aceptar los valores predeterminados que especifica el kit de herramientas de la pestaña **Connect** (Conectar). En la pestaña **Source** (Origen), haga clic en **Add** (Agregar) y, después, en **Java project** (Proyecto de Java), seleccione **Dynamic Web Project** (Proyecto web dinámico) y haga clic en **OK** (Aceptar). Cuando haya completado estos pasos, haga clic en **Debug** (Depurar).
   
    ![][04]
5. Cuando se le pregunte si desea **habilitar ahora la depuración remota en la aplicación web remota**, haga clic en **OK** (Aceptar).
6. Cuando se le indique que la **aplicación web ya está lista para la depuración remota**, haga clic en **OK** (Aceptar).
   
    ![][05]
7. Cuando vuelva a aparecer el cuadro de diálogo **Debug Configurations** (Configuraciones de depuración), haga clic en **Debug** (Depurar).
8. Un símbolo del sistema de Windows o el shell de Unix abrirán y prepararán la conexión necesaria para realizar la depuración. Antes de continuar, debe esperar hasta que la conexión a la aplicación web de Java remota se lleve a cabo correctamente. Si usa Windows, el resultado será similar al que se muestra en esta ilustración.
   
    ![][06]
9. Inserte un punto de interrupción en la página JSP; después, abra la dirección URL de la aplicación web de Java en un explorador:
   
   1. Abra el **Explorador de Azure** en Eclipse.
   2. Vaya a **Web Apps** (Aplicaciones web) y a la aplicación web de Java que quiera depurar.
   3. Haga clic con el botón derecho en la aplicación web y, con el izquierdo, en **Open in Browser**(Abrir en el explorador).
   4. Eclipse entrará ahora en el modo de depuración.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre el uso de Azure con Java, vea el [Centro para desarrolladores de Java de Azure].

Para obtener más información sobre cómo crear aplicaciones web de Azure, consulte [Introducción a Aplicaciones web].

[!INCLUDE [app-service-web-try-app-service](../../includes/app-service-web-try-app-service.md)]

<!-- URL List -->

[Azure App Service]: http://go.microsoft.com/fwlink/?LinkId=529714
[kit de herramientas de Azure para Eclipse]: ../azure-toolkit-for-eclipse.md
[Instalación del kit de herramientas de Azure para Eclipse]: ../azure-toolkit-for-eclipse-installation.md
[Creación de una aplicación web Hello World para Azure en Eclipse]: ./app-service-web-eclipse-create-hello-world-web-app.md
[proyecto web dinámico de ejemplo]: http://go.microsoft.com/fwlink/?LinkId=817337

[Centro para desarrolladores de Java de Azure]: https://azure.microsoft.com/develop/java/
[Introducción a Aplicaciones web]: ./app-service-web-overview.md

<!-- IMG List -->

[01]: ./media/app-service-web-debug-java-web-app-in-eclipse/01-debug-java-web-app-in-eclipse.png
[02]: ./media/app-service-web-debug-java-web-app-in-eclipse/02-configure-eclipse-remote-debug.png
[03]: ./media/app-service-web-debug-java-web-app-in-eclipse/03-debug-as.png
[04]: ./media/app-service-web-debug-java-web-app-in-eclipse/04-debug-configurations.png
[05]: ./media/app-service-web-debug-java-web-app-in-eclipse/05-ready-for-remote-debugging.png
[06]: ./media/app-service-web-debug-java-web-app-in-eclipse/06-windows-command-prompt-connection-successful-to-remote.png



<!--HONumber=Jan17_HO1-->


