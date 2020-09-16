---
title: Aplicación de varios contenedor con Docker Compose
description: Aprenda a administrar más de un contenedor y a comunicarse entre ellos en Visual Studio para Mac
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: e46a66ab9ec05f8e7ad13091fdced01bffbd93b5
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038678"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Creación de una aplicación de varios contenedores con Docker Compose

En este tutorial, aprenderá a administrar más de un contenedor y a comunicarse entre ellos mediante Docker Compose en Visual Studio para Mac.

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio para Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Creación de una aplicación web ASP.NET Core y adición de la compatibilidad con Docker

1. Para crear una nueva solución, vaya a **File > New Solution** (Archivo > Nueva solución).
1. En **Web y consola > Aplicación** elija la plantilla **Aplicación web**: ![Creación de una nueva aplicación ASP.NET](media/docker-quickstart-1.png)
1. Seleccione la plataforma de destino. En este ejemplo, usaremos .NET Core 3.1: ![Establecimiento de una plataforma de destino](media/docker-quickstart-2.png)
1. Escriba los detalles del proyecto, como el nombre del proyecto (_DockerDemoFrontEnd_ en este ejemplo) y el nombre de la solución (_DockerDemo_). El proyecto creado contiene todos los elementos básicos que necesita para crear y ejecutar un sitio web de ASP.NET Core.
1. En el Panel de solución, haga clic con el botón derecho en el proyecto DockerDemoFrontEnd y seleccione **Add > Add Docker Support** (Agregar > Agregar compatibilidad con Docker): ![Adición de compatibilidad con Docker](media/docker-quickstart-3.png)

Visual Studio para Mac agregará automáticamente un nuevo proyecto a la solución denominado **docker-compose** y agregará un archivo **Dockerfile** al proyecto existente.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Creación de una API web de ASP.NET Core y adición de la compatibilidad con Docker

A continuación, se creará un segundo proyecto que actuará como nuestra API de back-end. La plantilla de **API de .NET Core** incluye un controlador que nos permite controlar las solicitudes de RESTful.

1. Agregue un nuevo proyecto a la solución existente, haciendo clic con el botón derecho en la solución y eligiendo **Add > Add New Project** (Agregar > Agregar nuevo proyecto).
1. En **Web y consola > Aplicación** elija la plantilla **API**.
1. Seleccione la plataforma de destino. En este ejemplo, usaremos .NET Core 3.1.
1. Escriba los detalles del proyecto, como el nombre del proyecto (_MyWebAPI_, en este ejemplo).
1. Una vez creado, vaya al Panel de solución, haga clic con el botón derecho en el proyecto MyWebAPI y seleccione **Agregar > Agregar compatibilidad con Docker**.

El archivo **docker-compose.yml** del proyecto **docker-compose** se actualizará automáticamente para incluir el proyecto de API junto con el proyecto de aplicación Web existente. Cuando se cree y ejecute el proyecto **docker-compose**, cada uno de estos proyectos se implementará en un contenedor Docker independiente.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integración de los dos contenedores

Ahora tenemos dos proyectos ASP.NET en nuestra solución y ambas están configuradas con compatibilidad con Docker. ¡A continuación, necesitamos agregar algún código!

1. En el proyecto `DockerDemoFrontEnd`, abra el archivo *Pages/Index.cshtml.cs* y reemplace el método `OnGet` por el código siguiente:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > En el código de producción, no se debe desechar `HttpClient` después de cada solicitud. Para obtener los procedimientos recomendados, vea [Uso de HttpClientFactory para implementar solicitudes HTTP resistentes](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

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
  
1. En los proyectos de front-end y de API web, marque como comentario la llamada a [Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) en el método `Configure` en *Startup.cs*, ya que este código de ejemplo usa HTTP, no HTTPS, para llamar a la API web.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Establezca el proyecto `docker-compose` como proyecto de inicio y vaya a **Run > Start Debugging** (Ejecutar > Iniciar depuración). Si todo está configurado correctamente, verá el mensaje "Hello from webfrontend y webapi (con el valor 1)" (Hola desde webfrontend y webapi [Con valor 1]):

![Ejecución de una solución de varios contenedores de Docker](media/docker-multicontainer-debug.png)
