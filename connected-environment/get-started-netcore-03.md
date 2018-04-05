---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube - Paso 3: Crear una aplicación web ASP.NET Core | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: f858a013e4b0c2ce1c30b8f26f2dc33eebf19c27
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introducción a Connected Environment con .NET Core

Paso anterior: [Crear un entorno de desarrollo de Kubernetes en Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Crear una aplicación web ASP.NET Core
Si tiene [.NET Core](https://www.microsoft.com/net) instalado, puede crear rápidamente una aplicación web ASP.NET Core en una carpeta denominada `webfrontend`.
```cmd
dotnet new mvc --name webfrontend
```

También puede **descargar el código de ejemplo de GitHub**. Para ello, vaya a https://github.com/Azure/vsce y seleccione **Clonar o descargar** para descargar el repositorio de GitHub en su entorno local. El código de esta guía está en `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Actualizar un archivo de contenido
Connected Environment no se reduce exclusivamente a hacer que se ejecute código en Kubernetes: le permite ver rápidamente y de forma iterativa la forma en que los cambios de código surten efecto en un entorno de Kubernetes en la nube.

1. Busque el archivo `./Views/Home/Index.cshtml` y modifique el código HTML. Por ejemplo, cambie la línea 70 (donde se puede leer `<h2>Application uses</h2>`) por algo parecido a: `<h2>Hello k8s in Azure!</h2>`.
1. Guarde el archivo. Más tarde, en la ventana de terminal, verá un mensaje que indica que se ha actualizado un archivo en el contenedor en ejecución.
1. Vaya al explorador y actualice la página. La página web debería mostrar el HTML actualizado.

¿Qué ocurre? Las modificaciones de archivos de contenido, como HTML y CSS, no requieren que haya que recompilar en una aplicación web .NET Core, por lo que un comando `vsce up` activo sincronizará los archivos de contenido modificados de manera automática en el contenedor en ejecución en Azure, lo que constituye una forma rápida de ver las modificaciones de contenido.

## <a name="update-a-code-file"></a>Actualizar un archivo de código
Actualizar los archivos de código requiere un poco más de tarea, porque las aplicaciones .NET Core tienen que volver a generar los archivos binarios de la aplicación actualizada.

1. En la ventana de terminal, presione `Ctrl+C` (para detener `vsce up`).
1. Abra el archivo de código denominado `Controllers/HomeController.cs` y edite el mensaje que se mostrará en la página About: `ViewData["Message"] = "Your application description page.";`.
1. Guarde el archivo.
1. Ejecute `vsce up` en la ventana de terminal. 

Esto vuelve a generar la imagen del contenedor e implementa de nuevo el gráfico de Helm. Para ver cómo los cambios de código surten efecto en la aplicación en ejecución, vaya al menú About de la aplicación web.


Pero existe un *método todavía más rápido* para desarrollar código, que veremos en la siguiente sección. 
> [!div class="nextstepaction"]
> [Depurar un contenedor en Kubernetes](get-started-netcore-04.md)

