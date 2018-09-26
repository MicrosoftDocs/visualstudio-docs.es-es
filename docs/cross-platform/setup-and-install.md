---
title: Instalación de Xamarin para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 045b7745d8d9d171560546e893e89ea6cebe1b6f
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495900"
---
# <a name="setup-and-install"></a>Configuración e instalación

Para compilar aplicaciones nativas para iOS, Android y Windows a partir de una base de código común de C#/.NET con Xamarin, necesita los siguientes componentes de hardware y software:

-   Para trabajar con aplicaciones Windows y Android: un equipo de desarrollo Windows (no una máquina virtual) con Visual Studio 2017 (incluidas las características de desarrollo de Xamarin) instalado.

-   Para trabajar con aplicaciones iOS: Mac con macOS Sierra 10.12 o versiones posteriores, con Xcode y Visual Studio para Mac instalados.

Para utilizar la plataforma de Xamarin, no es necesario disponer de ninguna licencia aparte.

Puede configurar los equipos Windows y Mac a la vez y, mientras se ejecutan estos instaladores, puede repasar [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) para leer y ver el material de referencia necesario.

Si tiene problemas con la plataforma de Xamarin después de realizar esta configuración e instalación, publique su pregunta en [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" />

## <a name="pre-requisites"></a>Requisitos previos

###  <a name="for-targeting-windows-and-android"></a>Para seleccionar Windows y Android como destino

Vea [Requisitos de sistema de la familia de productos Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-vs) para obtener información detallada sobre los requisitos previos para la instalación de Visual Studio 2017.

Instale Visual 2017 en un equipo físico Windows (no en una máquina virtual) que ejecute Windows 10 con todas las actualizaciones instaladas.

### <a name="for-targeting-ios"></a>Para seleccionar iOS como destino

Para utilizar emuladores de iOS y dispositivos de su equipo Windows como destino, también necesitará un Mac conectado a una red o un Mac mini con macOS 10.12 o una versión posterior y Xcode 8.3. Vea [Configuración e instalación de Visual Studio para Mac](/visualstudio/mac/installation) para obtener información más detallada sobre los requisitos.

<a name="windows" />

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Configuración de Windows (Visual Studio y Xamarin)

Si aún no tiene instalado Visual Studio 2017, realice los pasos siguientes:

1.  [Descargue e inicie el instalador de cualquier edición de Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community, Professional o Enterprise). Visual Studio 2017 Community es la edición gratuita. Las ediciones Professional y Enterprise están disponibles en una versión de prueba de 30 días, tras la cual es necesaria una licencia.

2.  Cuando aparezca el cuadro de diálogo **Instalar**, marque las casillas siguientes:

    - **Aplicaciones móviles y juegos > Desarrollo móvil con .NET**. Esta opción también seleccionará automáticamente diversos Kits de desarrollo de Software y herramientas de Android.

        ![Seleccionar la opción Desarrollo móvil en Desarrollo móvil y de juegos](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Cross-Plat Xamarin Setup 2")

    - (Opcional) **Windows > Desarrollo de plataforma universal de Windows**.

Si ya tiene Visual Studio 2017 instalado, pero aún no ha instalado la plataforma Xamarin, realice los pasos siguientes:

1. Ejecute el **instalador de Visual Studio** desde el menú **Iniciar**.

2.  En el programa de instalación, haga clic en el botón **Más** y después elija **Modificar**:

    ![Elegir la opción Modificar en la instalación de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Cross-Plat Xamarin Setup 1")

3.  Cuando aparezca el cuadro de diálogo **Instalar**, marque las opciones **Dispositivos móviles y juegos > Desarrollo para dispositivos móviles con .NET** y (opcionalmente) **Windows > Desarrollo de la Plataforma universal de Windows**. La opción **Desarrollo para dispositivos móviles con .NET** también debe actualizar cualquier instalación de Xamarin existente.

Mientras se ejecuta la instalación, puede continuar con las instrucciones de instalación de Mac y consultar [Información sobre el desarrollo para dispositivos móviles con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Una vez completada la instalación, inicie Visual Studio e inicie sesión con su cuenta de Microsoft si se le solicita. Esta cuenta es la misma que utiliza con Windows.

6.  Para probar aplicaciones de Android, use el [emulador del SDK de Android](/xamarin/android/get-started/installation/android-emulator/) si no tiene un dispositivo físico Android.

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Configuración de Mac (ID de Apple, Xcode y Xamarin)

1.  Cree un ID de Apple gratuito en [https://appleid.apple.com](https://appleid.apple.com/) si aún no tiene uno. Este ID de Apple es necesario para instalar e iniciar sesión en Xcode.

2.  Descargue e instale Xcode desde [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) y agregue el ID de Apple, tal como se describe en [Agregar la cuenta a Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).

3.  Para descargar e instalar Visual Studio para Mac, siga las instrucciones que aparecen en [Configuración e instalación de Visual Studio para Mac](/visualstudio/mac/installation).

4.  Una vez que haya completado la instalación de Xamarin en los equipos Windows y Mac, siga las instrucciones de [Conectarse al equipo Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) para que pueda trabajar con iOS y Mac desde Visual Studio en el equipo Windows.

Ambos equipos deben estar en la misma red local.
