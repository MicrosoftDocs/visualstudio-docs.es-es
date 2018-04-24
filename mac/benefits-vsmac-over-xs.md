---
title: Ventajas de Visual Studio para Mac frente a Xamarin Studio
description: ''
ms.topic: overview
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.openlocfilehash: db4a328bceb79c1b99fdea95da89cc6cc7451523
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Ventajas de Visual Studio para Mac frente a Xamarin Studio 

Visual Studio para Mac ha reemplazado a Xamarin Studio como IDE con todas las características en Mac. Proporciona características que permiten desarrollar servicios y aplicaciones web, aplicaciones de escritorio y móviles multiplataforma y juegos. Además, facilita la integración con Azure, tanto para la publicación en Azure como para la creación de Azure Functions. Tiene todo lo que esperaría de un IDE moderno, incluido un editor de código fuente completo, un depurador eficaz, un área de trabajo personalizable, integración con GIT y un sistema de extensiones mejorado, todo ello diseñado de forma nativa para Mac. 

Otras características incluyen: 

* IntelliSense de C# basado en Roslyn, refactorización, analizadores y correcciones de código. 
* Administración de paquetes basada en NuGet. 
* Formato de proyectos compatible de Visual Studio. 
* Motor de compilación MSBuild. 
* Pruebas unitarias integradas. 
* Compatibilidad estándar con F#. 

Las ventajas que en esta guía están marcadas como **versión preliminar** solo están disponibles en el [canal alfa](https://docs.microsoft.com/visualstudio/mac/update#Changing_the_Updater_channel). 

## <a name="language-support"></a>Compatibilidad con lenguajes 

Puede escribir código de C# 7 en el equipo Mac únicamente en Visual Studio para Mac.

## <a name="net-core"></a>Núcleo de .NET  

[.NET Core](https://www.microsoft.com/net/core#macos) es una plataforma para crear aplicaciones que se ejecutan en Windows, Linux y Mac. Visual Studio para Mac tiene compatibilidad para cargar, crear, ejecutar y depurar proyectos de .NET Core. 

.NET Core se instala con Visual Studio para Mac y está listo para su uso.

La compatibilidad con .NET Core incluye: 

* IntelliSense de C# y F#. 
* Plantillas de proyecto de .NET Core para aplicaciones web, de biblioteca y de consola. 
* Compatibilidad de depuración total, incluidos puntos de interrupción, pila de llamadas, ventana de inspección, etc. 
* Referencias a paquetes NuGet y restauración basada en MSBuild. 
* Compatibilidad con pruebas unitarias integradas para la ejecución y la depuración de pruebas con la plataforma de pruebas de Visual Studio que se incluye con el SDK de .NET Core. 
* Migración desde el formato antiguo project.json. 
* Compatibilidad con proyectos de .NET Standard.

## <a name="web-development"></a>Desarrollo web  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio para Mac incluye de fábrica plantillas de ASP.NET Core para proyectos de Web API y MVC.
 
![IntelliSense para HTML](media/benefits-vsmac-over-xs-image3.png)

Visual Studio para Mac también agrega nueva compatibilidad con las herramientas web para archivos HTML, CSS y JSON. 

### <a name="html"></a>HTML 

* Nueva plantilla HTML. 
* Sangría inteligente y formato mejorados. 
* Coloración mejorada. 
* IntelliSense mejorado. 
* Plegado de código (debe habilitarse). 
* Comando Unminify. 
* Plantillas de código mejoradas (fragmentos de código). 
* Rodear la selección con `<div>`. 
* Con Opción+flecha arriba o flecha abajo se sube o baja el texto seleccionado. 

### <a name="css"></a>CSS 

* Sangría inteligente y formato mejorados. 
* Coloración mejorada. 
* IntelliSense mejorado. 
* Plegado de código. 
* Muchas plantillas de código (fragmentos de código). 
* Con Opción+flecha arriba o flecha abajo se sube o baja el texto seleccionado. 

### <a name="json"></a>JSON 
* Selector de esquema con acceso a schemastore.org. 
* Validación desde esquema. 
* IntelliSense desde esquema. 
* Sangría inteligente y formato mejorados. 
* Coloración mejorada. 
* Comentar y quitar marca de comentario. 
* Inyección de comillas y coincidencia de llaves. 
* Con Opción+flecha arriba o flecha abajo se sube o baja el texto seleccionado. 

## <a name="publishing-to-azure"></a>Publicación en Azure

Con Visual Studio para Mac, es posible publicar servicios y aplicaciones web de ASP.NET Core en Azure App Service. 

![Publicar en Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Azure Functions (**versión preliminar**)

Azure Functions es una solución para ejecutar fácilmente pequeños fragmentos de código, o funciones, en la nube. Visual Studio para Mac permite codificar y depurar localmente Azure Functions. Para comenzar, busque Azure Functions en Nube, en el cuadro de diálogo Nuevo proyecto. 

### <a name="docker-support-preview"></a>Compatibilidad con Docker (**versión preliminar**)

Ahora puede publicar aplicaciones de ASP.NET Core en contenedores de Docker y ejecutarlas desde Azure App Service. 

Para habilitar la compatibilidad con Docker en el proyecto, haga clic con el botón derecho en la aplicación web de ASP.NET Core y seleccione **Agregar > Add Docker Support** (Agregar compatibilidad con Docker). 

Para publicar la aplicación web en un contenedor de Docker, use el flujo de trabajo **Publicar > Publicar en Azure** que se ha introducido en Visual Studio para Mac.

## <a name="source-editor-improvements"></a>Mejoras en el editor de código fuente 

Además de IntelliSense de C# basado en Roslyn, refactorización, analizadores y correcciones de código, el editor de código fuente de Visual Studio para Mac proporciona las siguientes mejoras con respecto a Xamarin Studio: 

### <a name="language-bundles"></a>Paquetes de idioma 

Visual Studio para Mac tiene compatibilidad con los paquetes de idioma TextMate (`.tmBundle`) y Sublime 3 (`.sublime`), que se pueden usar para agregar: 

* Temas de color del editor 
* Fragmentos de código 
* Gramáticas para nuevos idiomas, que habilitan el resaltado e IntelliSense básico 

Puede agregar estos paquetes en **Preferencias > Editor de texto > Paquetes de idioma**. 

### <a name="color-theme-support"></a>Compatibilidad con el tema de color 

Se admiten los siguientes formatos de tema de color en Visual Studio para Mac: 

* Visual Studio (`.vssettings`) 
* Xamarin Studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) es una herramienta de creación de juegos que puede usar para crear juegos 2D y 3D multiplataforma de alta calidad para todas las plataformas principales: dispositivos móviles, escritorios, consolas, dispositivos de realidad aumentada y realidad virtual, e incluso la Web. 

A partir de Unity 5.6.1, puede usar Visual Studio para Mac para escribir y depurar juegos de Unity. Para empezar a trabajar, establezca Visual Studio como editor de scripts de Unity 5.6.1. 

Las herramientas de Unity incluyen: 

* Compatibilidad con scripts escritos en C#. 
* Panel de solución de Unity. 
* Depuración con un solo clic del editor de Unity. 
* IntelliSense para mensajes de Unity. 
* Colores de código para sombreadores de Unity. 
* Acceso a la documentación de Unity. 

## <a name="xamarin"></a>Xamarin 

Aunque las características multiplataforma de Xamarin siempre han sido un elemento preferente de Xamarin Studio, algunas características de Xamarin solo están disponibles en Visual Studio para Mac. 

### <a name="android"></a>Android 

* [Android SDK manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* Android O solo se admitirá en Visual Studio para Mac, no en Xamarin Studio. 

### <a name="ios-and-mac"></a>iOS y Mac 

* [Actualizaciones del flujo de trabajo de firma de iOS](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * Crear identidades de firma e instalarlas en la cadena de claves local. 
    * Crear perfiles de aprovisionamiento 
    * Agregar una identidad de firma a un perfil existente
    *  Aprovisionar dispositivos: registrar un dispositivo en el Portal para desarrolladores de Apple y agregarlo a un perfil de aprovisionamiento
* iOS 11, watchOS 4 y tvOS 2 solo se admitirán en Visual Studio para Mac, no en Xamarin Studio. 
* MacOS High Sierra solo se admitirá en Visual Studio para Mac, no en Xamarin Studio. 

### <a name="cross-platform"></a>Multiplataforma 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**versión preliminar**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**versión preliminar**) 
 