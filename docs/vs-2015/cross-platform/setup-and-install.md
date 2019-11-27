---
title: Configuración e instalación | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: 430c54527ad0a4647bb750c505942242688aaa17
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297719"
---
# <a name="setup-and-install"></a>Configuración e instalación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para compilar aplicaciones nativas para iOS, Android y Windows a partir de una base de código común de C#/.NET con Xamarin, necesita lo siguiente:  
  
- Para trabajar con aplicaciones Windows y Android: un equipo de desarrollo de Windows con Visual Studio 2015 y Xamarin 4 instalado (vea la nota a continuación). (También puede usar Visual Studio 2013 si sigue las instrucciones para la [instalación directa de Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) en xamarin.com).   
  
- Para trabajar con aplicaciones de iOS: un equipo Mac con OS X Yosemite (10.10.5) o superior, con XCode y Xamarin instalados.  
  
  Puede configurar los equipos Windows y Mac a la vez y, mientras se ejecutan estos instaladores, puede repasar [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) para leer y ver el material de referencia necesario.  
 
Si tiene problemas con Xamarin después de realizar esta configuración e instalación, publique su pregunta en [forums.xamarin.com](https://forums.xamarin.com/).
  
> [!NOTE]
> Desde el 31 de marzo de 2016, Xamarin al completo se incluye con todas las ediciones de Visual Studio sin costo adicional y sin necesidad de una licencia independiente. Xamarin Studio Community para Mac también es gratuito para estudiantes, desarrolladores de OSS y equipos pequeños. Tenga en cuenta que para las instalaciones existentes de Visual Studio que se configuraron con licencias de Xamarin anteriores, deberá actualizar Xamarin a la versión 4.0.3.214 o superior. Para ello, vaya a **Herramientas > Opciones > Xamarin > Otras**, haga clic en el vínculo **Comprobar ahora** y descargue la actualización 4.0.3.214. Al reiniciar Visual Studio, vaya a **Herramientas > Cuenta de Xamarin...** Debería ver el estado actualizado.  
  
 **En este tema:**  
  
- [Requisitos previos](#prereq)  
  
- [Configuración de Windows (Visual Studio y Xamarin)](#windows)  
  
- [Configuración de Mac (ID de Apple, Xcode y Xamarin)](#mac)  
  
## <a name="prereq"></a> Requisitos previos  
  
1. Para seleccionar Windows y Android como destino:  
  
    1. Recomendado: un equipo físico de Windows (no una máquina virtual) que ejecute Windows 8 o posterior, y que permita el uso del emulador rápido de Visual Studio para Android basado en Hyper-V si no tiene un dispositivo Android. (¿Hemos mencionado que necesita un equipo físico y no una máquina virtual?)  
  
    1. Puede usar un equipo con Windows 7 o una versión anterior, en cuyo caso usará Xamarin Player para Android como el emulador. 
    
    1. Para cualquier configuración, siempre puede ejecutar aplicaciones directamente en los dispositivos físicos conectados.  
  
1. Para seleccionar iOS como destino:  
  
    1. Un equipo Mac o Mac mini en red con OSX Yosemite ejecutándose en OS X 10.10.5 o posterior (necesario para Xcode 7.1).  
  
    1. Cuando se usa Visual Studio en un equipo Windows (7 y versiones posteriores) como entorno de desarrollo principal, solo se necesita un Mac en red para compilar y depurar aplicaciones de iOS, asociarse con el simulador de iOS o dispositivos anclados a red, y para usar el diseñador de guion gráfico de Visual Studio para diseñar la interfaz de usuario. Los modelos más antiguos de Mac son completamente suficientes para este rol secundario.  
  
## <a name="windows"></a> Configuración de Windows (Visual Studio y Xamarin)  
  
> [!TIP]
> Estas instrucciones se aplican a Visual Studio 2015. Para usar Xamarin con Visual Studio 2013 (es necesaria la Actualización 2), siga las instrucciones para la [instalación directa de Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) en xamarin.com.  
  
1. [Descargue e inicie el instalador de cualquier edición de Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional o Enterprise). Visual Studio 2015 Community es la edición gratuita. Existe una versión de prueba de 30 días de las ediciones Professional y Enterprise, después de la cual tendrá que comprar una licencia.  
  
   1. Si ya tiene Visual Studio instalado, abra **Panel de Control > Programas y características**, elija el elemento **Visual Studio 2015** y haga clic en **Cambiar**. Cuando se abra el programa de instalación, haga clic en **Modificar** y vaya al paso 3 siguiente.  
  
2. (Solo para instalaciones nuevas) En el instalador, seleccione una instalación **Personalizada**:  
  
    ![Elegir la opción personalizada en la instalación de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Instalación de Xamarin entre varios forros 1")  
  
3. Active las siguientes casillas:  
  
   1. **Desarrollo móvil multiplataforma > C#/.NET (Xamarin)** . Al hacerlo, también se seleccionarán automáticamente las distintas herramientas de Android en Kits de desarrollo de software y herramientas comunes. Esta opción también debe actualizar cualquier instalación de Xamarin existente.  
  
        ![Seleccionar la opción Xamarin en desarrollo&#45;móvil multiplataforma](../cross-platform/media/cross-plat-xamarin-setup-2.png "Instalación de Xamarin de varios forros 2")  
  
   2. Para Windows 8 y versiones posteriores: **Desarrollo móvil multiplataforma > Emulador de Microsoft Visual Studio para Android**. Nota: si usa un equipo con Windows 7 o anterior, o ejecuta Windows en un Mac, asegúrese de que esta opción esté *desactivada*. Vea "Nota sobre los emuladores en equipos Windows" después del paso 5. También puede dejar esta opción desactivada si piensa depurar únicamente en dispositivos Android físicos.  
  
   3. (Opcional) Si tiene previsto usar como destino dispositivos Windows, active también **Desarrollo de Web y de Windows > Herramientas de desarrollo de aplicaciones universales de Windows** y/o **Herramientas de Windows 8.1 y Windows Phone 8.0/8.1**. Se incluyen opciones para instalar imágenes de emuladores que tardarán más tiempo en descargarse; siempre puede volver al instalador de Visual Studio para agregarlos más adelante.  
  
4. Haga clic en el botón Instalar y deje que se ejecute el proceso. De nuevo, este proceso tardará algo de tiempo en completarse, durante el cual puede continuar con las instrucciones de configuración del Mac y repasar [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Una vez completada la instalación, inicie Visual Studio e inicie sesión con su cuenta de Microsoft si se le solicita (es decir, la misma cuenta que usa con Windows). Después, busque actualizaciones de Xamarin a través de **Herramientas > Opciones > Xamarin** o **Herramientas > Opciones > Xamarin > Otras**, donde encontrará el vínculo **Comprobar ahora**:  
  
    ![Comprobar las actualizaciones de Xamarin en las opciones de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Instalación entre varios forros de Xamarin 3")  
  
   > [!NOTE]
   > Como se indicó anteriormente, asegúrese de actualizar Xamarin a la versión 4.0.3.214 o superior para evitar problemas con las licencias de Xamarin anteriores.  

   Si no ve una opción para Xamarin en **Herramientas > Opciones**, vuelva a comprobar la instalación o intente reiniciar Visual Studio. También puede buscar Xamarin en el cuadro de diálogo Opciones.
      
6. Para Windows 7 y versiones anteriores, o si se ejecuta Windows en un equipo Mac, use el [emulador de Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) si no tiene dispositivos físicos. Vea la nota siguiente.  
  
   **Nota sobre los emuladores en equipos Windows:** Dado que las CPU solo admiten una tecnología de virtualización a la vez, es mejor tener solo una en uso en un equipo de desarrollo. Existen tres tecnologías de virtualización principales: Hyper-V (la usan el emulador de Visual Studio para Android y el emulador de Windows Phone), Virtual Box (la usa Genymotion) y HAXM de Intel (la usa el emulador del SDK de Android). Debido a problemas diversos entre Hyper-V y Virtual Box, es recomendable usar emuladores de un solo tipo en un equipo determinado. De ahí las recomendaciones anteriores de usar Hyper-V en equipos con Windows 8 y versiones posteriores, y emuladores HAXM de Intel para Windows 7 y versiones anteriores, y también cuando se ejecute Windows en un equipo Mac.  
  
## <a name="mac"></a> Configuración de Mac (ID de Apple, Xcode y Xamarin)  
  
1. Cree un ID de Apple gratuito en [https://appleid.apple.com](https://appleid.apple.com/) si todavía no tiene uno. Este paso es necesario para la instalación y el inicio de sesión en Xcode.  
  
2. Descargue e instale Xcode desde [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) y agregue el ID de Apple tal y como se describe en [Adding Your Account to XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Agregar su cuenta a XCode) en apple.com.  
  
3. Descargue e instale Xamarin siguiendo las instrucciones de [Installing and Configuring Xamarin.iOS](https://docs.microsoft.com/xamarin/ios/get-started/installation/mac) (Instalación y configuración de Xamarin.iOS) en xamarin.com.  
  
4. Cuando complete la instalación de Xamarin en los equipos Windows y Mac, siga las instrucciones de [Connecting to the Mac](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Conexión al Mac) en xamarin.com para poder trabajar con iOS y Mac desde Visual Studio en el equipo Windows.  
  
     Tenga en cuenta que ambos equipos deben estar en la misma red local.
