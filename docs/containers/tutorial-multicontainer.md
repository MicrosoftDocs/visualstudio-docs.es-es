---
title: Uso de varios contenedores con Docker Compose
author: ghogen
description: Aprenda a usar varios contenedores con Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: e5bd7673bc600d0ae84b0a343a071e2a8621e4b9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150215"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Tutorial: Creación de una aplicación de varios contenedores con Docker Compose

En este tutorial se aprende a administrar más de un contenedor y a comunicarse entre ellos mediante las herramientas de contenedor de Visual Studio.  La administración de varios contenedores requiere *orquestación de contenedor* y un orquestador como Docker Compose, Kubernetes o Service Fabric. Aquí se va a usar Docker Compose. Docker Compose es ideal para las pruebas y la depuración locales durante el ciclo de desarrollo.

## <a name="prerequisites"></a>Requisitos previos

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con las cargas de trabajo **Desarrollo web**, **Azure Tools** o **Desarrollo multiplataforma de .NET Core** instaladas
* [Herramientas de desarrollo de .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) para el desarrollo con .NET Core 2.2
* [Herramientas de desarrollo de .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) para el desarrollo con .NET Core 3.1
::: moniker-end

## <a name="create-a-web-application-project"></a>Creación de un proyecto de aplicación web

En Visual Studio, cree un proyecto de **Aplicación web de ASP.NET Core**, denominado `WebFrontEnd`, para crear una aplicación web con páginas de Razor.
  
::: moniker range="vs-2017"

No seleccione **Habilitar compatibilidad con Docker**. Esta se agrega más adelante.

![Captura de pantalla de la creación del proyecto web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Creación de un proyecto de Aplicación web de ASP.NET Core](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

No seleccione **Habilitar compatibilidad con Docker**. Esta se agrega más adelante.

![Captura de pantalla de la pantalla Información adicional cuando se crea un proyecto web. La opción Habilitar compatibilidad con Docker no está seleccionada.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Creación de un proyecto de API web

Agregue un proyecto a la misma solución y asígnele el nombre *MyWebAPI*. Seleccione **API** como tipo de proyecto y desactive la casilla de **Configure for HTTPS** (Configurar para HTTPS). En este diseño solo se usa SSL para la comunicación con el cliente, no para la comunicación entre contenedores de la misma aplicación web. Solo `WebFrontEnd` necesita HTTPS y en el código de los ejemplos se supone que ha desactivado esa casilla. En general, los certificados de desarrollador de .NET que usa Visual Studio solo se admiten para las solicitudes externas a contenedores, no para las solicitudes de contenedor a contenedor.

::: moniker range="vs-2017"
   ![Captura de pantalla de la creación del proyecto de API web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Captura de pantalla de la creación del proyecto de API web](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Adición de código para llamar a la API web

1. En el proyecto `WebFrontEnd`, abra el archivo *Index.cshtml.cs* y reemplace el método `OnGet` por el código siguiente.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > En el código del mundo real, no se debe desechar `HttpClient` después de cada solicitud. Para obtener los procedimientos recomendados, vea [Uso de HttpClientFactory para implementar solicitudes HTTP resistentes](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Para .NET Core 3.1 en Visual Studio 2019 o posterior, la plantilla de API web usa WeatherForecast API, por lo que debe quitar la marca de comentario de esa línea y comentar la línea para ASP.NET 2.x.

1. En el archivo *Index.cshtml*, agregue una línea para mostrar `ViewData["Message"]` para que el archivo sea similar al código siguiente:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (ASP.NET 2.x solo) Ahora, en el proyecto de API web, agregue código al controlador de valores para personalizar el mensaje devuelto por la API para la llamada agregada desde *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Con .NET Core 3.1, no es necesario, ya que puede usar WeatherForecast API que ya existe. Sin embargo, debe marcar como comentario la llamada a <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> en el método `Configure` en *Startup.cs*, porque este código usa HTTP, no HTTPS, para llamar a la API web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. En el proyecto `WebFrontEnd`, seleccione **Agregar > Compatibilidad con el orquestador de contenedores**. Aparece el cuadro de diálogo **Opciones de soporte técnico de Docker**.

1. Seleccione **Docker Compose**.

1. Seleccione el sistema operativo de destino, por ejemplo, Linux.

   ![Captura de pantalla de la elección del sistema operativo de destino](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio crea un archivo *docker-compose.yml* y un archivo *.dockerignore* en el nodo **docker-compose** de la solución, y ese proyecto se muestra en negrita, lo que indica que es el proyecto de inicio.

   ![Captura de pantalla del Explorador de soluciones con el proyecto docker-compose agregado](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *docker-compose.yml* aparece de la manera siguiente:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   El archivo *.dockerignore* contiene los tipos de archivo y las extensiones que no quiere que Docker incluya en el contenedor. Normalmente, estos archivos están asociados al entorno de desarrollo y el control de código fuente, no forman parte de la aplicación o el servicio que se está desarrollando.

   Vea la sección **Herramientas de contenedor** del panel de salida para obtener detalles de los comandos que se ejecutan.  Puede ver que la herramienta de línea de comandos docker-compose se usa para configurar y crear los contenedores en tiempo de ejecución.

1. En el proyecto de API web, vuelva a hacer clic con el botón derecho en el nodo del proyecto y seleccione **Agregar** > **Compatibilidad con el orquestador de contenedores**. Seleccione **Docker Compose** y, después, el mismo sistema operativo de destino.  

    > [!NOTE]
    > En este paso, Visual Studio le ofrece crear un Dockerfile. Si lo hace en un proyecto que ya tiene compatibilidad con Docker, se le pregunta si quiere sobrescribir el Dockerfile existente. Si ha realizado cambios que quiere conservar en el Dockerfile, seleccione no.

    Visual Studio realiza algunos cambios en el archivo YML de Docker Compose. Ahora ambos servicios están incluidos.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Ejecute el sitio localmente ahora (F5 o Ctrl + F5) para comprobar que funciona según lo previsto. Si todo está configurado correctamente con la versión .NET Core 2.x, aparece el mensaje "Hello from webfrontend and webapi (with value 1)" (Hola desde webfrontend y webapi [con valor 1]).  Con .NET Core 3, verá los datos de previsión meteorológica.

   El primer proyecto que se usa al agregar la orquestación de contenedores está configurado para iniciarse al ejecutar o depurar. Puede configurar la acción de inicio en las **Propiedades del proyecto** del proyecto docker-compose.  En el nodo del proyecto docker-compose, haga clic con el botón derecho para abrir el menú contextual y luego seleccione **Propiedades** o use Alt + Entrar.  En la captura de pantalla siguiente se muestran las propiedades deseables para la solución que se usa aquí.  Por ejemplo, puede cambiar la página que se carga mediante la personalización de la propiedad **URL de servicio**.

   ![Captura de pantalla de las propiedades del proyecto docker-compose](media/tutorial-multicontainer/launch-action.png)

   Esto es lo que se ve cuando se inicia (en la versión .NET Core 2.x):

   ![Captura de pantalla de la aplicación web en ejecución](media/tutorial-multicontainer/webfrontend.png)

   La aplicación web para .NET 3.1 muestra los datos meteorológicos en formato JSON.

## <a name="next-steps"></a>Pasos siguientes

Vea las opciones para implementar [contenedores en Azure](/azure/containers).

## <a name="see-also"></a>Consulte también
  
[Docker Compose](https://docs.docker.com/compose/)  
[Herramientas de contenedor](./index.yml)