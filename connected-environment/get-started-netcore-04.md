---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube - Paso 4: Depurar un contenedor en Kubernetes | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: f06489194f70a3e7e617f4022917cd1d4a96337f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introducción a Connected Environment con .NET Core
 
Paso anterior: [Crear una aplicación web ASP.NET Core](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Seleccionar la configuración de depuración de VSCE
1. Para abrir la vista Depurar, haga clic en el icono Depurar de la **barra de actividades** en el lateral de VS Code.
1. Seleccione **Iniciar .NET Core (VSCE)** como configuración de depuración activa.

![](media/debug-configuration.png)

> [!Note]
> Si no ve ningún comando de Connected Environment en la paleta de comandos, confirme que tiene [instalada la extensión de VS Code para Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="debug-the-container-in-kubernetes"></a>Depurar el contenedor en Kubernetes
Presione **F5** para depurar el código en Kubernetes.

Al igual que sucede con el comando `up`, el código se sincroniza con el entorno de desarrollo y se genera e implementa un contenedor en Kubernetes. En esta ocasión, el depurador está asociado al contenedor remoto, por supuesto.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Establezca un punto de interrupción en un archivo de código del lado servidor, por ejemplo, dentro de la función `Index()` en el archivo de origen `Controllers/HomeController.cs`. Si se actualiza la página del explorador, se seleccionará el punto de interrupción.

Tendrá acceso completo a la información de depuración tal y como lo haría si el código se ejecutara localmente, como las pilas de llamadas, las variables locales, la información de excepciones, etc.

## <a name="edit-code-and-refresh"></a>Editar el código y actualizar
Con el depurador activo, realice una modificación de código. Por ejemplo, modificar el mensaje de la página About en `Controllers/HomeController.cs`. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Guarde el archivo y, en el **panel Acciones de depuración**, haga clic en el botón **Actualizar**. 

![](media/debug-action-refresh.png)

En lugar de volver a generarse e implementarse una nueva imagen de contenedor cada vez que se realicen modificaciones del código (lo que suele conllevar mucho tiempo), Connected Environment irá recompilando cada vez más código dentro del contenedor existente para lograr un bucle de edición y depuración más rápido.

Actualice la aplicación web en el explorador y vaya a la página About. Debería ver el mensaje personalizado en la interfaz de usuario.

**Ya dispone de un método para iterar rápidamente por el código y depurar directamente en Kubernetes.** Veamos ahora cómo se puede crear un segundo contenedor y llamarlo.

> [!div class="nextstepaction"]
> [Llamar a un servicio que se ejecuta en un contenedor aparte](get-started-netcore-05.md)
