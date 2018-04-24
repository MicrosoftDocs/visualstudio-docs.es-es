---
title: Comprobar el entorno de Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 862af0d8912811aee8e0110b48fa8cc3e8f1c06b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="verify-your-xamarin-environment"></a>Comprobar el entorno de Xamarin

Una vez completados los instaladores (vea [Setup and install](../cross-platform/setup-and-install.md)), dedique unos minutos a comprobar que todo esté listo para la experiencia de desarrollo de Xamarin.  
  
 Cuando haya terminado de verificar la instalación, pruebe uno o ambos de los tutoriales siguientes:  
  
-   [Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin.Forms en Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md) para compilar una aplicación de Xamarin.Forms.
  
-   [Compilar aplicaciones con interfaz de usuario nativa mediante Xamarin en Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md) para usar las interfaces de usuario nativas en cada plataforma, pero compartiendo parte del código en una biblioteca estándar de .NET.
  
## <a name="all-platforms"></a>Todas las plataformas 
 
En Visual Studio, seleccione primero **Herramientas > Extensiones y actualizaciones** y compruebe si alguno de los componentes de Xamarin requiere actualizaciones.  
  
A continuación, cree una solución nueva de Xamarin.Forms en Visual Studio; para ello, use **Archivo > Nuevo proyecto**. En el cuadro de diálogo, expanda **Visual C# > Multiplataforma**, seleccione **Aplicación móvil (Xamarin.Forms)** y haga clic en Aceptar. En el cuadro de diálogo siguiente, seleccione **Aplicación en blanco**. En **Estrategia de uso compartido de código**, seleccione **.NET Standard**. Haga clic en Aceptar.

Estas acciones crean una solución con cuatro proyectos: un proyecto compartido de biblioteca estándar de .NET 2.0 y proyectos de aplicación para Android, iOS y la Plataforma Universal de Windows (UWP):  
  
![Resultados de la creación de un nuevo proyecto a partir de la plantilla de Xamarin.Forms de la aplicación vacía](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")  
   
## <a name="android"></a>Android  
  
1. Compruebe que tiene las últimas herramientas de SDK de Android instaladas; vaya a **Herramientas > Android > Administrador de Android SDK**. Instale las versiones más recientes de las herramientas de Android SDK, las herramientas de la plataforma Android SDK y las herramientas de compilación de Android SDK. No es necesario instalar siempre el nivel de API de Android más reciente. El nivel de API que necesita depende del nivel de plataforma que desee como destino. En general, al instalar la plataforma de Xamarin se instalará el nivel de plataforma de Android que requiere.  
  
2.  Valide la compilación y la depuración en un dispositivo o emulador:  
  
    -   Haga clic con el botón derecho en el proyecto de Android en el Explorador de soluciones y seleccione **Establecer como proyecto de inicio**.  
  
    -   En la barra de herramientas, debe ver una lista desplegable con los dispositivos y emuladores Android disponibles. 
    
    Los dispositivos Android deben estar habilitados para la depuración a través de USB en las opciones del desarrollador de la página de configuración del dispositivo. A continuación, el dispositivo se conecta al equipo mediante un cable USB. 
    
    En la lista también se incluyen los emuladores. Seleccione uno de los dispositivos o de los emuladores de Visual Studio:

  ![Seleccionar el emulador de Visual Studio para Android como destino de depuración](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")  
  
  Para obtener más información, consulte [Introducing Visual Studio’s Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (Presentación del emulador de Visual Studio para Android) (Blog de Visual Studio ALM). Si tiene problemas al hacer que funcione el emulador, consulte [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). También puede seleccionar **Herramientas > Android > Administrador de Android Emulator** para crear nuevos perfiles de dispositivo para el emulador.  
  
3. Presione F5 para compilar e implementar el programa en el dispositivo o emulador Android.
  
## <a name="windows"></a>Windows 
  
1.  Haga clic con el botón derecho en el proyecto universal de Windows en el Explorador de soluciones y seleccione **Establecer como proyecto de inicio**.  

2.  En la lista desplegable **Plataformas de solución**, seleccione **x86** o **x64**. Seleccione **Equipo local**.

3.  Presione F5 para implementar el programa en el escritorio.
  
## <a name="ios"></a>iOS  
  
1.  Asegúrese de que el equipo Mac esté disponible en la red y emparejado con Visual Studio como se describe en [Conexión al equipo Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/).  
  
2.  Haga clic con el botón derecho en el proyecto de iOS en el Explorador de soluciones y seleccione **Establecer como proyecto de inicio**.  
  
3.  Seleccione el destino de **iPhoneSimulator** en el menú desplegable de la compilación de Visual Studio como se muestra a continuación, o el destino de **iPhone** si tiene un dispositivo anclado al equipo Mac.   
  
 ![Seleccionar el destino de compilación iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5") 

 Si no aparece ningún simulador, inicie Xcode en el equipo Mac, seleccione **Xcode > Preferencias** y haga clic en **Descargar**. En el título **Componentes** debe ver las versiones del simulador que están disponibles para descargar. En la página [Depuración de iOS](/xamarin/ios/deploy-test/debugging-in-xamarin-ios/?tabs=vsmac#Debugging_on_the_Simulator), puede encontrar instrucciones adicionales para la depuración.
  
4.  Seleccione un destino del dispositivo emulador en la lista desplegable de Visual Studio:

 ![Seleccionar un destino de depuración iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")

5. Presione F5 para iniciar al depurador. El simulador se inicia en el equipo Mac, en que podrá interactuar con la aplicación mientras se realiza la depuración en Visual Studio. Si tiene un iPhone o iPad físico conectado al equipo Mac, aparecerá en la lista y puede seleccionarlo en su lugar. Si no ve ningún dispositivo ni simulador en la lista, compruebe la conexión al equipo Mac. Revise el artículo vinculado en el paso 1 anterior o vaya a **Herramientas > iOS > Emparejar con Mac**  
  
6.  Si tiene problemas para conectarse al equipo Mac, consulte [Solución de problemas de conexión](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/).  
  
7.  Si ve un error que indica "No hay perfiles de aprovisionamiento instalados que coincidan con las claves de firma de iOS instaladas", pruebe las sugerencias siguientes:  
  
  - Compruebe que la cuenta de Id. de Apple está agregada Xcode en el equipo Mac, como se describe en [Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Agregar una cuenta a Xcode) en apple.com.  Después de agregar la cuenta, asegúrese de reiniciar Visual Studio y Xcode.  
    
  - En las propiedades de iOS, en la pestaña de firmas de agrupaciones de iOS, compruebe que el campo de derecho personalizado esté vacío para la configuración de depuración activa.  Nota: Solo debe intentar quitar esta configuración si ha aparecido el mensaje de error anterior.  
  
  ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")  
