---
title: "Especificación de una versión de Node.js"
description: "Aprenda a especificar la versión de Node.js que usan Sitios web Azure y Servicios en la nube"
services: 
documentationcenter: nodejs
author: rmcmurray
manager: erikre
editor: 
ms.assetid: d0e15278-2ab4-4ec8-8256-913839c6d5ef
ms.service: multiple
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 11/01/2016
ms.author: robmcm
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: c41ef7c2bf4c7d66e8596627585cd3014a9ac839


---
# <a name="specifying-a-nodejs-version-in-an-azure-application"></a>Especificación de una versión de Node.js en una aplicación Azure
Cuando hospeda una aplicación de Node.js, es posible que desee asegurarse de que su aplicación utiliza una versión específica de Node.js. Hay muchas maneras de hacer esto con las aplicaciones hospedadas en Azure.

## <a name="default-versions"></a>Versiones predeterminadas
Las versiones de Node.js que Azure proporciona se actualizan constantemente. A menos que se indique lo contrario, se usará la versión predeterminada que se especifica en la variable de entorno `WEBSITE_NODE_DEFAULT_VERSION` . Para reemplazar este valor predeterminado, realice los pasos descritos en las secciones siguientes de este artículo.

> [!NOTE]
> Si hospeda su aplicación en un servicio en la nube de Azure (rol web o de trabajo) y es primera vez que ha implementado la aplicación, Azure intentará utilizar la misma versión de Node.js que ha instalado en su entorno de desarrollo si coincide con una de las versiones predeterminadas disponibles en Azure.
> 
> 

## <a name="versioning-with-packagejson"></a>Control de versiones con package.json
Puede especificar la versión de Node.js que se va a utilizar si agrega lo siguiente a su archivo **package.json** :

    "engines":{"node":version}

Donde *version* es el número específico de la versión que se utilizará. Puede especificar condiciones más complejas para la versión, como:

    "engines":{"node": "0.6.22 || 0.8.x"}

Como 0.6.22 no es una de las versiones disponibles en el entorno de hospedaje, se utilizará en su lugar la versión superior de la serie 0.8 que se encuentra disponible, es decir, 0.8.4.

## <a name="versioning-websites-with-app-settings"></a>Control de versiones de sitios web con configuración de aplicaciones
Si hospeda la aplicación en un sitio web, puede establecer la variable de entorno **WEBSITE_NODE_DEFAULT_VERSION** en la versión deseada.

## <a name="versioning-cloud-services-with-powershell"></a>Control de versiones de Servicios en la nube con PowerShell
Si hospeda la aplicación en un servicio en la nube y la aplicación se implementa con Azure PowerShell, puede reemplazar la versión predeterminada de Node.js mediante el uso del cmdlet **Set-AzureServiceProjectRole** de PowerShell. Por ejemplo:

    Set-AzureServiceProjectRole WebRole1 Node 0.8.4

Tenga en cuenta que los parámetros de la instrucción anterior distinguen entre mayúsculas y minúsculas.  Puede comprobar la versión correcta de Node.js que se ha seleccionado comprobando la propiedad **engines** en el **package.json** de su rol.

También puede utilizar **Get-AzureServiceProjectRoleRuntime** para recuperar una lista de las versiones disponibles de Node.js para las aplicaciones hospedadas como Servicio en la nube.  Compruebe siempre que la versión de Node.js de la que depende su proyecto se encuentre en esta lista.

## <a name="using-a-custom-version-with-azure-websites"></a>Uso de una versión personalizada con Sitios web Azure
A pesar de que Azure proporciona varias versiones predeterminadas de Node.js, es posible que desee utilizar una versión que no se brinda de manera predeterminada. Si su aplicación está hospedada como un sitio web de Azure, puede hacer esto con el archivo **iisnode.yml** . Los siguientes pasos describen el proceso de usar una versión personalizada de Node.js con un sitio web Azure:

1. Cree un directorio nuevo y, a continuación, cree un archivo **server.js** dentro del directorio. El archivo **server.js** debe contener lo siguiente:
   
        var http = require('http');
        http.createServer(function(req,res) {
          res.writeHead(200, {'Content-Type': 'text/html'});
          res.end('Hello from Azure running node version: ' + process.version + '</br>');
        }).listen(process.env.PORT || 3000);
   
    Con esto aparecerá la versión de Node.js que se utiliza cuando navega en el sitio web.
2. Cree un sitio web y anote el nombre del sitio. Por ejemplo, el ejemplo siguiente utiliza las [herramientas de línea de comandos de Azure] para crear un sitio web de Azure llamado **mywebsite**y luego se habilita un repositorio Git para el sitio web.
   
        azure site create mywebsite --git
3. Cree un directorio nuevo llamado **bin** como secundario del directorio que contiene el archivo **server.js**.
4. Descargue la versión específica de **node.exe** (la versión para Windows) que desea utilizar con su aplicación. Por ejemplo, a continuación se utiliza **curl** para descargar la versión 0.8.1:
   
        curl -O http://nodejs.org/dist/v0.8.1/node.exe
   
    Guarde el archivo **node.exe** en la carpeta **bin** que se creó anteriormente.
5. Cree un archivo **iisnode.yml** en el mismo directorio en que se encuentra el archivo **server.js** y, a continuación, agregue el siguiente contenido al archivo **iisnode.yml**:
   
        nodeProcessCommandLine: "D:\home\site\wwwroot\bin\node.exe"
   
    Esta ruta de acceso es donde el archivo **node.exe** se ubicará dentro del proyecto una vez que haya publicado su aplicación en el sitio web de Azure.
6. Publique la aplicación. Por ejemplo, dado que anteriormente creé un sitio web con el parámetro --git, los siguientes comandos agregarán los archivos de aplicación a mi repositorio Git local y luego los insertarán en el repositorio del sitio web:
   
        git add .
        git commit -m "testing node v0.8.1"
        git push azure master
   
    Cuando se haya publicado la aplicación, abra el sitio web en un explorador. Debe aparecer un mensaje que diga "Hello from Azure running node version: v0.8.1".

## <a name="next-steps"></a>Pasos siguientes
Ahora que sabe cómo especificar la versión de Node.js que utiliza su aplicación, obtenga más información sobrel [funcionamiento con módulos], la [compilación e implementación de un sitio web Node.js](app-service-web/web-sites-nodejs-develop-deploy-mac.md) y [Uso de las herramientas de línea de comandos de Azure para Mac y Linux].

Para más información, vea el [Centro para desarrolladores de Node.js](/develop/nodejs/).

[Uso de las herramientas de línea de comandos de Azure para Mac y Linux]: xplat-cli-install.md
[herramientas de línea de comandos de Azure]: xplat-cli-install.md
[funcionamiento con módulos]: nodejs-use-node-modules-azure-apps.md
[Compilación e implementación de un sitio web de Node.js]: web-sites-nodejs-develop-deploy-mac.md



<!--HONumber=Nov16_HO3-->


