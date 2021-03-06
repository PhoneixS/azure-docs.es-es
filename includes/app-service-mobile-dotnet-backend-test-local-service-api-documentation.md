
1. En el Explorador de soluciones de Visual Studio, haga clic con el botón derecho en el proyecto de servicio y haga clic en **Iniciar nueva instancia**, que está en el menú contextual **Depurar**.
   
    Visual Studio abre la página web predeterminada del servicio. De forma predeterminada, Visual Studio hospeda el back-end de aplicación móvil de manera local en IIS Express.
2. Haga clic con el botón derecho en el icono de la bandeja de IIS Express en la barra de tareas de Windows y compruebe que el back-end de aplicación móvil se haya iniciado.
   
     ![comprobar el servicio móvil en la barra de tareas](./media/mobile-services-dotnet-backend-test-local-service-api-documentation/iis-express-tray.png)
3. En la página de inicio de su back-end .NET, haga clic en **probarlo**.
   
    Se muestra la página de documentación de la API, que puede usar para probar la aplicación móvil.
   
   > [!NOTE]
   > No se requiere autenticación para obtener acceso a esta página cuando se ejecuta de forma local. Al ejecutarse en Azure, debe suministrar la clave de la aplicación como contraseña (sin nombre de usuario) para obtener acceso a la página.
   > 
   > 
4. Haga clic en el vínculo **GET tables/TodoItem**.
   
    ![](./media/mobile-services-dotnet-backend-test-local-service-api-documentation/service-api-documentation-page.png)
   
    Esto muestra la página de respuesta GET de la API.
5. Haga clic en **probarlo** y luego haga clic en **enviar**.
   
    ![](./media/mobile-services-dotnet-backend-test-local-service-api-documentation/service-try-this-out-get-todoitems.png)
   
    Esta acción envía una solicitud GET al back-end de aplicación móvil local para devolver todas las filas de la tabla TodoItem. Como la tabla la arranca el inicializador, se devuelven dos objetos TodoItem en el cuerpo del mensaje de respuesta. Para obtener más información sobre los inicializadores, vea [Modificación del modelo de datos de un servicio móvil back-end .NET](../articles/mobile-services/mobile-services-dotnet-backend-how-to-use-code-first-migrations.md).
   
    ![](./media/mobile-services-dotnet-backend-test-local-service-api-documentation/service-try-this-out-get-response.png)

<!---HONumber=Oct15_HO3-->