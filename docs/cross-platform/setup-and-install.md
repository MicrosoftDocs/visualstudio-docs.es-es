---
title: Instalación de Xamarin para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/13/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: asb3993
ms.author: amburns
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: a935ab3768d5e900aea681b392e920763cb53016
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="setup-and-install"></a>Configuración e instalación

Para compilar aplicaciones nativas para iOS, Android y Windows a partir de una base de código común de C#/.NET con Xamarin, necesita lo siguiente:

-   Para trabajar con aplicaciones Windows y Android: un equipo de desarrollo de Windows con Visual Studio 2017 o 2015 con Xamarin instalado. También puede usar Visual Studio 2013 si sigue las instrucciones para la [instalación directa de Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).

-   Para trabajar con aplicaciones de iOS: Mac con macOS Sierra 10.12 o versiones posteriores, con XCode y Xamarin instalados.

 Puede configurar los equipos Windows y Mac a la vez y, mientras se ejecutan estos instaladores, puede repasar [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) para leer y ver el material de referencia necesario.

Si tiene problemas con Xamarin después de realizar esta configuración e instalación, publique su pregunta en [forums.xamarin.com](http://forums.xamarin.com/).

> [!NOTE]
> Desde el 31 de marzo de 2016, Xamarin al completo se incluye con todas las ediciones de Visual Studio sin costo adicional y sin necesidad de una licencia independiente. Xamarin Studio Community para Mac también es gratuito para estudiantes, desarrolladores de OSS y equipos pequeños. Tenga en cuenta que para las instalaciones existentes de Visual Studio que se configuraron con licencias de Xamarin anteriores, deberá actualizar Xamarin a la versión 4.0.3.214 o superior. Para ello, vaya a **Herramientas > Opciones > Xamarin > Otras**, haga clic en el vínculo **Comprobar ahora** y descargue la actualización 4.0.3.214. Al reiniciar Visual Studio, vaya a **Herramientas > Cuenta de Xamarin...** Debería ver el estado actualizado.

##  <a name="prereq"></a> Requisitos previos

###  <a name="for-targeting-windows-and-android"></a>Para seleccionar Windows y Android como destino

1.  Recomendación: Equipo Windows físico (no una VM) con Windows 8 o versiones posteriores para obtener el mejor rendimiento del emulador de Android. (¿Hemos mencionado que necesita un equipo físico y no una máquina virtual?)

2.  Puede usar un equipo con Windows 7 o una versión anterior, en cuyo caso usará Xamarin Player para Android como el emulador.

3. Para cualquier configuración, siempre puede ejecutar aplicaciones directamente en los dispositivos físicos conectados.

### <a name="for-targeting-ios"></a>Para seleccionar iOS como destino

1.  Equipo Mac o Mac mini en red con macOS Sierra 10.12 o versiones posteriores (necesario para Xcode 8.3).

2.  Cuando se usa Visual Studio en un equipo Windows (7 y versiones posteriores) como entorno de desarrollo principal, solo se necesita un Mac en red para compilar y depurar aplicaciones de iOS, asociarse con el simulador de iOS o dispositivos anclados a red, y para usar el diseñador de guion gráfico de Visual Studio para diseñar la interfaz de usuario. Los modelos más antiguos de Mac son completamente suficientes para este rol secundario.

##  <a name="windows"></a> Configuración de Windows (Visual Studio y Xamarin)

> [!TIP]
> Estas instrucciones se aplican a Visual Studio 2017. Para Visual Studio 2015, consulte [MSDN](setup-and-install.md). Para usar Xamarin con Visual Studio 2013 (es necesaria la Actualización 2), siga las instrucciones para la [instalación directa de Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).

1.  [Descargue e inicie el instalador de cualquier edición de Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional o Enterprise). Visual Studio 2017 Community es la edición gratuita. Existe una versión de prueba de 30 días de las ediciones Professional y Enterprise, después de la cual tendrá que comprar una licencia.

    - Si ya tiene Visual Studio 2017 instalado, ejecute el **instalador de Visual Studio** desde el menú **Inicio**.

2.  En el programa de instalación, haga clic en el botón **Más** y después elija **Modificar**:

    ![Elegir la opción Modificar en la instalación de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Cross-Plat Xamarin Setup 1")

3.  Active las siguientes casillas:

    - **Aplicaciones móviles y juegos > Desarrollo móvil con .NET**. Al hacerlo, también se seleccionarán automáticamente las distintas herramientas de Android en Kits de desarrollo de software y herramientas comunes. Esta opción también debe actualizar cualquier instalación de Xamarin existente.

        ![Seleccionar la opción Desarrollo móvil en Desarrollo móvil y de juegos](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Cross-Plat Xamarin Setup 2")

    - (Opcional) **Windows > Desarrollo de plataforma universal de Windows**. Se incluyen opciones para instalar imágenes de emuladores que tardarán más tiempo en descargarse; siempre puede volver al instalador de Visual Studio para agregarlos más adelante.

4.  Haga clic en el botón **Modificar** y deje que se ejecute el proceso. De nuevo, este proceso tardará algo de tiempo en completarse, durante el cual puede continuar con las instrucciones de configuración del Mac y repasar [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Una vez completada la instalación, inicie Visual Studio e inicie sesión con su cuenta de Microsoft si se le solicita (es decir, la misma cuenta que usa con Windows).

6.  Si no tiene un dispositivo físico y quiere probar aplicaciones de Android, use el [emulador de Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/). Vea la nota siguiente.

> [!NOTE]
> **Emuladores en equipos Windows**: dado que las CPU solo admiten una tecnología de virtualización a la vez, es mejor tener solo una en uso en un equipo de desarrollo. Existen tres tecnologías de virtualización principales: Hyper-V (la usan el emulador de Visual Studio para Android y el emulador de Windows Phone), Virtual Box (la usa Genymotion) y HAXM de Intel (la usa el emulador del SDK de Android). Debido a problemas diversos entre Hyper-V y Virtual Box, es recomendable usar emuladores de un solo tipo en un equipo determinado. De ahí las recomendaciones anteriores de usar Hyper-V en equipos con Windows 8 y versiones posteriores, y emuladores HAXM de Intel para Windows 7 y versiones anteriores, y también cuando se ejecute Windows en un equipo Mac.

##  <a name="mac"></a> Configuración de Mac (ID de Apple, Xcode y Xamarin)

1.  Cree un ID de Apple gratuito en [https://appleid.apple.com](https://appleid.apple.com/) si aún no tiene uno. Este paso es necesario para la instalación y el inicio de sesión en Xcode.

2.  Descargue e instale Xcode desde [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) y agregue el ID de Apple tal y como se describe en [Adding Your Account to XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Agregar su cuenta a XCode) en apple.com.

3.  Descargue e instale Xamarin siguiendo las instrucciones de [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (Instalación y configuración de Xamarin.iOS) en xamarin.com.

4.  Cuando complete la instalación de Xamarin en los equipos Windows y Mac, siga las instrucciones de [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (Conexión al Mac) en xamarin.com para poder trabajar con iOS y Mac desde Visual Studio en el equipo Windows.

    Tenga en cuenta que ambos equipos deben estar en la misma red local.