---
title: 'Inicio rápido: Crear un servicio web de ASP.NET Core en F#'
description: Aprenda a crear paso a paso un servicio web de ASP.NET Core en Visual Studio con F#.
ms.date: 08/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 884dfec4d3b8050fa6059cb0f505e1c7619336f9
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43224764"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Inicio rápido: Usar Visual Studio para crear su primer servicio web de ASP.NET Core en F#

En esta introducción a F# en Visual Studio de unos 5 a 10 minutos, creará una aplicación web de ASP.NET Core en F#.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

Primero creará un proyecto de API web de ASP.NET Core. En el tipo de proyecto se incluyen los archivos de plantilla, que constituyen un servicio web funcional por sí mismos, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual F#** y seleccione **Web**. En el panel central, elija **Aplicación web ASP.NET Core** y después elija **Aceptar**.

     Si no ve la categoría de plantilla de proyecto de **.NET Core**, elija el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

     ![Carga de trabajo ASP.NET en el instalador de Visual Studio](../ide/media/quickstart-aspnet-workload.png)

4. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione **ASP.NET Core 2.1** en el menú desplegable situado en la parte superior. Si en la lista no aparece **ASP.NET Core 2.1**, debe instalarlo siguiendo el vínculo **Descargar** que aparece en una barra amarilla en la parte superior del cuadro de diálogo. Elija **Aceptar**.

## <a name="explore-the-ide"></a>Explorar el IDE

1. En la barra de herramientas del **Explorador de soluciones**, expanda la carpeta **Controllers** y después elija **ValuesController.fs** para abrirla en el editor.

   ![Explorador de soluciones con la carpeta Controllers expandida en el proyecto de API web de F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Después, modifique el miembro `Get()` para que sea como sigue:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

El código es sencillo. Se enlaza una matriz de valores de F# al nombre `values` y luego se pasa a ASP.NET Core MVC Framework como un `ActionResult`. ASP.NET Core se encarga de hacer el resto.

El resultado debería tener un aspecto similar a este en el editor:

![Miembro Get modificado](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

2. La página debería navegar hasta la ruta `/api/values`, pero si no es así, escriba `https://localhost:44396/api/values` en el explorador.

El explorador web mostrará ahora coincidencias de JSON que escribió antes.

## <a name="next-steps"></a>Pasos siguientes

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que le haya servido para aprender un poco sobre F#, ASP.NET Core y el IDE de Visual Studio. Para que la aplicación se ejecute en un servidor público, haga clic en el botón siguiente.

> [!div class="nextstepaction"]
> [Implementar la aplicación en Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Para saber más sobre F#, eche un vistazo a la [Guía de F#](/dotnet/fsharp/index).