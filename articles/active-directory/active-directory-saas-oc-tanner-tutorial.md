---
title: "Tutorial: Integración de Azure Active Directory con O. C. Tanner - AppreciateHub | Microsoft Docs"
description: "Aprenda a configurar el inicio de sesión único entre Azure Active Directory y O. C. Tanner - AppreciateHub."
services: active-directory
documentationcenter: 
author: jeevansd
manager: femila
editor: 
ms.assetid: dee8fbca-0b60-4a21-8917-1fb6919de5a0
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/21/2016
ms.author: jeedes
translationtype: Human Translation
ms.sourcegitcommit: a2129813f7214b2b32b2d7d6c9d666e96b60a926
ms.openlocfilehash: 10cf00155767b0cc8a318993e3ce95e55079312f


---
# <a name="tutorial-azure-active-directory-integration-with-o-c-tanner---appreciatehub"></a>Tutorial: Integración de Azure Active Directory con O. C. C. Tanner - AppreciateHub
El objetivo de este tutorial es mostrar la integración de O.C. Tanner - AppreciateHub con Azure Active Directory (Azure AD).  
Integración de O.C. Tanner - AppreciateHub con Azure AD proporciona las siguientes ventajas: 

* Puede controlar en Azure AD quién tiene acceso a O.C. C. Tanner - AppreciateHub 
* Puede permitir a los usuarios iniciar sesión automáticamente en O.C. Tanner - AppreciateHub (inicio de sesión único) con sus cuentas de Azure AD.
* Puede administrar sus cuentas en una ubicación central: el Portal de Azure clásico.

Si desea obtener más información sobre la integración de aplicaciones SaaS con Azure AD, vea [Qué es el acceso a las aplicaciones y el inicio de sesión único en Azure Active Directory](active-directory-appssoaccess-whatis.md).

## <a name="prerequisites"></a>Requisitos previos
Para configurar la integración de Azure AD con O.C. Tanner - AppreciateHub, necesita los siguientes elementos:

* Una suscripción de Azure AD
* Una suscripción habilitada para el inicio de sesión único a O.C. Tanner - AppreciateHub

> [!NOTE]
> Para probar los pasos de este tutorial, no se recomienda el uso de un entorno de producción.
> 
> 

Para probar los pasos de este tutorial, debe seguir estas recomendaciones:

* No debe usar el entorno de producción, a menos que sea necesario.
* Si no dispone de un entorno de prueba de Azure AD, puede obtener una versión de prueba de un mes [aquí](https://azure.microsoft.com/pricing/free-trial/). 

## <a name="scenario-description"></a>Descripción del escenario
El objetivo de este tutorial es permitirle probar el inicio de sesión único de Azure AD en un entorno de prueba.  
El escenario descrito en este tutorial consta de tres bloques de creación principales:

1. Agregar O.C. Tanner - AppreciateHub desde la galería 
2. Configuración y comprobación del inicio de sesión único de Azure AD

## <a name="adding-oc-tanner---appreciatehub-from-the-gallery"></a>Agregar O.C. Tanner - AppreciateHub desde la galería
Para configurar la integración de O.C. Tanner - AppreciateHub en Azure AD, debe agregar O.C. Tanner - AppreciateHub desde la galería a la lista de aplicaciones SaaS administradas.

**Para agregar O.C. Tanner - AppreciateHub desde la galería, realice los pasos siguientes:**

1. En el panel de navegación izquierdo del **Portal de Azure clásico**, haga clic en **Active Directory**. 
   
    ![Active Directory][1] 
2. En la lista **Directory** , seleccione el directorio cuya integración desee habilitar.
3. Para abrir la vista de aplicaciones, haga clic en **Applications** , en el menú superior de la vista de directorios.
   
    ![Applications][2] 
4. Haga clic en **Agregar** en la parte inferior de la página.
   
    ![Aplicaciones][3] 
5. En el cuadro de diálogo **¿Qué desea hacer?**, haga clic en **Agregar una aplicación de la galería**.
   
    ![Aplicaciones][4] 
6. En el cuadro de búsqueda, escriba **O.C. Tanner - AppreciateHub**.
   
    ![Aplicaciones][5] 
7. En el panel de resultados, seleccione **O.C. Tanner - AppreciateHub** y, luego, haga clic en **Completar** para agregar la aplicación.
   
    ![Aplicaciones][25] 

## <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuración y comprobación del inicio de sesión único de Azure AD
El objetivo de esta sección es mostrar cómo configurar y probar el inicio de sesión único de Azure AD con O.C. Tanner - AppreciateHub en función de un usuario de prueba llamado "Britta Simon".

Para que el inicio de sesión único funcione, Azure AD debe saber cuál es el usuario homólogo de O.C. Tanner - AppreciateHub para un usuario de Azure AD. Es decir, es necesario establecer una relación de vínculo entre un usuario de Azure AD y el usuario relacionado de  Tanner - AppreciateHub.  
Esta relación de vínculo se establece mediante la asignación del valor del **nombre de usuario** en Azure AD como el valor del **nombre de usuario** en O. C. Tanner - AppreciateHub.

Para configurar y probar el inicio de sesión único en Azure AD con O.C. Tanner - AppreciateHub, debe completar los siguientes bloques de creación:

1. **[Configuración del inicio de sesión único de Azure AD](#configuring-azure-ad-single-single-sign-on)** : para permitir a los usuarios usar esta característica.
2. **[Creación de un usuario de prueba de Azure AD](#creating-an-azure-ad-test-user)** : para probar el inicio de sesión único de Azure AD con Britta Simon.
3. **[Creación de un usuario de prueba de O.C. Tanner - AppreciateHub](#creating-a-halogen-software-test-user)**: para tener un homólogo de Britta Simon en O.C. Tanner - AppreciateHub que esté vinculado a la representación de ella en Azure AD.
4. **[Asignación del usuario de prueba de Azure AD](#assigning-the-azure-ad-test-user)** : para permitir que Britta Simon use el inicio de sesión único de Azure AD.
5. **[Prueba del inicio de sesión único](#testing-single-sign-on)** : para comprobar si funciona la configuración.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuración del inicio de sesión único de Azure AD
El objetivo de esta sección es habilitar el inicio de sesión único de Azure AD en el Portal de Azure clásico y configurar el inicio de sesión único en la aplicación O.C. Tanner - AppreciateHub.

**Para configurar y probar el inicio de sesión único en Azure AD con O.C. Tanner - AppreciateHub, realice los pasos siguientes:**

1. En el Portal de Azure clásico, en la página de integración de la aplicación **O.C. Tanner - AppreciateHub**, haga clic en **Configurar inicio de sesión único** para abrir el cuadro de diálogo **Configurar inicio de sesión único**.
   
    ![Configurar inicio de sesión único][6]
2. En la página **¿Cómo desea que los usuarios inicien sesión en O.C. Tanner - AppreciateHub?**, seleccione **Inicio de sesión único de Azure AD** y luego haga clic en **Siguiente**.
   
    ![Inicio de sesión único de Azure AD ][7]
3. En la página de diálogo **Configurar las opciones de la aplicación** , realice los pasos siguientes:
   
    ![Configurar las opciones de la aplicación][8]
   
     a. Abra el archivo de metadatos mediante el siguiente vínculo: [https://fed.appreciatehub.com/fed/sp/metadata](https://fed.appreciatehub.com/fed/sp/metadata).
   
     b. Busque el nodo **md:AssertionConsumerService** . 
   
     c. Copie el valor del atributo **Location** . 
   
     ![Configurar las opciones de la aplicación][12]
   
     d. En el cuadro de texto **URL de inicio de sesión** , pegue el valor que obtuvo en el paso anterior.
   
    > [!NOTE]
    > Si experimenta problemas al obtener la URL de respuesta del archivo de metadatos, póngase en contacto con el equipo de soporte de O.C. Tanner - AppreciateHub en [sso@octanner.com](mailto:sso@octanner.com).
    > 
    > 
   
    e. Haga clic en **Siguiente**.

4. En la página **Configurar inicio de sesión único en O.C. Tanner - AppreciateHub**, haga clic en **Descargar metadatos** y, luego, guarde el archivo de metadatos localmente en el equipo.
   
    ![Qué es Azure AD Connect][9]
5. Póngase en contacto con el equipo de soporte de O.C. Tanner - AppreciateHub mediante xyz, proporcióneles el archivo de metadatos y hágales saber que deben habilitar SSO para usted.
6. En el Portal de Azure clásico, seleccione la confirmación de la configuración de inicio de sesión único y haga clic en **Siguiente**. 
   
    ![Qué es Azure AD Connect][10]
7. En la página **Confirmación del inicio de sesión único**, haga clic en **Completar**.  
   
    ![Qué es Azure AD Connect][11]

### <a name="creating-an-azure-ad-test-user"></a>Creación de un usuario de prueba de Azure AD
El objetivo de esta sección es crear un usuario de prueba en el Portal de Azure clásico llamado Britta Simon.  

![Creación de un usuario de Azure AD][20]

**Siga estos pasos para crear un usuario de prueba en Azure AD:**

1. En el panel de navegación izquierdo del **Portal de Azure clásico**, haga clic en **Active Directory**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_02.png) 
2. En la lista **Directory** , seleccione el directorio cuya integración desee habilitar.
3. Para mostrar la lista de usuarios, en el menú de la parte superior, haga clic en **Usuarios**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_03.png) 
4. Para abrir el cuadro de diálogo **Agregar usuario**, en la barra de herramientas de la parte inferior, haga clic en **Agregar usuario**. 
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_04.png) 
5. En la página de diálogo **Proporcione información sobre este usuario** , realice los pasos siguientes: 
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_05.png) 
   
    a. En Tipo de usuario, seleccione Nuevo usuario de la organización.
   
    b. En el cuadro de texto **Nombre de usuario**, escriba**BrittaSimon**.
   
    c. Haga clic en **Siguiente**.
6. En la página de diálogo **Perfil de usuario** , realice los pasos siguientes: 
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_06.png)
   
    a. En el cuadro de texto **Nombre**, escriba **Britta**.  
   
    b. En el cuadro de texto **Apellidos**, escriba **Simon**.
   
    c. En el cuadro de texto **Nombre para mostrar**, escriba **Britta Simon**.
   
    d. En la lista **Rol**, seleccione **Usuario**.
    e. Haga clic en **Siguiente**.

7. En el cuadro de diálogo **Obtener contraseña temporal**, haga clic en **Crear**.
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_07.png) 
8. En la página de diálogo **Obtener contraseña temporal** , realice los pasos siguientes:
   
    ![Creación de un usuario de prueba de Azure AD](./media/active-directory-saas-oc-tanner-tutorial/create_aaduser_08.png) 
   
    a. Anote el valor del campo **Nueva contraseña**.
   
    b. Haga clic en **Completo**.   

### <a name="creating-a-oc-tanner---appreciatehub-test-user"></a>Creación de un usuario de prueba de O.C. C. Tanner - AppreciateHub
El objetivo de esta sección es crear un usuario de prueba llamado Britta Simon en O.C. Tanner - AppreciateHub.

**Para crear un usuario llamado Simon Britta en O.C. Tanner - AppreciateHub, realice los pasos siguientes:**

Pida al equipo de soporte de O.C. Tanner que cree un usuario que tenga como atributo nameID el mismo valor que el nombre de usuario de Britta Simon en Azure AD.

### <a name="assigning-the-azure-ad-test-user"></a>Asignación del usuario de prueba de Azure AD
El objetivo de esta sección es permitir que Britta Simon use el inicio de sesión único de Azure concediéndole acceso a O.C. Tanner - AppreciateHub.

![Asignar usuario][200]

**Para asignar a Simon Britta a O.C. Tanner - AppreciateHub, realice los pasos siguientes:**

1. En el Portal de Azure clásico, para abrir la vista de aplicaciones, en la vista del directorio, haga clic en **Aplicaciones** en el menú superior.
   
    ![Asignar usuario][201]
2. En la lista de aplicaciones, seleccione **O.C. Tanner - AppreciateHub**.
   
    ![Asignar usuario][202]
3. En el menú de la parte superior, haga clic en **Usuarios**.
   
    ![Asignar usuario][203]
4. En la lista Usuarios, seleccione **Britta Simon**.
5. En la barra de herramientas de la parte inferior, haga clic en **Asignar**.
   
    ![Asignar usuario][205]

### <a name="testing-single-sign-on"></a>Prueba del inicio de sesión único 
El objetivo de esta sección es probar la configuración del inicio de sesión único de Azure AD mediante el panel de acceso.  
Cuando hace clic en el icono de O.C. Tanner - AppreciateHub en el panel de acceso, debe iniciar sesión automáticamente en la aplicación O.C. Tanner - AppreciateHub.

## <a name="additional-resources"></a>Recursos adicionales
* [Lista de tutoriales sobre cómo integrar aplicaciones SaaS con Azure Active Directory](active-directory-saas-tutorial-list.md)
* [¿Qué es el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory?](active-directory-appssoaccess-whatis.md)

<!--Image references-->
[1]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_04.png
[5]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_01.png
[25]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_25.png


[6]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_05.png
[7]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_02.png
[8]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_03.png
[9]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_04.png
[10]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_05.png
[11]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_06.png
[12]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_08.png
[20]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_octanner_07.png
[203]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_203.png
[204]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_204.png
[205]: ./media/active-directory-saas-oc-tanner-tutorial/tutorial_general_205.png









<!--HONumber=Nov16_HO4-->


