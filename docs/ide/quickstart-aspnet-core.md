---
title: Creación de una aplicación web ASP.NET Core en C#
description: Obtenga información sobre cómo crear una aplicación web simple Hola mundo en Visual Studio con C# y ASP.NET Core, paso a paso.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1873c11d8f2e6243a0dc0f867e579f1927cd1607
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579963"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Inicio rápido: uso de Visual Studio para crear su primera aplicación web ASP.NET Core

En esta introducción de entre cinco y diez minutos sobre el uso de Visual Studio, se crea una aplicación web sencilla "Hello World" mediante una plantilla de proyecto de ASP.NET y el lenguaje de programación C#.

## <a name="before-you-begin"></a>Antes de empezar

### <a name="install-visual-studio"></a>Instalación de Visual Studio

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Elija su tema (opcional)

En esta guía de inicio rápido se incluyen capturas de pantalla que utilizan el tema oscuro. Si no está usando el tema oscuro pero le gustaría hacerlo, vea la página [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](quickstart-personalize-the-ide.md) para obtener información sobre cómo hacerlo.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación web ASP.NET Core. En el tipo de proyecto se incluyen todos los archivos de plantilla para crear una aplicación web, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y luego elija **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core**. <br/><br/>Luego nombre al archivo `HelloWorld` y haga clic en **Aceptar**.

   ![Creación de un proyecto de aplicación web ASP.NET Core para C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

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

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione **ASP.NET Core 2.1** en el menú desplegable situado en la parte superior. Después, elija **Aplicación web** y luego haga clic en **Aceptar**.

   ![Cuadro de diálogo Nueva aplicación web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Si no ve **ASP.NET Core 2.1**, asegúrese de que se está ejecutando la versión más reciente de Visual Studio. Para obtener más información sobre cómo actualizar la instalación, vea la página [Actualización de Visual Studio a la versión más reciente](../install/update-visual-studio.md).

Poco después, Visual Studio abre el archivo de proyecto.

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *ASP.NET*. Seguidamente, elija **C#** en la lista de lenguajes y luego, **Windows** en la lista de plataformas.

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación web ASP.NET Core** y, luego, **Siguiente**.

   ![Seleccionar la plantilla C# para Aplicación web ASP.NET Core](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación web ASP.NET Core**, puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?**, elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo de ASP.NET y web**.
   >
   > ![Carga de trabajo Aplicación web ASP.NET Core en el instalador de Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *HelloWorld* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ![En la ventana "Configurar el nuevo proyecto", asigne al proyecto el nombre "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. En la ventana **Crear una aplicación web ASP.NET Core**, compruebe que **ASP.NET Core 3.0** aparece en el menú desplegable de la parte superior. Luego, elija **Aplicación Web**, que incluye Razor Pages de ejemplo. Seguidamente, elija **Crear**.

   ![Ventana "Crear una aplicación web ASP.NET Core"](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio se abre en el nuevo proyecto.

::: moniker-end

## <a name="create-and-run-the-app"></a>Crear y ejecutar la aplicación

::: moniker range="vs-2017"

1. En el **Explorador de soluciones**, expanda la carpeta **Páginas** y después elija **About.cshtml**.

   ![Selección del archivo About.cshtml desde el Explorador de soluciones](../ide/media/csharp-aspnet-about-page-html-file.png)

   Este archivo corresponde a una página denominada **Acerca de** en la aplicación web y que se ejecuta en un explorador web.

   ![Página Acerca de de la aplicación web](../ide/media/csharp-aspnet-about-page.png)

   En el editor, verá el código HTML para el área "información adicional" de la página **Acerca de**.

   ![El código HTML para el área de información adicional en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Cambie el texto "información adicional" para que rece "**Hello World!**".

   ![Cambio del código HTML predeterminado para el área de información adicional en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. En el **Explorador de soluciones**, expanda **About.cshtml** y luego elija **About.cshtml.cs**. (Este archivo también se corresponde con la página **Acerca de** en un explorador web).

   ![Selección del archivo About.cshtml desde el Explorador de soluciones](../ide/media/csharp-aspnet-about-page-code-file.png)

   En el editor, verá el código de C# que incluye texto para el área "Descripción de la aplicación" de la página **Acerca de**.

   ![El código de C# para el área de descripción de la aplicación en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Cambie el texto del mensaje "descripción de la aplicación" para que rece "**¿Cuál es mi mensaje?**".

   ![Cambio del texto del mensaje predeterminado para el área de descripción de la aplicación en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Seleccione **IIS Express** o presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

   ![Haga clic en el botón IIS Express de Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Si recibe un mensaje de error que dice **No se puede conectar al servidor web "IIS Express"** o un mensaje de error que menciona un certificado SSL, cierre Visual Studio. Después, abra Visual Studio mediante la opción **Ejecutar como administrador** del menú contextual. A continuación, vuelva a ejecutar la aplicación.

1. En el explorador web, compruebe que la página **Acerca de** incluye el texto actualizado.

   ![Visualización de la página Acerca de actualizada que incluye los cambios realizados](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Cierre el explorador web.

### <a name="review-your-work"></a>Revisión del trabajo

Vea la animación siguiente para comprobar el trabajo que ha realizado en la sección anterior.

  ![Vista del archivo .gif animado en el que se muestra cómo crear y ejecutar una sencilla aplicación web ASP.NET Core de C# en Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE (entorno de desarrollo integrado) de Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. En el **Explorador de soluciones**, expanda la carpeta **Páginas** y, después, elija **Index.cshtml**.

   ![Selección del archivo Index.cshtml del Explorador de soluciones](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Este archivo corresponde a una página denominada **Inicio** en la aplicación web y que se ejecuta en un explorador web.

   ![Página Acerca de de la aplicación web](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   En el editor, verá código HTML para el texto que se muestra en la página **Inicio**.

   ![Código HTML del archivo Index.cshtml para la página Inicio en el editor de Visual Studio.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Cambie el texto "Le damos la bienvenida" por "**Hola mundo**".

   ![En el editor de Visual Studio, cambie el código HTML predeterminado "Le damos la bienvenida" por "Hola mundo".](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Seleccione **IIS Express** o presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

   ![Haga clic en el botón IIS Express de Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Si recibe un mensaje de error que dice **No se puede conectar al servidor web "IIS Express"** o un mensaje de error que menciona un certificado SSL, cierre Visual Studio. Después, abra Visual Studio mediante la opción **Ejecutar como administrador** del menú contextual. A continuación, vuelva a ejecutar la aplicación.

1. En el explorador web, compruebe que la página **Inicio** incluya el texto actualizado.

   ![Visualización de la página Inicio actualizada con los cambios realizados](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Cierre el explorador web.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

Para más información, continúe con el siguiente tutorial:

> [!div class="nextstepaction"]
> [Introducción a C# y ASP.NET Core en Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Consulte también

[Publicar una aplicación web en Azure App Service mediante Visual Studio](../deployment/quickstart-deploy-to-azure.md)
