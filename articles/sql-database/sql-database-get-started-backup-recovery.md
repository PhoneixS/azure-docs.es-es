---
title: "Introducción a la copia de seguridad y la restauración de bases de datos SQL de Azure para la protección y la recuperación de los datos | Microsoft Docs"
description: "En este tutorial se muestra cómo restaurar copias de seguridad automatizadas a un momento en el tiempo y cómo almacenar copias de seguridad automatizadas en el almacén de Azure Recovery Services y restaurarlas de él."
keywords: tutorial de base de datos sql
services: sql-database
documentationcenter: 
author: CarlRabeler
manager: jhubbard
editor: 
ms.assetid: aeb8c4c3-6ae2-45f7-b2c3-fa13e3752eed
ms.service: sql-database
ms.custom: business continuity
ms.workload: data-management
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: hero-article
ms.date: 12/08/2016
ms.author: carlrab
translationtype: Human Translation
ms.sourcegitcommit: 7f26cd0f6c5f9c7a2fe692bfcdc6ef60d1b2200f
ms.openlocfilehash: d4ea089ed4b5d29c261b25e95f4d304611f9a857


---
<!------------------
This topic is annotated with TEMPLATE guidelines for TUTORIAL TOPICS.


Metadata guidelines

title
    60 characters or less. Tells users clearly what they will do (deploy an ASP.NET web app to App Service). Not the same as H1. It's 60 characters or fewer including all characters between the quotes and the Microsoft Docs site identifier.

description
    115-145 characters. Duplicate of the first sentence in the introduction. This is the abstract of the article that displays under the title when searching in Bing or Google. 

    Example: "This tutorial shows how to deploy an ASP.NET web application to a web app in Azure App Service by using Visual Studio 2015."
------------------>

<!----------------

TEMPLATE GUIDELINES for tutorial topics

The tutorial topic shows users how to solve a problem using a product or service. It includes the prerequisites and steps users need to be successful.  

It is a "solve a problem" topic, not a "learn concepts" topic.

DO include this:
    • What users will do
    • What they will create or accomplish by the end of the tutorial
    • Time estimate
    • Optional but useful: Include a diagram or video. Diagrams help users see the big picture of what they are doing. A video of the steps can be used by customers as an alternative to following the steps in the topic.
    • Prerequisites: Technical expertise and software requirements
    • End-to-end steps. At the end, include next steps to deeper or related tutorials so users can learn more about the service

DON'T include this:
    • Conceptual info about the service. This info is in overview topics that you can link to in the prerequisites section if necessary

------------------->

<!------------------
GUIDELINES for the H1 
    
    The H1 should answer the question "What will I do in this topic?" Write the H1 heading in conversational language and use search keywords as much as possible. Since this is a "solve a problem" topic, make sure the title indicates that. Use a strong, specific verb like "Deploy."  
        
    Heading must use an industry standard term. If your feature is a proprietary name like "elastic pools", use a synonym. For example: "Learn about elastic pools for multi-tenant databases." In this case multi-tenant database is the industry-standard term that will be an anchor for finding the topic.

-------------------->

# <a name="get-started-with-backup-and-restore-for-data-protection-and-recovery"></a>Introducción a la copia de seguridad y la restauración para la protección y la recuperación de los datos

<!------------------
    GUIDELINES for introduction
    
    The introduction is 1-2 sentences.  It is optimized for search and sets proper expectations about what to expect in the article. It should contain the top keywords that you are using throughout the article.The introduction should be brief and to the point of what users will do and what they will accomplish. 

    In this example:
     

Sentence #1 Explains what the user will do. This is also the metadata description. 
    This tutorial shows how to deploy an ASP.NET web application to a web app in Azure App Service by using Visual Studio 2015. 

Sentence #2 Explains what users will learn and the benefit.  
    When you’re finished, you’ll have a simple web application up and running in the cloud.

-------------------->


En este tutorial de introducción, aprenderá a usar Azure Portal para:

- Ver copias de seguridad existentes de una base de datos
- Restaurar una base de datos a un momento anterior en el tiempo
- Configurar la retención a largo plazo de un archivo de copia de seguridad de base de datos en el almacén de Azure Recovery Services
- Restaurar una base de datos del almacén de Azure Recovery Services

**Estimación del tiempo**: este tutorial se realiza en 30 minutos (suponiendo que ya se hayan cumplido los requisitos previos).


## <a name="prerequisites"></a>Requisitos previos

* Necesitará una cuenta de Azure. Puede [abrir una cuenta gratuita de Azure](/pricing/free-trial/?WT.mc_id=A261C142F) o [activar las ventajas que disfrutan los suscriptores de Visual Studio](/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). 

* Debe poder conectarse a Azure Portal mediante una cuenta que sea miembro del rol de colaborador o propietario de la suscripción. Para más información sobre el acceso basado en roles (RBAC), consulte [Introducción a la administración de acceso en Azure Portal](../active-directory/role-based-access-control-what-is.md).

* Ha finalizado la [introducción a los servidores, las bases de datos y las reglas de firewalls de Azure SQL Database mediante Azure Portal y SQL Server Management Studio](sql-database-get-started.md) o la [versión de PowerShell](sql-database-get-started-powershell.md) equivalente de este tutorial. Si no es así, realice el tutorial que es requisito previo o ejecute el script de PowerShell al final de la [versión de PowerShell](sql-database-get-started-powershell.md) de este tutorial antes de continuar.


> [!TIP]
> Puede realizar las mismas tareas del tutorial de introducción con [PowerShell](sql-database-get-started-backup-recovery-powershell.md).


## <a name="sign-in-by-using-your-existing-account"></a>Inicio de sesión con una cuenta existente
Con una [suscripción existente](https://account.windowsazure.com/Home/Index), siga estos pasos para conectarse al portal de Azure.

1. Abra el explorador que prefiera y conéctese al [Portal de Azure](https://portal.azure.com/).
2. Inicie sesión en el [Portal de Azure](https://portal.azure.com/).
3. En la página **Iniciar sesión** , proporcione las credenciales de la suscripción.
   
   ![Iniciar sesión](./media/sql-database-get-started/login.png)


<a name="create-logical-server-bk"></a>

## <a name="view-the-oldest-restore-point-from-the-service-generated-backups-of-a-database"></a>Visualización del punto de restauración más antiguo de las copias de seguridad generadas por el servicio de una base de datos

En esta sección del tutorial, verá información sobre el punto de restauración más antiguo de las [copias de seguridad automatizadas generadas por el servicio](sql-database-automated-backups.md) de su base de datos. 

1. Abra la hoja **SQL Database** de la base de datos **sqldbtutorialdb**.

    ![hoja nueva base de datos de ejemplo](./media/sql-database-get-started/new-sample-db-blade.png)

2. En la barra de herramientas, haga clic en **Restaurar**.

    ![barra de herramientas restaurar](./media/sql-database-get-started-backup-recovery/restore-toolbar.png)

3. En la hoja Restaurar, revise el punto de restauración más antiguo.

    ![punto de restauración más antiguo](./media/sql-database-get-started-backup-recovery/oldest-restore-point.png)

## <a name="restore-a-database-to-a-previous-point-in-time"></a>Restauración de una base de datos a un momento anterior en el tiempo

En esta sección del tutorial, restaurará la base de datos en una nueva base de datos a partir de un momento específico en el tiempo.

1. En la hoja **Restaurar** de la base de datos, revise el nombre predeterminado de la nueva base de datos en la que va a restaurar su base de datos a un momento anterior en el tiempo (el nombre es el nombre de la base de datos existente anexado una marca de tiempo). Este nombre se cambia para reflejar la hora que especifique en los siguientes pasos.

    ![nombre de base de datos restaurada](./media/sql-database-get-started-backup-recovery/restored-database-name.png)

2. Haga clic en el icono de **calendario** en el cuadro de entrada **Punto de restauración (UTC)**.

    ![punto de restauración](./media/sql-database-get-started-backup-recovery/restore-point.png)

2. En el calendario, seleccione una fecha dentro del período de retención.

    ![fecha de punto de restauración](./media/sql-database-get-started-backup-recovery/restore-point-date.png)

3. En el cuadro de entrada **Punto de restauración (UTC)**, especifique la hora en la fecha seleccionada a la que desea restaurar los datos de la base de datos de las copias de seguridad de base de datos automatizadas.

    ![hora de punto de restauración](./media/sql-database-get-started-backup-recovery/restore-point-time.png)

    >[!NOTE]
    >Observe que el nombre de la base de datos ha cambiado para reflejar la fecha y la hora seleccionadas. Observe también que no se puede cambiar el servidor en el que va a restaurar a un momento específico en el tiempo. Para restaurar en un servidor diferente, use [Georestauración](sql-database-disaster-recovery.md#recover-using-geo-restore). Por último, tenga en cuenta que la restauración se puede realizar en un [grupo elástico](sql-database-elastic-jobs-overview.md) o en otro plan de tarifa. 
    >

4. Haga clic en **Aceptar** para restaurar la base de datos a un momento anterior en el tiempo en la nueva base de datos.

5. En la barra de herramientas, haga clic en el icono de notificación para ver el estado del trabajo de restauración.

    ![progreso del trabajo de restauración](./media/sql-database-get-started-backup-recovery/restore-job-progress.png)

6. Cuando finalice el trabajo de restauración, abra la hoja **Bases de datos SQL** para ver la base de datos recién restaurada.

    ![base de datos restaurada](./media/sql-database-get-started-backup-recovery/restored-database.png)

   > [!NOTE]
   > Desde aquí, puede conectarse a la base de datos restaurada mediante SQL Server Management Studio para realizar las tareas necesarias, como [extraer un bit de datos de la base de datos restaurada para copiarlo en la base de datos existente o para eliminar la base de datos existente y cambiar el nombre de la base de datos restaurada por el nombre de la base de datos existente](sql-database-recovery-using-backups.md#point-in-time-restore).
   >

## <a name="configure-long-term-retention-of-automated-backups-in-an-azure-recovery-services-vault"></a>Configuración de la retención a largo plazo de copias de seguridad automatizadas en un almacén de Azure Recovery Services 

En esta sección del tutorial, [configurará un almacén de Azure Recovery Services para conservar copias de seguridad automatizadas](sql-database-long-term-retention.md) durante un período más largo que el período de retención del nivel de servicio. 


> [!TIP]
> Para eliminar las copias de seguridad, consulte [Delete long-term retention backups](sql-database-long-term-retention-delete.md) (Eliminación de copias de seguridad de retención a largo plazo).


1. Abra la hoja **SQL Server** de su servidor, **sqldbtutorialserver**.

    ![hoja sql server](./media/sql-database-get-started/sql-server-blade.png)

2. Haga clic en **Long-term backup retention** (Retención de copia de seguridad a largo plazo).

   ![vínculo de retención de copia de seguridad a largo plazo](./media/sql-database-get-started-backup-recovery/long-term-backup-retention-link.png)

3. En la hoja **sqldbtutorial - Long-term backup retention** (sqldbtutorial: Retención de copia de seguridad a largo plazo), revise y acepte los términos de versión preliminar (a no ser que ya lo haya hecho, o esta característica ya no esté en versión preliminar).

   ![aceptar los términos de versión preliminar](./media/sql-database-get-started-backup-recovery/accept-the-preview-terms.png)

4. Para configurar la retención de copia de seguridad a largo plazo para la base de datos sqldbtutorialdb, seleccione esa base de datos en la cuadrícula y luego haga clic en **Configurar** en la barra de herramientas.

   ![seleccionar base de datos para retención de copia de seguridad a largo plazo](./media/sql-database-get-started-backup-recovery/select-database-for-long-term-backup-retention.png)

5. En la hoja **Configurar**, haga clic en **Configurar los valores obligatorios** en **Recovery service vault** (Almacén de servicios de recuperación).

   ![vínculo para configurar almacén](./media/sql-database-get-started-backup-recovery/configure-vault-link.png)

6. En la hoja **Recovery services vault** (Almacén de servicios de recuperación), seleccione un almacén existente, si lo hay. Si no se encuentra ningún almacén de servicios de recuperación para su suscripción, haga clic para salir del flujo y crear uno.

   ![vínculo para crear nuevo almacén](./media/sql-database-get-started-backup-recovery/create-new-vault-link.png)

7. En la hoja **Almacenes de Recovery Services**, haga clic en **Agregar**.

   ![vínculo para agregar nuevo almacén](./media/sql-database-get-started-backup-recovery/add-new-vault-link.png)
   
8. En la hoja **Almacén de Recovery Services**, proporcione un nombre válido para el almacén de Recovery Services.

   ![nuevo nombre de almacén](./media/sql-database-get-started-backup-recovery/new-vault-name.png)

9. Seleccione la suscripción y el grupo de recursos y luego seleccione la ubicación del almacén. Cuando termine, haga clic en **Crear**.

   ![crear nuevo almacén](./media/sql-database-get-started-backup-recovery/create-new-vault.png)

   > [!IMPORTANT]
   > El almacén debe estar ubicado en la misma región que el servidor lógico de Azure SQL y debe usar el mismo grupo de recursos que el servidor lógico.
   >

10. Después de crear el nuevo almacén, ejecute los pasos necesarios para volver a la hoja **Almacén de Recovery Services**.

11. En la hoja **Almacén de Recovery Services**, haga clic en el almacén y luego en **Seleccionar**.

   ![seleccionar almacén existente](./media/sql-database-get-started-backup-recovery/select-existing-vault.png)

12. En la hoja **Configurar**, proporcione un nombre válido para la nueva directiva de retención, modifique la directiva de retención predeterminada según sea apropiado y luego haga clic en **Aceptar**.

   ![definir directiva de retención](./media/sql-database-get-started-backup-recovery/define-retention-policy.png)

13. En la hoja **sqldbtutorial - Long-term backup retention** (sqldbtutorial: Retención de copia de seguridad a largo plazo), haga clic en **Guardar** y luego en **Aceptar** para aplicar la directiva de retención de copia de seguridad a largo plazo a todas las bases de datos seleccionadas.

   ![definir directiva de retención](./media/sql-database-get-started-backup-recovery/save-retention-policy.png)

14. Haga clic en **Guardar** para habilitar la retención de copia de seguridad a largo plazo mediante esta nueva directiva para el almacén de Azure Recovery Services que ha configurado.

   ![definir directiva de retención](./media/sql-database-get-started-backup-recovery/enable-long-term-retention.png)

15. Cuando haya habilitado la retención de copia de seguridad a largo plazo, abra la hoja **sqldbtutorialvault** (vaya a **Todos los recursos** y selecciónela en la lista de recursos de su suscripción).

   ![ver el almacén de servicios de recuperación](./media/sql-database-get-started-backup-recovery/view-recovery-services-vault.png)

   > [!IMPORTANT]
   > Una vez configurado, las copias de seguridad se mostrarán en el almacén en los próximos siete días. No continúe con este tutorial hasta que las copias de seguridad se muestren en el almacén.
   >

## <a name="view-backups-in-long-term-retention"></a>Visualización de copias de seguridad con retención a largo plazo

En esta sección del tutorial, verá información sobre las copias de seguridad de base de datos con [retención a largo plazo](sql-database-long-term-retention.md). 

1. Abra la hoja **sqldbtutorialvault** (vaya a **Todos los recursos** y selecciónela de la lista de recursos de su suscripción) para ver la cantidad de almacenamiento que usan las copias de seguridad de base de datos en el almacén.

   ![ver almacén de servicios de recuperación con copias de seguridad](./media/sql-database-get-started-backup-recovery/view-recovery-services-vault-with-data.png)

2. Abra la hoja **SQL Database** de la base de datos **sqldbtutorialdb**.

    ![hoja nueva base de datos de ejemplo](./media/sql-database-get-started/new-sample-db-blade.png)

3. En la barra de herramientas, haga clic en **Restaurar**.

    ![barra de herramientas restaurar](./media/sql-database-get-started-backup-recovery/restore-toolbar.png)

4. En la hoja Restaurar, haga clic en **A largo plazo**.

5. En Azure vault backups (Copias de seguridad de Azure Vault), haga clic en **Seleccionar una copia de seguridad** para ver las copias de seguridad de base de datos disponibles con retención a largo plazo.

    ![copias de seguridad en almacén](./media/sql-database-get-started-backup-recovery/view-backups-in-vault.png)

## <a name="restore-a-database-from-a-backup-in-long-term-backup-retention"></a>Restauración de una base de datos de una copia de seguridad con retención a largo plazo

En esta sección del tutorial, restaurará la base de datos en una nueva desde una copia de seguridad del almacén de Azure Recovery Services.

1. En la hoja **Azure vault backups** (Copias de seguridad de Azure Vault), haga clic en la copia de seguridad que quiere restaurar y luego haga clic en **Seleccionar**.

    ![seleccionar copia de seguridad en almacén](./media/sql-database-get-started-backup-recovery/select-backup-in-vault.png)

2. En el cuadro de texto **Nombre de la base de datos**, proporcione el nombre de la base de datos restaurada.

    ![nombre de nueva base de datos](./media/sql-database-get-started-backup-recovery/new-database-name.png)

3. Haga clic en **Aceptar** para restaurar la base de datos de la copia de seguridad del almacén en la nueva base de datos.

4. En la barra de herramientas, haga clic en el icono de notificación para ver el estado del trabajo de restauración.

    ![progreso de trabajo de restauración del almacén](./media/sql-database-get-started-backup-recovery/restore-job-progress-long-term.png)

5. Cuando finalice el trabajo de restauración, abra la hoja **Bases de datos SQL** para ver la base de datos recién restaurada.

    ![base de datos restaurada desde almacén](./media/sql-database-get-started-backup-recovery/restored-database-from-vault.png)

   > [!NOTE]
   > Desde aquí, puede conectarse a la base de datos restaurada mediante SQL Server Management Studio para realizar las tareas necesarias, como [extraer un bit de datos de la base de datos restaurada para copiarlo en la base de datos existente o para eliminar la base de datos existente y cambiar el nombre de la base de datos restaurada por el nombre de la base de datos existente](sql-database-recovery-using-backups.md#point-in-time-restore).
   >


<!--**Next steps**: *Reiterate what users have done, and give them interesting and useful next steps so they want to go on.*-->

## <a name="next-steps"></a>Pasos siguientes

- Para aprender sobre las copias de seguridad automáticas generadas por el servicio, consulte [copias de seguridad automáticas](sql-database-automated-backups.md)
- Para más información sobre la retención de copia de seguridad a largo plazo, consulte sobre la [retención de copia de seguridad a largo plazo](sql-database-long-term-retention.md).
- Para aprender sobre la restauración a partir de copias de seguridad, consulte sobre la [restauración desde una copia de seguridad](sql-database-recovery-using-backups.md).



<!--HONumber=Dec16_HO4-->


