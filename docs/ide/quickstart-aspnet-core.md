---
title: Creación de una aplicación web ASP.NET Core en C#
description: Obtenga información sobre cómo crear una aplicación web simple Hola mundo en Visual Studio con C# y ASP.NET Core, paso a paso.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.custom: mvc,seodec18
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 88c0362f05fc6e938d9268faf373aa7bd4e8d9ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839723"
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

En primer lugar, creará un proyecto de aplicación web ASP.NET Core. En el tipo de proyecto se incluyen todos los archivos de plantilla para crear una aplicación web, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y luego elija **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core**. Luego asigne un nombre al archivo `HelloWorld` y elija **Aceptar**.

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

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione **ASP.NET Core 2.0** o posterior en el menú desplegable situado en la parte superior.

   > [!NOTE]
   > Si no ve **ASP.NET Core 2.0** o posterior, asegúrese de que se está ejecutando la versión más reciente de Visual Studio. Para obtener más información sobre cómo actualizar la instalación, vea la página [Actualizar Visual Studio 2017 a la versión más reciente](../install/update-visual-studio.md).

1. Después, elija **Aplicación web** y luego haga clic en **Aceptar**.

   ![Cuadro de diálogo Nueva aplicación web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

Poco después, Visual Studio abre el archivo de proyecto.

## <a name="create-the-app"></a>Creación de la aplicación

1. En el **Explorador de soluciones**, expanda la carpeta **Páginas** y después elija **About.cshtml**.

   ![Selección del archivo About.cshtml desde el Explorador de soluciones](../ide/media/csharp-aspnet-about-page-html-file.png)

   Este archivo corresponde a una página denominada **Acerca de** de la aplicación web.

   ![Página Acerca de de la aplicación web](../ide/media/csharp-aspnet-about-page.png)

   En el editor, verá el código HTML para el área "información adicional" de la página **Acerca de**.

   ![El código HTML para el área de información adicional en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Cambie el texto "información adicional" para que rece "**Hello World!**".

   ![Cambio del código HTML predeterminado para el área de información adicional en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. En el **Explorador de soluciones**, expanda **About.cshtml** y luego elija **About.cshtml.cs**. (Este archivo también se corresponde con la página **Acerca de** de la aplicación web).

   ![Selección del archivo About.cshtml desde el Explorador de soluciones](../ide/media/csharp-aspnet-about-page-code-file.png)

   En el editor, verá el código de C# que incluye texto para el área "Descripción de la aplicación" de la página **Acerca de**.

   ![El código de C# para el área de descripción de la aplicación en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Cambie el texto del mensaje "descripción de la aplicación" para que rece "**¿Cuál es mi mensaje?**".

   ![Cambio del texto del mensaje predeterminado para el área de descripción de la aplicación en el editor de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>Ejecutar la aplicación

1. Presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

   > [!NOTE]
   > Si recibe un mensaje de error que dice **No se puede conectar al servidor web "IIS Express"** o un mensaje de error que menciona un certificado SSL, cierre Visual Studio. Después, abra Visual Studio mediante la opción **Ejecutar como administrador** en el menú contextual. A continuación, vuelva a ejecutar la aplicación.

1. En la parte superior de la página web, elija **Acerca de**.

   ![Selección de Acerca de en la página web](../ide/media/csharp-aspnet-home-page-about.png)

1. Vea el texto actualizado que agregó a la página **Acerca de**.

   ![Visualización de la página Acerca de actualizada que incluye el texto agregado](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Cierre el explorador web.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE (entorno de desarrollo integrado) de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Introducción a C# y ASP.NET Core en Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Vea también

[Publicar una aplicación web en Azure App Service mediante Visual Studio](../deployment/quickstart-deploy-to-azure.md)
