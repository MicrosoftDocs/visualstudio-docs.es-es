---
title: Uso de Visual Studio para crear una aplicación web ASP.NET Core en C#
description: Obtenga información sobre cómo crear una aplicación web ASP.NET Core en Visual Studio con C#, paso a paso.
ms.custom: mvc
ms.date: 07/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9978a7eb80a833eeb81796694b958a62a35cd347
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469144"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Inicio rápido: uso de Visual Studio para crear su primera aplicación web ASP.NET Core

En esta introducción de 5 a 10 minutos sobre cómo usar Visual Studio, creará una aplicación web simple "Hola mundo" mediante el uso de una plantilla de proyecto ASP.NET y el lenguaje de programación C#.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación web ASP.NET Core. Esta es la manera de hacerlo.

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y luego elija **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core**. Luego nombre al archivo `HelloWorld` y haga clic en **Aceptar**.

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, compruebe que **ASP.NET Core 2.0** aparece en el menú desplegable de la parte superior. Luego elija **Aplicación web** y haga clic en **Aceptar**.

  ![Ver el archivo .gif animado que muestra cómo crear un proyecto de ASP.NET Core de C# en Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

  Poco después, Visual Studio abre el archivo de proyecto.

   > [!NOTE]
   > Si no ve la categoría de plantilla de proyecto de **.NET Core**, elija el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda.
   >
   > ![Abrir el Instalador de Visual Studio desde el cuadro de diálogo Nuevo proyecto](../ide/media/open-visual-studio-installer.png)
   >
   > Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después haga clic en **Modificar**.
   >
   > ![Carga de trabajo ASP.NET en el instalador de Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Es posible que deba cerrar Visual Studio para continuar con la instalación de la carga de trabajo nueva).

## <a name="create-and-run-the-app"></a>Crear y ejecutar la aplicación

Luego se crea y se ejecuta la aplicación web "Hello World". Esta es la manera de hacerlo.

1. En el **Explorador de soluciones**, expanda la carpeta **Páginas** y después elija **About.cshtml**.

   Este archivo corresponde a una página denominada **Acerca de** de la aplicación web.

   ![Página Acerca de de la aplicación web](../ide/media/csharp-aspnet-about-page.png)

1. Cambie el texto "información adicional" para que rece "**Hello World!**".

1. En el **Explorador de soluciones**, expanda **About.cshtml** y luego elija **About.cshtml.cs**.

1. Cambie el texto del mensaje "descripción de la aplicación" para que rece "**¿Cuál es mi mensaje?**".

1. Seleccione **IIS Express** o presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

  ![Ver el archivo .gif animado que muestra cómo crear y ejecutar una aplicación web de ASP.NET Core de C# en Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Si recibe un mensaje de error que indica **No se puede conectar al servidor web "IIS Express"**, cierre Visual Studio y, luego, ábralo mediante la opción **Ejecutar como administrador** que aparece si hace clic con el botón derecho o en el menú contextual. A continuación, vuelva a ejecutar la aplicación.

1. Compruebe que la página **Acerca de** incluye el texto actualizado.

1. Cierre el explorador web.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE (entorno de desarrollo integrado) de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Introducción a C# y ASP.NET Core en Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Vea también

[Publicar una aplicación web en Azure App Service mediante Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
