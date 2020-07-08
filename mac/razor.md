---
title: Creación de aplicaciones web de Razor
description: Proporciona información sobre la compatibilidad de Razor en aplicaciones de ASP.NET Core en Visual Studio para Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 008052c9b78f93b84e650329cd7ebaf6200d21f1
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950527"
---
# <a name="create-razor-web-apps"></a>Creación de aplicaciones web de Razor

Esta guía proporciona una introducción a la creación de su primera aplicación web de Razor. Para obtener instrucciones más detalladas, vea [Introducción a Razor Pages en ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio para Mac ofrece compatibilidad con la edición de Razor, lo que incluye IntelliSense y el resaltado de sintaxis en archivos *.cshtml*. Una novedad de Visual Studio 2019 para Mac 8.3+ consiste en que IntelliSense es compatible con el contexto dentro de un archivo Razor, de modo que recibe sugerencias de IntelliSense que coinciden con el lenguaje que está editando actualmente dentro de un documento.

![Edición de Razor en Visual Studio para Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Creación de un nuevo proyecto de Razor

1. En la pantalla de bienvenida, seleccione **Nuevo** para crear un proyecto:

   ![Nuevo proyecto de Visual Studio para Mac](media/razor-new.png)
1. En el cuadro de diálogo **Nuevo proyecto**, vaya a **.NET Core** > **Aplicación** > **Aplicación web** y seleccione **Siguiente**:

   ![Plantilla de proyecto de Razor](media/razor-new-project1.png)
1. Seleccione la plataforma de destino de .NET Core (se recomienda la versión 2.2 o posterior) y, luego, haga clic en **Siguiente**. Elija un nombre para el proyecto y, si es necesario, agregue compatibilidad con GIT. Seleccione **Crear** para crear el proyecto.

   ![Nombre del proyecto de Razor](media/razor-new-project2.png)

   Visual Studio para Mac abrirá el proyecto en la ventana de diseño de código.
1. Ejecute el proyecto sin depurarlo mediante **Comando+Opción+F5**.

   Visual Studio inicia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), abre un explorador en `https://localhost:5001` y muestra su primera aplicación web de Razor.

   ![Aplicación web de Razor en Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomía de los proyectos

Las aplicaciones web de Razor incluyen los componentes siguientes.

### <a name="pages-folder"></a>Carpeta Pages

Esta carpeta contiene las páginas web de un proyecto, junto con el código subyacente de cada una:
   - Un archivo *\*.cshtml* para el marcado HTML y la sintaxis Razor.
   - Un archivo *\*.cshtml.cs* para el código subyacente de C# para controlar los eventos de la página.

Los archivos auxiliares tienen nombres que comienzan con un carácter de subrayado. Por ejemplo, el archivo _Layout.cshtml configura los elementos de la interfaz de usuario comunes a todas las páginas. Este archivo configura el menú de navegación de la parte superior de la página y el aviso de copyright de la parte inferior. Para obtener más información, consulte [Diseño en ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Configuración de inicio

El archivo *launchSettings.json* contiene la configuración de IIS, la dirección URL de la aplicación y otros parámetros relacionados.

### <a name="app-settings"></a>Configuración de la aplicación

El archivo *appSettings.json* contiene datos de configuración, como las cadenas de conexión.

Para obtener más información sobre la configuración, consulte la [guía de configuración en ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Carpeta wwwroot

Esta carpeta contiene archivos estáticos, como los archivos HTML, JavaScript y CSS. Para obtener más información, vea [Archivos estáticos en ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Este archivo contiene el punto de entrada del programa. Para obtener más información, consulte [Host web de ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Este archivo contiene código que configura el comportamiento de la aplicación, como, por ejemplo, si la aplicación requiere consentimiento para las cookies. Para obtener más información, vea [Inicio de la aplicación en ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Vea también

Para obtener información más completa sobre la creación de aplicaciones web de Razor, consulte [Introducción a Razor Pages en ASP.NET Core](/aspnet/core/razor-pages/index).
