---
title: Configuración, instalación y comprobaciones para usuarios de Mac | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: fca4f8ef2d3fb1272dc835b4bedd7dcdcc83725f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772838"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Configuración, instalación y comprobaciones para usuarios de Mac
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Este tema está destinado a los desarrolladores que trabajan principalmente con Mac y que, opcionalmente, usan Visual Studio en una máquina virtual de Windows en el Mac. Si es un desarrollador que trabaja principalmente en un equipo Windows y necesita configurar un Mac secundario para iOS, vea el tema [Configuración e instalación](../cross-platform/setup-and-install.md) principal.  
  
 Para trabajar con Xamarin en un Mac, necesitará lo siguiente:  
  
- Una cuenta de Xamarin. Vaya a [ https://www.xamarin.com/ ](https://www.xamarin.com/) y haga clic en **sesión** en la esquina superior derecha de la página, a continuación, haga clic en **crear una nueva cuenta** en la página que aparece. Seleccione una dirección de correo y una contraseña para su cuenta de Xamarin.  
  
- Un Mac con OSX Yosemite (10.10) o superior, con Xcode 7 y Xamarin 4 instalado.  
  
- Una de las siguientes configuraciones:  
  
  -   **Para ejecutar Xamarin Studio directamente en el Mac:** Xamarin Studio es el entorno de desarrollo de Xamarin, que admite la compilación de aplicaciones para Android, iOS y Windows con C#.  Para obtener una introducción rápida de Xamarin Studio, consulte la [información general de Xamarin Studio](https://xamarin.com/studio) (xamarin.com).  
  
  -   **Si ya tiene Parallels o VMWare configurado en el Mac:** ejecute Windows con Visual Studio 2015 y Xamarin 4 en Parallels o VMWare.  Con esta configuración, Xamarin es una extensión que se instala con Visual Studio y que ofrece la posibilidad de usar Visual Studio como entorno de desarrollo para compilar aplicaciones para Android, iOS y Windows Phone con C#.  Tenga en cuenta que puede obtener una suscripción gratuita de 3 meses de Parallels como parte del programa Visual Studio Developer Essentials. Consulte [Microsoft Visual Studio Dev Essentials Will Include Parallels Desktop Pro and Parallels Access](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (Microsoft Visual Studio Dev Essentials incluirá Parallels Desktop y Parallels Access ) en el blog de Parallels.  
  
  En este tema se ofrecen instrucciones para estos requisitos.  Mientras se ejecuta el proceso de instalación, puede revisar el tema [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) para leer y consultar el material de referencia necesario.  
  
  **En este tema:**  
  
- [Configuración de Mac (ID de Apple, Xcode y Xamarin)](#mac)  
  
- [Configuración de Windows en Parallels (Visual Studio y Xamarin)](#windows)  
  
- [Comprobar el entorno](#verify)  
  
##  <a name="mac"></a> Configuración de Mac (ID de Apple, Xcode y Xamarin)  
  
1.  Cree un ID de Apple gratuito en [Mi ID de Apple](https://appleid.apple.com/) si aún no tiene uno. Este paso es necesario para la instalación y el inicio de sesión en Xcode.  
  
2.  Descargue e instale Xcode desde [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/).  
  
3.  Descargue e instale Xamarin siguiendo las instrucciones de [Installing and Configuring Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (Instalación y configuración de Xamarin.iOS) en xamarin.com.  
  
4.  Cuando complete la instalación de Xamarin en los equipos Windows y Mac, siga las instrucciones de [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (Conexión al Mac con XMA) en xamarin.com para poder trabajar con iOS y Mac desde Visual Studio en el equipo Windows.  
  
##  <a name="windows"></a> Configuración de Windows en Parallels (Visual Studio y Xamarin)  
  
1.  Use el escritorio de Windows configurado en Parallels/VMWare para [descargar e iniciar el instalador de cualquier edición de Visual Studio 2015](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) (Community, Professional o Enterprise). Visual Studio 2015 Community es la edición gratuita; existe una versión de prueba gratuita de 30 días de las ediciones Professional y Enterprise.  
  
2.  En el instalador, seleccione una instalación **Personalizada** :  
  
     ![Elegir la opción personalizada en la instalación de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Cross-Plat Xamarin Setup 1")  
  
3.  Active o desactive las casillas siguientes:  
  
    1.  Active **Desarrollo móvil multiplataforma > C#/.NET (Xamarin)**. Al hacerlo, también se seleccionarán automáticamente las distintas herramientas de Android en Kits de desarrollo de software y herramientas comunes.  
  
         ![Seleccionar la opción Xamarin en Desarrollo móvil multiplataforma](../cross-platform/media/cross-plat-xamarin-setup-2.png "Cross-Plat Xamarin Setup 2")  
  
    2.  Desactive **Desarrollo móvil multiplataforma > Emulador de Microsoft Visual Studio para Android**.  
  
4.  Haga clic en el botón Instalar y deje que se ejecute el proceso. De nuevo, este proceso tardará algo de tiempo en completarse, durante el cual puede continuar con este tema y repasar [Más información sobre el desarrollo móvil con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  Una vez completada la instalación, inicie Visual Studio e inicie sesión con su cuenta de Microsoft si se le solicita (es decir, la misma cuenta que usa con Windows). Después, busque actualizaciones de Xamarin a través de **Herramientas > Opciones > Xamarin** o **Herramientas > Opciones > Xamarin > Otras**, donde encontrará el vínculo **Comprobar ahora**:  
  
     ![Búsqueda de actualizaciones de Xamarin en las opciones de Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Cross-Plat Xamarin Setup 3")  
  
    > [!NOTE]
    >  Asegúrese de actualizar Xamarin a la versión 4.0.3.214 o superior para evitar problemas con las licencias de Xamarin anteriores.  Si intenta buscar actualizaciones y ve un error sobre las herramientas de compilación de Microsoft, vea la conversación en los [foros de Xamarin](http://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6.  Cuando complete la instalación de Xamarin en los equipos Windows y Mac, siga las instrucciones de [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (Conexión al Mac mediante XMA) en xamarin.com para poder trabajar con iOS desde Visual Studio.  
  
##  <a name="verify"></a> Comprobar el entorno  
 Una vez completados los instaladores, dedique unos minutos a comprobar que todo está listo para la experiencia de desarrollo de Xamarin.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 En primer lugar, al navegar a los vínculos proporcionados, asegúrese de que **Xamarin Studio** esté seleccionado en la esquina superior derecha para ver la versión correcta de la documentación de Xamarin:  
  
 ![Seleccionar Xamarin Studio para ver la documentación correcta en Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Valide la creación de un proyecto de Android siguiendo las instrucciones de [Create an Android Project](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (Crear un proyecto de Android) en xamarin.com.  
  
2. Valide la depuración en el reproductor Android a través de la [documentación de Android Player > Integration with Xamarin Studio](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (Android Player > Integración con Xamarin Studio) en xamarin.com.  
  
   **iOS**  
  
3. Valide la creación de un proyecto de iOS siguiendo las instrucciones de [Create an iOS Project](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (Crear un proyecto de iOS) en xamarin.com.  
  
4. Valide la depuración en el simulador de iOS a través de la [documentación de Debugging in the Simulator](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (Depuración en el simulador) en xamarin.com.  
  
### <a name="visual-studio"></a>Programa para la mejora  
 En primer lugar, al navegar a los vínculos proporcionados, asegúrese de que **Visual Studio** esté seleccionado en la esquina superior derecha para ver la versión correcta de la documentación de Xamarin:  
  
 ![Selección de Visual Studio para ver la documentación correcta en Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 También inicie sesión en su cuenta de Xamarin a través de **Herramientas > Cuenta de Xamarin...**  
  
 **Android**  
  
1. Valide la creación de un proyecto de Android siguiendo las instrucciones de [Create an Android Project](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (Crear un proyecto de Android) en xamarin.com.  
  
2. Valide el diseñador de Android: en el proyecto de Android en el Explorador de soluciones, abra el archivo **Recursos > Diseño > Main.axml**.  
  
   -   Si recibe un error que dice "El SDK de Android instalado es demasiado antiguo", haga clic en **abrir Android SDK** en dicho mensaje y seleccione la versión del SDK más reciente disponible. Tenga en cuenta que debe estar ejecutando Visual Studio como administrador para actualizar el SDK.  
  
3. Compruebe que puede conectarse desde Visual Studio al emulador que está instalado en el Mac.  El resultado de esto es que verá el reproductor de Xamarin en la lista de los emuladores que seleccione en Visual Studio para la depuración.  To do this, follow the instructions on [Connecting Visual Studio to the Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (Conexión de Visual Studio a Xamarin Android Player) en xamarin.com.  
  
   **iOS**  
  
4. Asegúrese de que el Mac esté disponible en la red y emparejado con Visual Studio como se describe en [Connecting to the Mac using XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (Conexión al Mac mediante XMA) en xamarin.com.  
  
5. Valide la creación de un proyecto de iOS siguiendo las instrucciones de [Create an iOS Project](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (Crear un proyecto de iOS) en xamarin.com.  
  
6. Valide el diseñador del guión gráfico: en el proyecto de iOS en el Explorador de soluciones, abra el archivo **MainStoryboard.storyboard** . En este caso, Visual Studio hospeda el diseñador que se ejecuta de forma remota en el Mac.  
  
7. Valide la compilación y la depuración:  
  
   1.  Haga clic con el botón derecho en el proyecto de iOS en el Explorador de soluciones y seleccione **Establecer como proyecto de inicio**.  
  
   2.  Seleccione el destino **iPhoneSimulator** del menú desplegable de la compilación de Visual Studio, como se muestra a continuación. Si no aparece ningún simulador, inicie Xcode en el Mac, seleccione **Xcode -> Preferencias** y haga clic en **Descargar**. Bajo **Componentes** debería ver las versiones del simulador que están disponibles para descargar. Encontrará instrucciones adicionales para la depuración en la página [Depuración](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (Depuración) de Xamarin en xamarin.com.  
  
        ![Seleccionar el destino de compilación iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")  
  
   3.  Seleccione un destino de iPhone del menú desplegable de depuración de Visual Studio, tal como se muestra a continuación y presione F5 para iniciar el depurador. Se inicia el simulador en el Mac, donde podrá interactuar con la aplicación mientras se lleva a cabo la depuración en Visual Studio.  
  
        ![Seleccionar un destino de depuración iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")

