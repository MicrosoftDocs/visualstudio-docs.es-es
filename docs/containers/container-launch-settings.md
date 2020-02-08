---
title: Configuración de inicio de las herramientas de contenedor de Visual Studio
author: ghogen
description: Información general del proceso de compilación de las herramientas de contenedor
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 1c9786c29573da3b0149a9ec6578f2ce58c4de9f
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542599"
---
# <a name="container-tools-launch-settings"></a>Configuración de inicio de las herramientas de contenedor

En la carpeta *Properties* de un proyecto de ASP.NET Core, encontrará el archivo launchSettings.json, que contiene la configuración que controla el modo en que se inicia la aplicación web en el equipo de desarrollo. Para obtener información detallada sobre cómo se usa este archivo en el desarrollo de ASP.NET, vea [Usar varios entornos en ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). En *launchSettings.json*, los valores de la sección **Docker** están relacionados con la forma en que Visual Studio controla las aplicaciones en contenedores.

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

El valor commandName identifica que esta sección se aplica a las herramientas de contenedor. En la tabla siguiente se muestran las propiedades que se pueden establecer en esta sección:

::: moniker range="vs-2017"

|Nombre de valor|Versión|Ejemplo|Descripción|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Indica si se debe iniciar el explorador después de iniciar correctamente el proyecto.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Esta dirección URL se usa al iniciar el explorador.  Los tokens de reemplazo admitidos para esta cadena son:<br>   {Scheme}: se reemplaza por "http" o "https" en función de si se usa SSL.<br>   {ServiceHost}: normalmente se reemplaza por "localhost". Cuando el destino son los contenedores de Windows en Windows 10 RS3 o versiones anteriores, se reemplaza por la dirección IP del contenedor.<br>   {ServicePort}: normalmente se reemplaza por sslPort o httpPort, en función de si se usa SSL.  Cuando el destino son los contenedores de Windows en Windows 10 RS3 o versiones anteriores, se reemplaza por "443" o "80", en función de si se usa SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nombre de valor         | Ejemplo                                               | Descripción                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Estos argumentos de la línea de comandos se usan al iniciar el proyecto en el contenedor.                                     |
| environmentVariables | "environmentVariables": {                             | Estos valores de variables de entorno se pasan al proceso cuando se inicia en el contenedor.                       |
|                      | "ASPNETCORE_URLS": "https://+:443; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Este puerto del host se asigna al puerto 80 del contenedor al iniciar el contenedor.                                |
|                      |                                                       | Si no se especifica, el valor se toma del valor iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Indica si se debe iniciar el explorador después de iniciar correctamente el proyecto.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Esta dirección URL se usa al iniciar el explorador. Los tokens de reemplazo admitidos para esta cadena son:                          |
|                      |                                                       | - {Scheme}: se reemplaza por "http" o "https" en función de si se usa SSL.                                   |
|                      |                                                       | - {ServiceHost}: normalmente se reemplaza por "localhost".                                                                    |
|                      |                                                       | Cuando el destino son los contenedores de Windows en Windows 10 RS3 o versiones anteriores, se reemplaza por la dirección IP del contenedor.           |
|                      |                                                       | - {ServicePort}: normalmente se reemplaza por sslPort o httpPort, en función de si se usa SSL.                   |
|                      |                                                       | Cuando el destino son los contenedores de Windows en Windows 10 RS3 o versiones anteriores, se reemplaza por "443" u "80",         |
|                      |                                                       | dependiendo de si se usa SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Este puerto del host se asigna al puerto 443 del contenedor al iniciar el contenedor.                               |
|                      |                                                       | Si no se especifica, el valor se toma del valor iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Indica si se debe usar SSL al iniciar el proyecto. Si no se especifica useSSL, se usa SSL cuando sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

Configure el proyecto estableciendo las [propiedades de compilación las herramientas de contenedor](container-msbuild-properties.md).

## <a name="see-also"></a>Vea también

[Propiedades de compilación de Docker Compose ](docker-compose-properties.md)
