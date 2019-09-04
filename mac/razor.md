---
title: Razor
description: Información sobre la compatibilidad de razor en aplicaciones principales de asp.net en Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: a66a31d2c63fcb0e2adc4554c49a76c727f9a288
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107925"
---
# <a name="razor"></a>Razor

Visual Studio para Mac ofrece compatibilidad con la edición de Razor, lo que incluye IntelliSense y el resaltado de sintaxis en archivos *.cshtml*.

![Edición de Razor en Visual Studio para Mac](media/razor-editor.png)

Esta guía proporciona una introducción a la creación de su primera aplicación web de Razor. Para profundizar en ello, consulte la información sobre [Razor Pages en la documentación de .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Creación de un nuevo proyecto de Razor

* En la pantalla de bienvenida, seleccione **Nuevo** para crear un proyecto nuevo:

![Nuevo proyecto de Visual Studio para Mac](media/razor-new.png)

* En el cuadro de diálogo Nuevo proyecto, vaya a **.NET Core** > **Aplicación** > **Aplicación web** y seleccione el botón **Siguiente**:

![Plantilla de proyecto de Razor](media/razor-new-project1.png)

* Seleccione el marco de destino de .NET Core necesario (se recomienda 2.2 o superior) y seleccione **Siguiente**.  Elija un nombre para el proyecto y, de ser necesario, agregue la compatibilidad con GIT. Seleccione **Crear** para crear el proyecto.

![Nombre del proyecto de Razor](media/razor-new-project2.png)

Visual Studio para Mac abrirá el proyecto en el diseño de código.

* Ejecute el proyecto sin depurarlo mediante **Cmd-Opt-F5**.

Visual Studio iniciará [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) e iniciará un explorador para `https://localhost:5001` y mostrará su primera aplicación web de Razor:

![Aplicación web de Razor en Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomía de los proyectos

Las aplicaciones web de Razor constan de los siguientes componentes:

### <a name="pages-folder"></a>Carpeta Pages

La carpeta Pages del proyecto es donde se pueden encontrar las páginas web, junto con el código subyacente para cada una de ellas:
* Un archivo * *.cshtml* para el marcado HTML y la sintaxis Razor.
* Un archivo * *. cshtml.cs* para el código subyacente de C# para controlar los eventos de la página.

Los archivos auxiliares tienen nombres que comienzan con un carácter de subrayado. Por ejemplo, el archivo _Layout.cshtml configura los elementos de la interfaz de usuario comunes a todas las páginas. Este archivo configura el menú de navegación de la parte superior de la página y el aviso de copyright de la parte inferior de la página. Para obtener más información, consulte [Diseño en ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Configuración de inicio

El archivo *launchSettings.json* contiene la configuración de IIS, la dirección URL de la aplicación y otros parámetros relacionados.

### <a name="app-settings"></a>Configuración de la aplicación

El archivo *appSettings,json* contiene los datos de configuración, como las cadenas de conexión.

Para más información sobre la configuración, consulte la [guía de configuración en ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Carpeta wwwroot

Contiene los archivos estáticos, como los archivos HTML, los archivos de JavaScript y los archivos CSS. Para obtener más información, vea [Archivos estáticos en ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Contiene el punto de entrada del programa. Para obtener más información, consulte [Host web de ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Contiene código que configura el comportamiento de la aplicación, como, por ejemplo, si se requiere consentimiento para las cookies. Para obtener más información, vea [Inicio de la aplicación en ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Vea también

Para obtener información más completa sobre la creación de aplicaciones web de Razor, consulte [Introducción a Razor Pages en ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
