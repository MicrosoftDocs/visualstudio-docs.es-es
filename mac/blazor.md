---
title: Creación de aplicaciones web de Blazor
description: Proporciona información sobre la compatibilidad de Blazor en aplicaciones de ASP.NET Core en Visual Studio para Mac.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 0dcc254366e0d652ab7a8442a4d0c526fd72c403
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402546"
---
# <a name="create-no-locblazor-web-apps"></a>Creación de aplicaciones web de Blazor

Esta guía proporciona una introducción a la creación de su primera aplicación web de Blazor. Para obtener instrucciones más detalladas, vea [Introducción a ASP.NET Core Blazor](/aspnet/core/blazor/index).

Blazor en ASP.NET Core admite dos opciones de hospedaje diferentes: Blazor WebAssembly (WASM) o Blazor Server. Visual Studio para Mac admite ambos modelos de hospedaje. Visual Studio para Mac 8.4+ admite Blazor Server, mientras que Visual Studio para Mac 8.6+ admite ambas opciones. Para más información sobre los modelos de hospedaje de Blazor, vea [Modelos de hospedaje Blazor en ASP.NET Core](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). La compatibilidad con la depuración de proyectos de Blazor WebAssembly en Visual Studio para Mac está disponible en la versión preliminar de la versión 8.8 (disponible a través del canal de actualización de la versión preliminar en el menú **Visual Studio > Buscar actualizaciones...** ).

¿Qué es Blazor? Blazor es un marco de compilación de la interfaz de usuario web del lado cliente interactiva con .NET que ofrece las siguientes ventajas a los desarrolladores web:

* Escribe el código en C# en lugar de JavaScript.
* Aprovechamiento del ecosistema y las bibliotecas .NET existentes.
* Uso compartido de la lógica de aplicación en el servidor y el cliente.
* Beneficios de rendimiento, confiabilidad y seguridad de .NET.
* Mantenga la productividad con Visual Studio en PC, Linux y macOS.
* Compile sobre un conjunto común de lenguajes, marcos y herramientas que son estables, completos y fáciles de usar.

## <a name="create-a-new-no-locblazor-webassembly-project"></a>Creación de un proyecto de Blazor WebAssembly
1. En la **ventana de inicio**, seleccione **Nuevo** para crear un nuevo proyecto:

   ![Ventana de inicio de Visual Studio para Mac con la selección de Nuevo resaltada](media/blazor-new-project.png)

1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **.NET Core** > **Aplicación** > **Aplicación Blazor WebAssembly** y seleccione **Siguiente**: ![Cuadro de diálogo Elija una plantilla para el nuevo proyecto con la plantilla Aplicación de servidor Blazor seleccionada](media/blazor-wasm-project-template.png)

1. Seleccione .NET Core 3.1 como marco de destino y, a continuación, seleccione **Siguiente**. 
   ![Cuadro de diálogo Configure su nueva aplicación Blazor WebAssembly abierto con .NET Core 3.1 seleccionado como plataforma de destino](media/blazor-wasm-select-target-framework.png)

1. Elija un nombre para el proyecto y, si lo desea, agregue la compatibilidad con GIT. Seleccione **Crear** para crear el proyecto.
    ![Cuadro de diálogo Configure su nueva aplicación Blazor WebAssembly abierto mientras se escribe el nombre del proyecto](media/blazor-wasm-name-project.png)

   Visual Studio para Mac abrirá el proyecto en la ventana de diseño de código.

1. Seleccione **Ejecutar** > **Iniciar sin depurar** para ejecutar la aplicación.

   Visual Studio inicia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), abre un explorador en `https://localhost:5001` y muestra la aplicación web de Blazor.

   ![Aplicación web Blazor en Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-no-locblazor-server-project"></a>Creación de un proyecto de Blazor Server

1. En la **ventana de inicio**, seleccione **Nuevo** para crear un nuevo proyecto:

   ![Ventana de inicio de Visual Studio para Mac con la selección de Nuevo resaltada](media/blazor-new-project.png)
1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **.NET Core** > **Aplicación** > **Aplicación de servidor Blazor** y seleccione **Siguiente**: ![Cuadro de diálogo Elija una plantilla para el nuevo proyecto con la plantilla Aplicación de servidor Blazor seleccionada](media/blazor-project-template.png)

1. Seleccione .NET Core 3.1 como marco de destino y, a continuación, seleccione **Siguiente**. 
   ![Cuadro de diálogo Configure su nueva aplicación de servidor Blazor abierto con .NET Core 3.1 seleccionado como marco de destino](media/blazor-select-target-framework.png)

1. Elija un nombre para el proyecto y, si lo desea, agregue la compatibilidad con GIT. Seleccione **Crear** para crear el proyecto.
   ![Cuadro de diálogo Configure su nueva aplicación de servidor Blazor abierto mientras se escribe el nombre del proyecto](media/blazor-name-project.png)

   Visual Studio para Mac abrirá el proyecto en la ventana de diseño de código.
1. Seleccione **Ejecutar** > **Iniciar sin depurar** para ejecutar la aplicación.

   Visual Studio inicia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), abre un explorador en `https://localhost:5001` y muestra la aplicación web de Blazor.

   ![Aplicación web Blazor en Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="no-locblazor-support-in-visual-studio-for-mac"></a>Compatibilidad con Blazor en Visual Studio para Mac

Visual Studio para Mac (a partir de la versión 8.4) incluye nuevas características que le ayudarán a crear proyectos de servidor Blazor. Además, proporciona el soporte técnico Standard que cabría esperar, como la compilación, ejecución y depuración de proyectos de Blazor. En Visual Studio para Mac 8.6, se agregó compatibilidad con la creación, compilación y ejecución de proyectos de Blazor WebAssembly.

En el tutorial anterior, vimos cómo la plantilla de proyecto de aplicación Blazor Server sirve para crear un proyecto de aplicación Blazor Server o de aplicación Blazor WebAssembly. Veamos algunas de las características adicionales de Visual Studio para Mac que admiten el desarrollo de proyectos de Blazor.

### <a name="editor-support-for-razor-files"></a>Compatibilidad del editor con archivos *.razor*
Visual Studio para Mac incluye compatibilidad con la edición de archivos .razor (la mayoría de los archivos que usará al crear aplicaciones Blazor). Visual Studio para Mac proporciona compatibilidad total del uso de colores y finalización con sus archivos .razor, incluidas las finalizaciones de los componentes Razor declarados en el proyecto.

![Ventana del editor de Visual Studio para Mac en la que se muestra IntelliSense para Blazor](media/blazor-intellisense.png)

### <a name="publishing-no-locblazor-applications-to-azure-app-service"></a>Publicación de aplicaciones Blazor en Azure App Service
Las aplicaciones Blazor también se pueden publicar directamente en Azure App Service. Si no tiene una cuenta de Azure para ejecutar su aplicación Blazor en Azure, siempre puede [suscribirse a una cuenta gratuita aquí](https://azure.microsoft.com/free) que también incluya 12 meses de servicios populares gratuitos, 200 USD de créditos de Azure gratuitos y más de 25 servicios gratuitos para siempre.

![Visual Studio para Mac que muestra la experiencia de publicación de Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomía de los proyectos

Las aplicaciones web de Blazor incluyen algunos directorios y archivos de forma predeterminada. Como está empezando, estos son los principales con los que deberá estar familiarizado:

### <a name="pages-folder"></a>Carpeta Pages

Esta carpeta contiene las páginas web de un proyecto, que usan una extensión de archivo *.razor*.

### <a name="shared-folder"></a>Carpeta Shared

Esta carpeta incluye componentes compartidos, que también usan la extensión *.razor*. Verá que esta incluye *MainLayout.razor*, que se usa para definir el diseño común en toda la aplicación. También incluye el componente *NavMenu.razor* compartido, que se usa en todas las páginas. Si va a crear componentes reutilizables, irán en la carpeta **Shared**.

### <a name="app-settings"></a>Configuración de la aplicación

El archivo *appSettings.json* contiene datos de configuración, como las cadenas de conexión.

Para obtener más información sobre la configuración, consulte la [guía de configuración en ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Carpeta wwwroot

Esta carpeta contiene archivos estáticos, como los archivos HTML, JavaScript y CSS. Para obtener más información, vea [Archivos estáticos en ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Este archivo contiene el punto de entrada del programa. Para obtener más información, consulte [Host web de ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="no-locblazor-server-app-specific-files"></a>Archivos específicos de la aplicación Blazor Server
#### <a name="app-settings"></a>Configuración de la aplicación

El archivo *appSettings.json* contiene datos de configuración, como las cadenas de conexión.

Para obtener más información sobre la configuración, consulte la [guía de configuración en ASP.NET](/aspnet/core/fundamentals/configuration/index).

#### <a name="startupcs"></a>Startup.cs

Este archivo contiene código que configura el comportamiento de la aplicación, como, por ejemplo, si la aplicación requiere consentimiento para las cookies. Para obtener más información, vea [Inicio de la aplicación en ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Resumen
En este tutorial, ha visto cómo crear una aplicación Blazor Server o una aplicación Blazor WebAssembly en Visual Studio para Mac y ha obtenido información sobre algunas de las características que ofrece Visual Studio para Mac para ayudarle a crear aplicaciones Blazor.

## <a name="see-also"></a>Vea también

Para obtener información más exhaustiva sobre cómo crear aplicaciones web de Blazor, vea [Introducción a Blazor en ASP.NET CoreBlazor](/aspnet/core/blazor/index).
