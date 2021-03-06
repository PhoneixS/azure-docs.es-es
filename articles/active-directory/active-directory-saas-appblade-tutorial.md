---
title: "Tutorial: Integración de Azure Active Directory con AppBlade | Microsoft Docs"
description: "Aprenda a configurar el inicio de sesión único entre Azure Active Directory y AppBlade."
services: active-directory
documentationcenter: 
author: jeevansd
manager: femila
editor: 
ms.assetid: 3360d7aa-6518-4f99-88bd-b7f7258183e8
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/30/2016
ms.author: jeedes
translationtype: Human Translation
ms.sourcegitcommit: 82e5a947d48f8a289deb2f6e85bbb47990a9fcd7
ms.openlocfilehash: a378ca7be4c5a7df066c5450f9205c02c2acda0f


---
# <a name="tutorial-azure-active-directory-integration-with-appblade"></a>Tutorial: Integración de Azure Active Directory con AppBlade
El objetivo de este tutorial es mostrar cómo integrar AppBlade con Azure Active Directory (Azure AD).  
La integración de AppBlade con Azure AD proporciona las siguientes ventajas:

* Puede controlar en Azure AD quién tiene acceso a AppBlade.
* Puede permitir que los usuarios inicien sesión automáticamente en AppBlade (inicio de sesión único) con sus cuentas de Azure AD.
* Puede administrar sus cuentas en una ubicación central: el Portal de Azure clásico.

Si desea obtener más información sobre la integración de aplicaciones SaaS con Azure AD, vea [Qué es el acceso a las aplicaciones y el inicio de sesión único en Azure Active Directory](active-directory-appssoaccess-whatis.md).

## <a name="prerequisites"></a>Requisitos previos
Para configurar la integración de Azure AD con AppBlade, necesita los siguientes elementos:

* Una suscripción de Azure AD
* Una suscripción habilitada para inicio de sesión único en AppBlade

> [!NOTE]
> Para probar los pasos de este tutorial, no se recomienda el uso de un entorno de producción.
> 
> 

Para probar los pasos de este tutorial, debe seguir estas recomendaciones:

* No debe usar el entorno de producción, a menos que sea necesario.
* Si no dispone de un entorno de prueba de Azure AD, puede obtener una versión de prueba de un mes [aquí](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Descripción del escenario
El objetivo de este tutorial es permitirle probar el inicio de sesión único de Azure AD en un entorno de prueba.  
La situación descrita en este tutorial consta de dos bloques de creación principales:

1. Adición de AppBlade desde la galería
2. Configuración y comprobación del inicio de sesión único de Azure AD

## <a name="adding-appblade-from-the-gallery"></a>Adición de AppBlade desde la galería
Para configurar la integración de AppBlade en Azure AD, deberá agregar AppBlade desde la galería a la lista de aplicaciones SaaS administradas.

**Para agregar AppBlade desde la galería, realice los pasos siguientes:**

1. En el **Portal de Azure clásico**, en el panel de navegación izquierdo, haga clic en **Active Directory**. 
   
    ![Active Directory][1]
2. En la lista **Directory** , seleccione el directorio cuya integración desee habilitar.
3. Para abrir la vista de aplicaciones, haga clic en **Applications** , en el menú superior de la vista de directorios.
   
    ![Applications][2]
4. Haga clic en **Agregar** en la parte inferior de la página.
   
    ![Aplicaciones][3]
5. En el cuadro de diálogo **¿Qué desea hacer?**, haga clic en **Agregar una aplicación de la galería**.
   
    ![Aplicaciones][4]
6. En el cuadro de búsqueda, escriba **AppBlade**.

    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/tutorial_appblade_01.png)

1. En el panel de resultados, seleccione **AppBlade** y después haga clic en **Completar** para agregar la aplicación.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/tutorial_appblade_02.png)

## <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuración y comprobación del inicio de sesión único de Azure AD
El objetivo de esta sección es mostrar cómo configurar y probar el inicio de sesión único de Azure AD con AppBlade con una usuaria de prueba llamada "Britta Simon".

Para que el inicio de sesión único funcione, Azure AD debe saber cuál es el usuario homólogo de AppBlade para un usuario de Azure AD. Es decir, es necesario establecer una relación de vínculo entre un usuario de Azure AD y el usuario relacionado de AppBlade.  
Esta relación de vínculo se establece asignando el valor del **nombre de usuario** en Azure AD como valor de **Username** en AppBlade.

Para configurar y probar el inicio de sesión único de Azure AD con AppBlade, es preciso completar los siguientes bloques de creación:

1. **[Configuración del inicio de sesión único de Azure AD](#configuring-azure-ad-single-single-sign-on)** : para permitir a los usuarios usar esta característica.
2. **[Creación de un usuario de prueba de Azure AD](#creating-an-azure-ad-test-user)** : para probar el inicio de sesión único de Azure AD con Britta Simon.
3. **[Creación de un usuario de prueba de AppBlade](#creating-a-appblade-test-user)** : para tener un homólogo de Britta Simon en AppBlade que esté vinculado a la representación de ella en Azure AD.
4. **[Asignación del usuario de prueba de Azure AD](#assigning-the-azure-ad-test-user)** : para permitir que Britta Simon use el inicio de sesión único de Azure AD.
5. **[Prueba del inicio de sesión único](#testing-single-sign-on)** : para comprobar si funciona la configuración.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuración del inicio de sesión único de Azure AD
El objetivo de esta sección es habilitar el inicio de sesión único de Azure AD en el Portal de Azure clásico y configurar el inicio de sesión único en la aplicación AppBlade.

**Para configurar el inicio de sesión único de Azure AD con AppBlade, realice los pasos siguientes:**

1. En el Portal de Azure clásico, en la página de integración de aplicaciones de **AppBlade**, haga clic en **Configurar inicio de sesión único** para abrir el cuadro de diálogo **Configurar inicio de sesión único**.
   
    ![Configurar inicio de sesión único][6] 
2. En la página **How would you like users to sign on to AppBlade** (¿Cómo desea que los usuarios inicien sesión en AppBlade?), seleccione **Inicio de sesión único de Azure AD** y después haga clic en **Siguiente**.
   
    ![Configurar inicio de sesión único](./media/active-directory-saas-appblade-tutorial/tutorial_appblade_03.png) >
3. En la página de diálogo **Configurar las opciones de la aplicación** , realice los pasos siguientes:
   
    ![Configurar inicio de sesión único](./media/active-directory-saas-appblade-tutorial/tutorial_appblade_04.png) 

    a. En el cuadro de texto URL de inicio de sesión, escriba la dirección URL que usan los usuarios para iniciar sesión en su aplicación AppBlade con el siguiente patrón: **“https://companyname.appblade.com/saml/tenantid”**.

    b. Haga clic en **Next**.


1. En la página **Configurar inicio de sesión único en AppBlade** , realice los pasos siguientes:
   
    ![Configurar inicio de sesión único](./media/active-directory-saas-appblade-tutorial/tutorial_appblade_05.png) 
   
    a. Haga clic en **Descargar metadatos**y luego guarde el archivo en el equipo.
   
    b. Haga clic en **Next**.
2. Para que se configure el SSO para la aplicación, póngase en contacto con su equipo de soporte técnico de AppBlade a través de **support@appblade.com** y adjunte el archivo de metadatos descargado a su correo electrónico. Además, pídales que configuren la **URL de usuario de SSO** como **https://appblade.com/saml**. Esta configuración es necesaria para que el inicio de sesión único funcione.
3. En el Portal de Azure clásico, seleccione la confirmación de la configuración de inicio de sesión único y haga clic en **Siguiente**.
   
    ![Inicio de sesión único de Azure AD ][10]
4. En la página **Confirmación del inicio de sesión único**, haga clic en **Completar**.  
   
    ![Inicio de sesión único de Azure AD ][11]

### <a name="creating-an-azure-ad-test-user"></a>Creación de un usuario de prueba de Azure AD
El objetivo de esta sección es crear un usuario de prueba en el Portal de Azure clásico llamado Britta Simon.  

![Creación de un usuario de Azure AD][20]

**Siga estos pasos para crear un usuario de prueba en Azure AD:**

1. En el panel de navegación izquierdo del **Portal de Azure clásico**, haga clic en **Active Directory**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_09.png) 
2. En la lista **Directory** , seleccione el directorio cuya integración desee habilitar.
3. Para mostrar la lista de usuarios, en el menú de la parte superior, haga clic en **Usuarios**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_03.png) 
4. Para abrir el cuadro de diálogo **Agregar usuario**, en la barra de herramientas de la parte inferior, haga clic en **Agregar usuario**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_04.png) 
5. En la página de diálogo **Proporcione información sobre este usuario** , realice los pasos siguientes:
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_05.png) 
   
    a. En Tipo de usuario, seleccione Nuevo usuario de la organización.
   
    b. En el cuadro de texto **Nombre de usuario**, escriba**BrittaSimon**.
   
    c. Haga clic en **Siguiente**.
6. En la página de diálogo **Perfil de usuario** , realice los pasos siguientes:
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_06.png) 
   
    a. En el cuadro de texto **Nombre**, escriba **Britta**.  
   
    b. En el cuadro de texto **Apellidos**, escriba **Simon**.
   
    c. En el cuadro de texto **Nombre para mostrar**, escriba **Britta Simon**.
    
    d. En la lista **Rol**, seleccione **Usuario**.
   
    e. Haga clic en **Siguiente**.

7. En el cuadro de diálogo **Obtener contraseña temporal**, haga clic en **Crear**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_07.png) 
8. En la página de diálogo **Obtener contraseña temporal** , realice los pasos siguientes:
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-appblade-tutorial/create_aaduser_08.png) 
   
    a. Anote el valor del campo **Nueva contraseña**.
   
    b. Haga clic en **Complete**.   

### <a name="creating-a-appblade-test-user"></a>Creación de un usuario de prueba de AppBlade
El objetivo de esta sección es crear un usuario llamado Britta Simon en AppBlade. AppBlade admite el aprovisionamiento Just-In-Time, que está habilitado de forma predeterminada. **Asegúrese de que el nombre de dominio está configurado con AppBlade para el aprovisionamiento de usuarios. Después de eso solo el aprovisionamiento de usuarios Just-In-Time funcionará.**

Si el usuario tiene una dirección de correo electrónico que termina con el dominio configurado por AppBlade para la cuenta, dicho usuario se unirá automáticamente a la cuenta como un miembro con el nivel de permiso que especifique, que puede ser "Básico" (un usuario básico que solamente puede instalar aplicaciones), "Miembro del equipo" (un usuario que puede cargar nuevas versiones de aplicaciones y administrar proyectos) o "Administrador" (privilegios completos de administrador para la cuenta). Normalmente se elegiría Básico y después se promocionaría a los usuarios manualmente a través de un inicio de sesión del administrador (AppBlade debe configurar un inicio de sesión del administrador basado en correo electrónico por adelantado o promocionar a un usuario en nombre del cliente después de iniciar sesión).

No hay ningún elemento de acción para usted en esta sección. Durante un intento de acceder a AppBlade se creará un nuevo usuario, en caso de que no exista. [Configuración del inicio de sesión único de Azure AD](#configuring-azure-ad-single-single-sign-on).

> [!NOTE]
> Si necesita crear manualmente un usuario, es preciso que se ponga contacto con el equipo de soporte técnico de AppBlade.
> 
> 

### <a name="assigning-the-azure-ad-test-user"></a>Asignación del usuario de prueba de Azure AD
El objetivo de esta sección es permitir que Britta Simon use el inicio de sesión único de Azure concediéndole acceso a AppBlade.

![Asignar usuario][200] 

**Para asignar a Britta Simon a AppBlade, realice los pasos siguientes:**

1. En el Portal de Azure clásico, para abrir la vista de aplicaciones, en la vista del directorio, haga clic en **Aplicaciones** en el menú superior.
   
    ![Asignar usuario][201] 
2. En la lista de aplicaciones, seleccione **AppBlade**.
   
    ![Configurar inicio de sesión único](./media/active-directory-saas-appblade-tutorial/tutorial_appblade_50.png) 
3. En el menú de la parte superior, haga clic en **Usuarios**.
   
    ![Asignar usuario][203] 
4. En la lista Usuarios, seleccione **Britta Simon**.
5. En la barra de herramientas de la parte inferior, haga clic en **Asignar**.
   
    ![Asignar usuario][205]

### <a name="testing-single-sign-on"></a>Prueba del inicio de sesión único 
El objetivo de esta sección es probar la configuración del inicio de sesión único de Azure AD mediante el panel de acceso.  
Al hacer clic en el icono de AppBlade en el Panel de acceso, debería iniciar sesión automáticamente en su aplicación AppBlade.

## <a name="additional-resources"></a>Recursos adicionales
* [Lista de tutoriales sobre cómo integrar aplicaciones SaaS con Azure Active Directory](active-directory-saas-tutorial-list.md)
* [¿Qué es el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory?](active-directory-appssoaccess-whatis.md)

<!--Image references-->

[1]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_04.png

[6]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_05.png
[10]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_06.png
[11]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_07.png
[20]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_201.png
[203]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_203.png
[204]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_204.png
[205]: ./media/active-directory-saas-appblade-tutorial/tutorial_general_205.png



<!--HONumber=Dec16_HO4-->


