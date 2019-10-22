---
title: Depurar aplicaciones en un contenedor de Docker local | Microsoft Docs
description: Aprenda a modificar una aplicación que se ejecuta en un contenedor de Docker local, a actualizar el contenedor mediante Editar y Actualizar y luego a establecer puntos de interrupción de depuración.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 5af092bbcb987f45b10121f37d40eaa5466c3da5
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71126158"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Depurar aplicaciones en un contenedor de Docker local

Visual Studio ofrece una forma coherente de desarrollar en un contenedor de Docker y validar la aplicación localmente. sin tener que reiniciar el contenedor cada vez que se realiza un cambio en el código.

En este artículo se explica cómo usar Visual Studio para iniciar una aplicación web de ASP.NET Core en un contenedor de Docker local, realizar cambios y luego actualizar el explorador para ver los cambios. También se muestra cómo establecer puntos de interrupción para la depuración de aplicaciones web de ASP.NET Core en contenedores y aplicaciones de consola de .NET Framework.

## <a name="prerequisites"></a>Requisitos previos

Para depurar aplicaciones en un contenedor de Docker local, deben instalarse las siguientes herramientas:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con la carga de trabajo Desarrollo web instalada

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con la carga de trabajo Desarrollo web instalada

::: moniker-end

Para ejecutar contenedores de Docker de forma local, se necesita un cliente de Docker local. Puede usar el [cuadro de herramientas de Docker](https://www.docker.com/products/docker-toolbox), que requiere que Hyper-V esté deshabilitado. También puede usar [Docker para Windows](https://www.docker.com/get-docker), que usa Hyper-V y requiere Windows 10. 

Los contenedores de Docker están disponibles para proyectos de .NET Framework y .NET Core. Veamos dos ejemplos. En primer lugar, vemos una aplicación web de .NET Core. Luego vemos una aplicación de consola de .NET Framework.

## <a name="create-a-web-app"></a>Creación de una aplicación web

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Edición del código y actualización

Para iterar cambios rápidamente, puede iniciar la aplicación en un contenedor. Luego siga realizando cambios y viéndolos como haría con IIS Express.

1. Establezca **Configuración de solución** en **Depurar**. Luego presione **Ctrl**+**F5** para compilar la imagen de Docker y ejecutarla localmente.

    Cuando la imagen del contenedor se ha compilado y se está ejecutando en un contenedor de Docker, Visual Studio inicia la aplicación web en el explorador predeterminado.

2. Vaya a la página *Índice*. Los cambios se van a realizar en esta página.
3. Vuelva a Visual Studio y abra *Index.cshtml*.
4. Agregue el siguiente contenido HTML al final del archivo y luego guarde los cambios.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. En la ventana de salida, cuando haya finalizado la compilación de .NET y vea las siguientes líneas, vuelva al explorador y actualice la página:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Se han aplicado los cambios.

### <a name="debug-with-breakpoints"></a>Depurar con puntos de interrupción

A menudo, los cambios requieren inspección adicional. Puede usar las características de depuración de Visual Studio para esta tarea.

1. En Visual Studio, abra *Index.cshtml.cs*.
2. Reemplace el contenido del método `OnGet` por el código siguiente:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Establezca un punto de interrupción a la izquierda de la línea de código.
4. Presione F5 para iniciar la depuración y alcanzar el punto de interrupción.
5. Cambie a Visual Studio para ver el punto de interrupción. Inspeccione los valores.

   ![Punto de interrupción](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Creación de una aplicación de consola de .NET Framework

Cuando se usan proyectos de aplicación de consola de .NET Framework, no se admite la opción de agregar compatibilidad de Docker sin orquestación. Puede seguir usando el siguiente procedimiento aunque solo use un proyecto de Docker.

1. Cree un nuevo proyecto de aplicación de consola de .NET Framework.
1. En el Explorador de soluciones, haga clic con el botón derecho en el nodo del proyecto y seleccione **Agregar** > **Container Orchestration Support** (Compatibilidad con la orquestación de contenedores).  En el cuadro de diálogo que aparece, seleccione **Docker Compose**. Se agregan al proyecto un Dockerfile y un proyecto de Docker Compose con archivos de compatibilidad asociados.

### <a name="debug-with-breakpoints"></a>Depurar con puntos de interrupción

1. En el Explorador de soluciones, abra *Program.cs*.
2. Reemplace el contenido del método `Main` por el código siguiente:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Establezca un punto de interrupción a la izquierda de la línea de código.
4. Presione F5 para iniciar la depuración y alcanzar el punto de interrupción.
5. Cambie a Visual Studio para ver el punto de interrupción e inspeccionar los valores.

   ![Punto de interrupción](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Reutilización del contenedor

Durante el ciclo de desarrollo, Visual Studio solo vuelve a compilar las imágenes del contenedor y el propio contenedor cuando se modifica el Dockerfile. Si no cambia el Dockerfile, Visual Studio vuelve a usar el contenedor a partir de una ejecución anterior.

Si ha modificado manualmente el contenedor y quiere reiniciar con una imagen de contenedor limpia, use el comando **Compilar** > **Limpiar** de Visual Studio y luego compile del modo habitual.

## <a name="troubleshoot"></a>Solucionar problemas

Aprenda a [solucionar problemas de desarrollo de Visual Studio con Docker](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Más información acerca de Docker con Visual Studio, Windows y Azure

* Obtenga más información sobre el [desarrollo de contenedores con Visual Studio](/visualstudio/containers).
* Para compilar e implementar un contenedor de Docker, vea [Integración de Docker para Azure Pipelines](https://aka.ms/dockertoolsforvsts).
* Para obtener un índice de artículos de Windows Server y Nano Server, vea [Contenedores en la documentación de Windows](https://aka.ms/containers).
* Obtenga información sobre [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) y vea la [documentación de Azure Kubernetes Service](/azure/aks).
