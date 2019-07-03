---
title: 'Tutorial: Creación de una aplicación de varios contenedores con Docker Compose'
description: Aprenda a administrar más de un contenedor y a comunicarse entre ellos en Visual Studio para Mac
author: bytesguy
ms.author: adhartle
ms.date: 06/17/2019
ms.openlocfilehash: df130e86de7f35c43459a70a12c0e9cfafbbe3a4
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67196110"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Creación de una aplicación de varios contenedores con Docker Compose

En este tutorial, aprenderá a administrar más de un contenedor y a comunicarse entre ellos mediante Docker Compose en Visual Studio para Mac.

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio para Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Creación de una aplicación web ASP.NET Core y adición de la compatibilidad con Docker

1. Para crear una nueva solución, vaya a **File > New Solution** (Archivo > Nueva solución).
1. En **.NET Core > App** (.NET Core > Aplicación), elija la plantilla **Web Application** (Aplicación web): ![Creación de una nueva aplicación ASP.NET](media/docker-quickstart-1.png)
1. Seleccione la plataforma de destino. En este ejemplo, usaremos .NET Core 2.2: ![Establecimiento de una plataforma de destino](media/docker-quickstart-2.png)
1. Escriba los detalles del proyecto, como el nombre del proyecto (_DockerDemoFrontEnd_ en este ejemplo) y el nombre de la solución (_DockerDemo_). El proyecto creado contiene todos los elementos básicos que necesita para crear y ejecutar un sitio web de ASP.NET Core.
1. En el Panel de solución, haga clic con el botón derecho en el proyecto DockerDemoFrontEnd y seleccione **Add > Add Docker Support** (Agregar > Agregar compatibilidad con Docker): ![Adición de compatibilidad con Docker](media/docker-quickstart-3.png)

Visual Studio para Mac agregará automáticamente un nuevo proyecto a la solución denominado **docker-compose** y agregará un archivo **Dockerfile** al proyecto existente.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Creación de una API web de ASP.NET Core y adición de la compatibilidad con Docker

A continuación, se creará un segundo proyecto que actuará como nuestra API de back-end. La plantilla de **API de .NET Core** incluye un controlador que nos permite controlar las solicitudes de RESTful.

1. Agregue un nuevo proyecto a la solución existente, haciendo clic con el botón derecho en la solución y eligiendo **Add > Add New Project** (Agregar > Agregar nuevo proyecto).
1. En **.NET Core > App** (.NET Core > Aplicación), elija la plantilla **API**.
1. Seleccione la plataforma de destino. En este ejemplo, usaremos .NET Core 2.2:
1. Escriba los detalles del proyecto, como el nombre del proyecto (_DockerDemoAPI_, en este ejemplo).
1. Una vez creado, vaya al Panel de solución, haga clic con el botón derecho en el proyecto DockerDemoFrontEnd y seleccione **Add > Add Docker Support** (Agregar > Agregar compatibilidad con Docker).

El archivo **docker-compose.yml** del proyecto **docker-compose** se actualizará automáticamente para incluir el proyecto de API junto con el proyecto de aplicación Web existente. Cuando se cree y ejecute el proyecto **docker-compose**, cada uno de estos proyectos se implementará en un contenedor Docker independiente.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integración de los dos contenedores

Ahora tenemos dos proyectos ASP.NET en nuestra solución y ambas están configuradas con compatibilidad con Docker. ¡A continuación, necesitamos agregar algún código!

1. En el proyecto `DockerDemoFrontEnd`, abra el archivo *Index.cshtml.cs* y reemplace el método `OnGet` por el código siguiente:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. En el archivo *Index.cshtml*, agregue una línea para mostrar `ViewData["Message"]` para que el archivo sea similar al código siguiente:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. Ahora, en el proyecto API web, agregue código al controlador de valores para personalizar el mensaje devuelto por la API para la llamada que agregó desde *webfrontend*:
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```
1. Establezca el proyecto `docker-compose` como proyecto de inicio y vaya a **Run > Start Debugging** (Ejecutar > Iniciar depuración). Si todo está configurado correctamente, verá el mensaje "Hello from webfrontend y webapi (con el valor 1)" (Hola desde webfrontend y webapi [Con valor 1]):

![Ejecución de una solución de varios contenedores de Docker](media/docker-multicontainer-debug.png)
