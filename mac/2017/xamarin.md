---
title: Xamarin
description: 'Xamarin en Visual Studio para Mac le permite crear aplicaciones multiplataforma destinadas a iOS, Mac, Android, tvOS y watchOS. '
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/12/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: overview
ms.openlocfilehash: 89d724a9ddf4c8f3dc7fe941e5e4d999d30da1e8
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950629"
---
# <a name="xamarin-mobile-app-development"></a>Desarrollo de aplicaciones móviles con Xamarin

La compatibilidad de primera clase con [Xamarin](/xamarin) le permite desarrollar experiencias nativas completas para Android, macOS, iOS, tvOS y watchOS. Las aplicaciones multiplataforma de Xamarin.Forms ayudan a compartir código de interfaz de usuario basado en XAML entre Android, iOS y macOS sin limitar el acceso a la funcionalidad nativa.

## <a name="android"></a>Android

Visual Studio para Mac tiene su propio administrador de Android SDK integrado, lo que permite acceder a los SDK de la aplicación de destino.

Para aplicaciones Android, Visual Studio para Mac incluye su propio diseñador, que funciona con archivos `.axml` de Android para crear visualmente las interfaces de usuario. Visual Studio para Mac abre estos archivos en Android Designer, como se muestra en la imagen siguiente:

![Diseñador de IU de Android](media/intro-image31.png)

Para obtener más información sobre Android Designer, consulte la guía de [información general sobre Xamarin.Android Designer](/xamarin/android/user-interface/android-designer/index).

## <a name="ios"></a>iOS

iOS Designer está totalmente integrado con Visual Studio para Mac y permite la edición visual de archivos .xib y de guión gráfico para crear interfaces de usuario y transiciones de iOS, tvOS y watchOS. La interfaz de usuario al completo puede compilarse mediante la funcionalidad de arrastrar y colocar entre el cuadro de herramientas y la superficie de diseño, mientras se usa un enfoque intuitivo para controlar los eventos. iOS Designer también admite [controles personalizados](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) con la ventaja adicional de representación en tiempo de diseño.

![Diseñador de guiones gráficos de iOS](media/intro-image30.png)

Para obtener más información sobre cómo se usa iOS Designer, vea las guías de [Designer](/xamarin/ios/user-interface/designer/?tabs=macos).

### <a name="mac"></a>Mac

Xamarin proporciona enlaces nativos de API de Mac, lo que permite crear atractivas aplicaciones de Mac.

Para obtener más información sobre cómo escribir aplicaciones de Mac con Visual Studio para Mac, consulte las guías de [Xamarin.Mac](/xamarin/mac/get-started/index).

## <a name="xamarin-enterprise-features"></a>Características de Xamarin Enterprise

> [!Note]
> Estos productos solo se pueden usar con una suscripción de Visual Studio Enterprise.

### <a name="profiler"></a>generador de perfiles

Xamarin Profiler tiene disponibles tres instrumentos para la generación de perfiles. En la guía de introducción a [Xamarin Profiler](/xamarin/tools/profiler/index?tabs=macos) se explora lo que miden dichos instrumentos y cómo analizan la aplicación, y se explica el significado de los datos presentados en cada pantalla.

### <a name="inspector"></a>Inspector

Xamarin Inspector proporciona una consola de C# interactiva con herramientas de usuario. Se puede usar como ayuda para la depuración o el diagnóstico al inspeccionar las aplicaciones activas, o bien como herramienta de aprendizaje, documentación o experimentación.

![Xamarin Inspector](media/intro-inspector.png)

Consta de una aplicación independiente que proporciona una consola de C# enriquecida que puede tener como destino varias plataformas de programación (Android, iOS, Mac y Windows), así como integrarse en el flujo de trabajo de depuración del IDE.

Para obtener más información, vea la guía de [Xamarin Inspector](/xamarin/tools/inspector/).