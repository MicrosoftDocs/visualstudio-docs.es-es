---
title: Creación de una aplicación web ASP.NET Core en C#
description: Obtenga información sobre cómo crear una aplicación web simple Hola mundo en Visual Studio con C# y ASP.NET Core, paso a paso.
ms.custom: mvc
ms.date: 10/29/2018
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
ms.openlocfilehash: ab4ce9393e922dec6677d37d7679e1a400a2b5fc
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158884"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Inicio rápido: Uso de Visual Studio para crear la primera aplicación web ASP.NET Core

En esta introducción de 5 a 10 minutos sobre cómo usar Visual Studio, creará una aplicación web simple "Hola mundo" mediante el uso de una plantilla de proyecto ASP.NET y el lenguaje de programación C#.

## <a name="before-you-begin"></a>Antes de empezar

### <a name="install-visual-studio"></a>Instalar Visual Studio

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

### <a name="update-visual-studio"></a>Actualizar Visual Studio

Si ya ha instalado Visual Studio, asegúrese de que se está ejecutando la versión más reciente. Para obtener más información sobre cómo actualizar la instalación, vea la página [Actualizar Visual Studio 2017 a la versión más reciente](../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Elija su tema (opcional)

En esta guía de inicio rápido se incluyen capturas de pantalla que utilizan el tema oscuro. Si no está usando el tema oscuro pero le gustaría hacerlo, vea la página [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](quickstart-personalize-the-ide.md) para obtener información sobre cómo hacerlo.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación web ASP.NET Core. Esta es la manera de hacerlo.

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y luego elija **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core**. Luego nombre al archivo `HelloWorld` y haga clic en **Aceptar**.

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione **ASP.NET Core 2.0** o posterior en el menú desplegable situado en la parte superior y después seleccione **Aplicación web**.

   > [!NOTE]
   > Si no ve **ASP.NET Core 2.0** o posterior en el menú desplegable superior, asegúrese de que se está ejecutando la versión más reciente de Visual Studio. Para obtener más información sobre cómo actualizar la instalación, vea la página [Actualizar Visual Studio 2017 a la versión más reciente](../install/update-visual-studio.md).

   ![Ver el archivo .gif animado que muestra cómo crear un proyecto de ASP.NET Core de C# en Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

   Poco después, Visual Studio abre el archivo de proyecto.

   > [!NOTE]
   > Si no ve la categoría de plantilla de proyecto de **.NET Core**, elija el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda. (Según la configuración de pantalla, es posible que tenga que desplazarse para verlo).
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

1. En el **Explorador de soluciones** de Visual Studio, expanda la carpeta **Páginas**. Luego elija **About.cshtml**.

   ![Selección del archivo About.cshtml desde el Explorador de soluciones](../ide/media/csharp-aspnet-about-page-html-file.png)

   Este archivo corresponde a una página denominada **Acerca de** en la aplicación web y que se ejecuta en un explorador web.

   ![Página Acerca de de la aplicación web](../ide/media/csharp-aspnet-about-page.png)

1. En el editor de código de Visual Studio, cambie el texto "información adicional" para que diga "**Hola mundo**".

1. En el **Explorador de soluciones**, expanda **About.cshtml** y luego elija **About.cshtml.cs**.

1. Cambie el texto del mensaje "descripción de la aplicación" para que rece "**¿Cuál es mi mensaje?**".

1. Seleccione **IIS Express** o presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

   ![Ver el archivo .gif animado que muestra cómo crear y ejecutar una aplicación web de ASP.NET Core de C# en Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Si recibe un mensaje de error que dice **No se puede conectar al servidor web "IIS Express"** o un mensaje de error que menciona un certificado SSL, cierre Visual Studio. Después, abra Visual Studio mediante la opción **Ejecutar como administrador** en el menú contextual. A continuación, vuelva a ejecutar la aplicación.

1. En el explorador web, compruebe que la página **Acerca de** incluye el texto actualizado.

1. Cierre el explorador web.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE (entorno de desarrollo integrado) de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Introducción a C# y ASP.NET Core en Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Vea también

[Publicar una aplicación web en Azure App Service mediante Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
