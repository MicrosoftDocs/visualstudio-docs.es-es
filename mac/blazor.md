---
title: Creación de aplicaciones web de Blazor
description: Proporciona información sobre la compatibilidad de Blazor en aplicaciones de ASP.NET Core en Visual Studio para Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: d04441e3c5f2eff3a63f7aca35ccf7ecac90fb44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737304"
---
# <a name="create-blazor-web-apps"></a>Creación de aplicaciones web de Blazor

Esta guía proporciona una introducción a la creación de su primera aplicación web de Blazor. Para obtener instrucciones más detalladas, consulte [Introducción a Blazor en ASP.NET Core](/aspnet/core/blazor/index).

Visual Studio para Mac (a partir de la versión 8.4) incluye compatibilidad con el desarrollo y la publicación de aplicaciones de servidor Blazor en ASP.NET Core. Blazor es un marco para compilar la interfaz de usuario web del lado cliente interactiva con .NET, que ofrece las siguientes ventajas a los desarrolladores web:

* Escribe el código en C# en lugar de JavaScript.
* Aprovechamiento del ecosistema y las bibliotecas .NET existentes.
* Uso compartido de la lógica de aplicación en el servidor y el cliente.
* Beneficios de rendimiento, confiabilidad y seguridad de .NET.
* Mantenga la productividad con Visual Studio en PC, Linux y macOS.
* Compile sobre un conjunto común de lenguajes, marcos y herramientas que son estables, completos y fáciles de usar.

## <a name="creating-a-new-blazor-project"></a>Creación de un nuevo proyecto de Blazor

1. En la **ventana de inicio**, seleccione **Nuevo** para crear un nuevo proyecto:

   ![Ventana de inicio de Visual Studio para Mac con la selección de Nuevo resaltada](media/blazor-new-project.png)
1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **.NET Core** > **Aplicación** > **Aplicación de servidor Blazor** y seleccione **Siguiente**: ![Cuadro de diálogo Elija una plantilla para el nuevo proyecto con la plantilla Aplicación de servidor Blazor seleccionada](media/blazor-project-template.png)

1. Seleccione .NET Core 3.1 como marco de destino y, a continuación, seleccione **Siguiente**. 
   ![Cuadro de diálogo Configure your new Blazor Server App (Configure su nueva aplicación de servidor Blazor) mostrado con .NET Core 3.1 seleccionado como marco de destino](media/blazor-select-target-framework.png)

1. Elija un nombre para el proyecto y, si lo desea, agregue la compatibilidad con GIT. Seleccione **Crear** para crear el proyecto.
   ![Cuadro de diálogo Configure your new Blazor Server App (Configure su nueva aplicación de servidor Blazor) mostrado mientras se escribe el nombre del proyecto](media/blazor-name-project.png)

   Visual Studio para Mac abrirá el proyecto en la ventana de diseño de código.
1. Seleccione **Ejecutar** > **Iniciar sin depurar** para ejecutar la aplicación.

   Visual Studio inicia [Kestrel](/aspnet/core/fundamentals/servers/kestrel), abre un explorador en `https://localhost:5001` y muestra su aplicación web de Blazor.

   ![Aplicación web de Blazor en Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Compatibilidad con Blazor en Visual Studio para Mac

Visual Studio para Mac (a partir de la versión 8.4) incluye nuevas características que le ayudarán a crear nuevos proyectos de servidor Blazor. Además, le proporciona el soporte técnico Standard que cabría esperar, como la compilación, ejecución y depuración de proyectos de Blazor. 

En el tutorial anterior, vimos cómo le ayuda la plantilla de proyecto Aplicación de servidor Blazor a crear un nuevo proyecto de aplicación de servidor Blazor. Echemos un vistazo a algunas de las características adicionales de Visual Studio para Mac para admitir el desarrollo de proyectos de servidor Blazor.

### <a name="editor-support-for-razor-files"></a>Compatibilidad del editor con archivos *.razor*
Visual Studio para Mac incluye compatibilidad con la edición de archivos .razor (la mayoría de los archivos que usará al crear aplicaciones Blazor). La versión de Windows y la de Mac del entorno de desarrollo integrado comparten el mismo editor de archivos .razor. Verá la compatibilidad total de uso de colores y finalización con sus archivos .razor, incluidas las finalizaciones de los componentes Razor declarados en el proyecto.

![Ventana del editor de Visual Studio para Mac en la que se muestra IntelliSense para Blazor.](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publicación de aplicaciones Blazor en Azure App Service
También puede publicar aplicaciones Blazor directamente en Azure App Service. Si no tiene una cuenta de Azure para ejecutar su aplicación Blazor en Azure, siempre puede [suscribirse a una cuenta gratuita aquí](https://azure.microsoft.com/free) que también incluya 12 meses de servicios populares gratuitos, 200 USD de créditos de Azure gratuitos y más de 25 servicios gratuitos para siempre.

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

### <a name="startupcs"></a>Startup.cs

Este archivo contiene código que configura el comportamiento de la aplicación, como, por ejemplo, si la aplicación requiere consentimiento para las cookies. Para obtener más información, vea [Inicio de la aplicación en ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Resumen
En este tutorial, ha visto cómo crea una nueva aplicación de servidor Blazor en Visual Studio para Mac y ha obtenido información sobre algunas de las características que ofrece Visual Studio para Mac para ayudarle a crear aplicaciones Blazor.

## <a name="see-also"></a>Vea también

Para obtener información más completa sobre la creación de aplicaciones web de Blazor, consulte [Introducción a Blazor en ASP.NET Core](/aspnet/core/blazor/index).
