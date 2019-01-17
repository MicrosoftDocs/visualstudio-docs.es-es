---
title: Presentación de Visual Studio para Mac
description: En este artículo se presentan las características de Visual Studio para Mac.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 59e349b1d784e68c3ef6842834d875ce5d1917bb
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315558"
---
# <a name="visual-studio-for-mac"></a>Visual Studio para Mac

Visual Studio para Mac es un IDE moderno y sofisticado con numerosas características para crear aplicaciones móviles, web y de escritorio. Admite los siguientes tipos de desarrollo:

- Móvil con .NET: Android, iOS, tvOS, watchOS
- Aplicaciones de escritorio de Mac
- Aplicaciones .NET Core
- Aplicaciones web ASP.NET Core
- Juegos multiplataforma de Unity

Incluye características como un editor enriquecido, depuración, integración de plataforma nativa con iOS, Mac y Android, y control de código fuente integrado.

En este artículo se analizan varias secciones de Visual Studio para Mac y se presentan las características que lo convierten en una herramienta eficaz para crear aplicaciones multiplataforma.

> [!TIP]
> La **versión preliminar de Visual Studio 2019 para Mac** ya está disponible con fines de pruebas. Siga estas [instrucciones de instalación](/visualstudio/mac/installation/?view=vsmac-2019) y vea el [Paseo de IDE de 2019](/visualstudio/mac/ide-tour/?view=vsmac-2019).

## <a name="installation"></a>Instalación

Siga los pasos de la guía de [instalación](install-preview.md) para descargar e instalar Visual Studio para Mac.

## <a name="language-support"></a>Compatibilidad con lenguajes

Visual Studio para Mac admite el desarrollo en C# y F#, de forma predeterminada.

### <a name="c"></a>C#

C# es el más lenguaje más usado para crear aplicaciones multiplataforma en Visual Studio para Mac. El IDE tiene compatibilidad total con todas las características de C# 7.

### <a name="f"></a>F#

F# es un lenguaje de programación funcional fuertemente tipado diseñado para ejecutarse en .NET. Está disponible como un lenguaje de programación para los usuarios de Visual Studio para Mac en Android, Mac e iOS. Para obtener más información sobre el uso de F# y ver ejemplos creados en este lenguaje, vea las guías de [F#](https://developer.xamarin.com/guides/cross-platform/fsharp/).

## <a name="platform-support"></a>Compatibilidad con la plataforma

## <a name="net-core"></a>Núcleo de .NET

[.NET Core](https://www.microsoft.com/net/core#macos) es una plataforma para crear aplicaciones que se ejecutan en Windows, Linux y Mac. Visual Studio para Mac tiene compatibilidad para cargar, crear, ejecutar y depurar proyectos de .NET Core. 

Para poder ejecutar proyectos de .NET Core es necesario descargar e instalar el SDK de .NET Core.

La compatibilidad con .NET Core incluye:

- IntelliSense de C# y F#.
- Plantillas de proyecto de .NET Core para aplicaciones web, de biblioteca y de consola.
- Compatibilidad de depuración total, incluidos puntos de interrupción, pila de llamadas, ventana de inspección, etc.
- NuGet PackageReferences y restauración basada en MSBuild.
- Compatibilidad con pruebas unitarias integradas para la ejecución y la depuración de pruebas con la plataforma de pruebas de Visual Studio que se incluye con el SDK de .NET Core.
- Migración desde el formato antiguo project.json.

Para empezar, vea el [laboratorio práctico](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started) de aplicaciones web de ASP.NET Core.

## <a name="xamarin-mobile-app-development"></a>Desarrollo de aplicaciones móviles con Xamarin

La compatibilidad de primera clase con [Xamarin](https://developer.xamarin.com/) le permite desarrollar experiencias nativas completas para Android, macOS, iOS, tvOS y watchOS. Las aplicaciones multiplataforma de Xamarin.Forms ayudan a compartir código de interfaz de usuario basado en XAML entre Android, iOS y macOS sin limitar el acceso a la funcionalidad nativa.

Para empezar, vea el [laboratorio práctico](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started) de aplicaciones móviles.

### <a name="android"></a>Android

Visual Studio tiene integrado su propio administrador de Android SDK.

Para aplicaciones Android, Visual Studio para Mac incluye su propio diseñador, que funciona con archivos `.axml` de Android para crear visualmente las interfaces de usuario. Visual Studio para Mac abre estos archivos en Android Designer, como se muestra en la imagen siguiente:

![Diseñador de IU de Android](media/intro-image31.png)

Para obtener más información sobre Android Designer, vea el documento de [información general sobre Android Designer](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview).

### <a name="ios"></a>iOS

iOS Designer está totalmente integrado con Visual Studio para Mac y permite la edición visual de archivos .xib y de guión gráfico para crear interfaces de usuario y transiciones de iOS, tvOS y watchOS. La interfaz de usuario al completo puede compilarse mediante la funcionalidad de arrastrar y colocar entre el cuadro de herramientas y la superficie de diseño, mientras se usa un enfoque intuitivo para controlar los eventos. iOS Designer también admite [controles personalizados](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) con la ventaja adicional de representación en tiempo de diseño.

![Diseñador de guiones gráficos de iOS](media/intro-image30.png)

Para obtener más información sobre cómo se usa iOS Designer, vea los documentos sobre el [diseñador](https://developer.xamarin.com/guides/ios/user_interface/designer).

### <a name="mac"></a>Mac

Xamarin proporciona enlaces nativos de API de Mac, lo que permite crear atractivas aplicaciones de Mac.

Para obtener más información sobre cómo escribir aplicaciones de Mac con Visual Studio para Mac, vea la documentación de [Xamarin.Mac](https://developer.xamarin.com/guides/#mac).

## <a name="gaming"></a>Juegos

Visual Studio para Mac proporciona compatibilidad con el desarrollo de juegos multiplataforma con Unity 5.6.1.

Para empezar, vea el [laboratorio práctico](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started) de Unity.

## <a name="enterprise-features"></a>Características empresariales

> [!Note]
> Estos productos solo se pueden usar con una suscripción de Visual Studio Enterprise.

### <a name="profiler"></a>generador de perfiles

Xamarin Profiler tiene disponibles tres instrumentos para la generación de perfiles. En la guía de introducción a [Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) se explora lo que miden dichos instrumentos y cómo analizan la aplicación, y se explica el significado de los datos presentados en cada pantalla.

### <a name="inspector"></a>Inspector

Xamarin Inspector proporciona una consola de C# interactiva con herramientas de usuario. Se puede usar como ayuda para la depuración o el diagnóstico al inspeccionar las aplicaciones activas, o bien como herramienta de aprendizaje, documentación o experimentación.

![Xamarin Inspector](media/intro-inspector.png)

Consta de una aplicación independiente que proporciona una consola de C# enriquecida que puede tener como destino varias plataformas de programación (Android, iOS, Mac y Windows), así como integrarse en el flujo de trabajo de depuración del IDE. 

Para obtener más información, vea la guía de [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/).

## <a name="next-steps"></a>Pasos siguientes

- **Paseo introductorio**: para obtener una visión general de muchas de las características principales de Visual Studio para Mac, vea el [paseo por el IDE](/visualstudio/mac/ide-tour/) de Visual Studio para Mac.
- **Configuración**: para obtener información sobre cómo descargar e instalar Visual Studio 2017 para Mac, vea la [Guía de instalación](/visualstudio/mac/installation/?view=vsmac-2017).
- **Tutoriales de Xamarin**: para obtener más información sobre cómo desarrollar código con Xamarin, vaya al [Centro para desarrolladores](https://developer.xamarin.com) de Xamarin.
- **Vídeos**: para obtener más información sobre otras características y aspectos de Visual Studio para Mac, vea los vídeos del sitio web de [Xamarin University](https://university.xamarin.com).
- **Laboratorios prácticos**: para empezar a trabajar con las diversas cargas de trabajo incluidas en Visual Studio para Mac, vea los [laboratorios prácticos](https://github.com/Microsoft/vs4mac-labs).
