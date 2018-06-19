---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube con Visual Studio - Paso 5: Llamar a otro contenedor | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: ab3934e6f7f013dd21309dc8c98461983bdfe30a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898432"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introducción a Connected Environment con .NET Core y Visual Studio

Paso anterior: [Depurar un contenedor en Kubernetes](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Llamar a otro contenedor
En esta sección vamos a crear un segundo servicio (`mywebapi`) y haremos que `webfrontend` lo llame. Cada servicio se ejecutará en un contenedor diferente. Luego, depuraremos ambos contenedores.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Descargar el código de ejemplo de *mywebapi*
Por motivos de tiempo, descargaremos código de ejemplo de un repositorio de GitHub. Vaya a https://github.com/Azure/vsce y seleccione **Clonar o descargar** para descargar el repositorio de GitHub. El código de esta sección está en `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Ejecutar *mywebapi*
1. Abra el proyecto en `mywebapi` en una *ventana aparte de Visual Studio*.
1. Seleccione **Connected Environment for AKS** en la lista desplegable de configuración de inicio, como ya hizo con el proyecto `webfrontend`. Esta vez, en lugar de crear un entorno de desarrollo, seleccione el que ya ha creado. Al igual que antes, deje Space en el valor predeterminado `mainline` y haga clic en **Aceptar**. En la ventana de salida, verá que Visual Studio empieza a "dar forma" a este nuevo servicio en el entorno de desarrollo para acelerar las cosas cuando empiece la depuración.
1. Presione F5 y espere a que el servicio se compile e implemente. Sabrá que está listo cuando la barra de estado de Visual Studio cambie a color naranja.
1. Anote la dirección URL del punto de conexión que aparece en el panel **Connected Environment for AKS** de la ventana **Salida**, que tendrá un aspecto parecido a http://localhost:\<númeroDePuerto\>. Puede parecer que el contenedor se ejecuta localmente, pero en realidad se está ejecutando en nuestro entorno de desarrollo en Azure.
1. Cuando `mywebapi` esté listo, abra el explorador en la dirección de host local y anexe `/api/values` a la dirección URL para invocar la API GET predeterminada para `ValuesController`. 
1. Si todos los pasos se realizan correctamente, debería ver una respuesta del servicio `mywebapi` con ese aspecto.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Cursar una solicitud de *webfrontend* a *mywebapi*
Ahora, vamos a escribir código en `webfrontend` para cursar una solicitud en `mywebapi`. Cambie a la ventana de Visual Studio que tenga el proyecto `webfrontend`. En el archivo `HomeController.cs`, *reemplace* el código del método About por lo siguiente:

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

Observe cómo se usa la detección de servicios DNS de Kubernetes para hacer referencia al servicio como `http://mywebapi`. **El código en nuestro entorno de desarrollo se ejecuta de la misma manera en que lo haría en uno de producción**.

En el código de ejemplo anterior también se usa una clase `HeaderPropagatingHttpClient`. Esta clase auxiliar es el archivo `HeaderPropagation.cs` que se agregó al proyecto cuando lo configuró para usar Connected Environment. `HeaderPropagatingHttpClient` deriva de la clase conocida `HttpClient` y agrega funcionalidad para propagar encabezados específicos desde un objeto HttpRequest de ASP .NET existente a un objeto HttpRequestMessage saliente. Más adelante veremos cómo esto facilita una experiencia de desarrollo más productiva en escenarios de trabajo en equipo.

## <a name="debug-across-multiple-services"></a>Depurar en varios servicios
1. Llegado este punto, `mywebapi` debe seguir ejecutándose con el depurador asociado. Si no es así, presione la tecla F5 en el proyecto `mywebapi`.
1. Establezca un punto de interrupción en el método `Get(int id)` del archivo `ValuesController.cs` que controla las solicitudes GET de `api/values/{id}`.
1. En el proyecto `webfrontend` donde pegamos el código anterior, establezca un punto de interrupción justo antes del envío de una solicitud GET a `mywebapi/api/values`.
1. Presione la tecla F5 en el proyecto `webfrontend`. De nuevo, Visual Studio abrirá un explorador en el puerto localhost adecuado y se mostrará la aplicación web.
1. Haga clic en el vínculo "**About**" en la parte superior de la página para activar el punto de interrupción en el proyecto `webfrontend`. 
1. Presione F10 para continuar. Ahora, el punto de interrupción en el proyecto `mywebapi` estará activado.
1. Presione F5 para continuar; regresará al código en el proyecto `webfrontend`.
1. Si presiona F5 de nuevo, la solicitud se completará y se devolverá una página en el explorador. En la aplicación web, la página About mostrará un mensaje donde se concatenan ambos servicios: "Hello from webfrontend" y "Hello from mywebapi".

¡Bien hecho! Ahora tenemos una aplicación con varios contenedores donde cada uno de ellos se puede desarrollar e implementar por separado.

> [!div class="nextstepaction"]
> [Nociones del desarrollo en equipo](get-started-netcore-visualstudio-06.md)

