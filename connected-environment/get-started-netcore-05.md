---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube - Paso 5: Llamar a otro contenedor | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 6ef3a79d0b79feae64adcaebe31daa48ba75ab75
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887341"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introducción a Connected Environment con .NET Core

Paso anterior: [Depurar un contenedor en Kubernetes](get-started-netcore-04.md)

En esta sección vamos a crear un segundo servicio (`mywebapi`) y haremos que `webfrontend` lo llame. Cada servicio se ejecutará en un contenedor diferente. Luego, depuraremos ambos contenedores.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Descargar el código de ejemplo de *mywebapi*
Por motivos de tiempo, descargaremos código de ejemplo de un repositorio de GitHub. Vaya a https://github.com/Azure/vsce y seleccione **Clonar o descargar** para descargar el repositorio de GitHub. El código de esta sección está en `vsce/samples/dotnetcore/getting-started/mywebapi`.


## <a name="run-mywebapi"></a>Ejecutar *mywebapi*
1. Abra la carpeta `mywebapi` en una *ventana de VS Code aparte*.
1. Presione F5 y espere a que el servicio se compile e implemente. Sabrá que está listo cuando aparezca la barra de depuración de VS Code.
1. Anote la dirección URL del punto de conexión, que tendrá un aspecto parecido a http://localhost:\<númeroDePuerto\>. **Consejo: La barra de estado de VS Code mostrará una dirección URL interactiva.** Puede parecer que el contenedor se ejecuta localmente, pero en realidad se está ejecutando en nuestro entorno de desarrollo en Azure. La razón de usar la dirección de host local es que `mywebapi` no tiene definido ningún punto de conexión público y solo se puede tener acceso a ella desde dentro de la instancia de Kubernetes. Para mayor comodidad, y de cara a facilitar la interacción con el servicio privado desde el equipo local, Connected Environment crea un túnel SSH temporal hacia el contenedor que se ejecuta en Azure.
1. Cuando `mywebapi` esté listo, abra el explorador en la dirección de host local. Anexe `/api/values` a la dirección URL para invocar la API GET predeterminada para `ValuesController`. 
1. Si todos los pasos se realizan correctamente, debería ver una respuesta del servicio `mywebapi`.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Cursar una solicitud de *webfrontend* a *mywebapi*
Ahora, vamos a escribir código en `webfrontend` para cursar una solicitud en `mywebapi`.
1. Cambie a la ventana de VS Code de `webfrontend`.
1. *Reemplace* el código por el método About:

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

En el código de ejemplo anterior también se usa una clase `HeaderPropagatingHttpClient`. Esta clase auxiliar se agregó a la carpeta de código cuando ejecutó `vsce init`. `HeaderPropagatingHttpClient` deriva de la clase conocida `HttpClient` y agrega funcionalidad para propagar encabezados específicos desde un objeto HttpRequest de ASP .NET existente a un objeto HttpRequestMessage saliente. Más adelante veremos cómo esto facilita una experiencia de desarrollo más productiva en escenarios de trabajo en equipo.


## <a name="debug-across-multiple-services"></a>Depurar en varios servicios
1. Llegado este punto, `mywebapi` debe seguir ejecutándose con el depurador asociado. Si no es así, presione la tecla F5 en el proyecto `mywebapi`.
1. Establezca un punto de interrupción en el método `Get(int id)` que controla las solicitudes GET de `api/values/{id}`.
1. En el proyecto `webfrontend`, establezca un punto de interrupción justo antes del envío de una solicitud GET a `mywebapi/api/values`.
1. Presione la tecla F5 en el proyecto `webfrontend`.
1. Invoque la aplicación web y recorra el código en ambos servicios.
1. En la aplicación web, la página About mostrará un mensaje donde se concatenan ambos servicios: "Hello from webfrontend" y "Hello from mywebapi".


¡Bien hecho! Ahora tenemos una aplicación con varios contenedores donde cada uno de ellos se puede desarrollar e implementar por separado.

> [!div class="nextstepaction"]
> [Nociones del desarrollo en equipo](get-started-netcore-06.md)

