---
title: "Instalar Visual C++ para desarrollo móvil multiplataforma | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b9f87e95a2d4088bb72890ef3f9508d9c5e02abc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Instalar Visual C++ para el desarrollo móvil multiplataforma
[Visual C++ para el desarrollo móvil multiplataforma](http://go.microsoft.com/fwlink/p/?LinkId=536383) es un componente opcional instalable incluido en Visual Studio 2015. Incluye plantillas de Visual Studio de varias plataformas e instala las herramientas de desarrollo multiplataforma y SDK que permiten comenzar a usarlos sin tener que buscarlos, descargarlos y configurarlos usted mismo. Puede usar estas herramientas en Visual Studio para crear, editar, depurar y probar proyectos para varias plataformas de manera sencilla. Este tema describe cómo instalar las herramientas y los software de terceros necesarios para desarrollar aplicaciones multiplataforma con Visual Studio. Para obtener información general del componente, vea [Desarrollo móvil multiplataforma de Visual Studio C++](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Requisitos](#Requirements)   
 [Obtener las herramientas](#GetTheTools)   
 [Instalar las herramientas](#InstallTheTools)   
 [Install tools for iOS](#InstallForiOS)   
 [Instalar o actualizar manualmente las dependencias](#ThirdParty)  
  
##  <a name="Requirements"></a> Requisitos  
  
-   Para obtener información sobre los requisitos de instalación, vea [Requisitos de sistema de Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
    > [!IMPORTANT]
    >  Si usa Windows 7 o Windows Server 2008 R2, puede desarrollar código para aplicaciones de Windows clásico, aplicaciones Android Native Activity y bibliotecas, así como aplicaciones y bibliotecas de código para iOS, pero no aplicaciones Windows universales ni de la Tienda Windows.  
  
 Existen algunos requisitos adicionales para la compilación de aplicaciones para plataformas de dispositivo específicas:  
  
-   Los emuladores de Windows Phone y el emulador de Microsoft Visual Studio para Android requieren un equipo que pueda ejecutar Hyper-V. Debe habilitarse la característica de Hyper-V en Windows antes de poder instalar y ejecutar los emuladores. Para más información, vea los [requisitos del sistema](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf) del emulador.  
  
-   Los emuladores de Android x86 que vienen con el SDK de Android funcionan mejor en equipos que pueden ejecutar el controlador HAXM de Intel. Este controlador requiere un procesador Intel x64 compatible con VT-x y Execute Disable Bit. Para obtener más información, vea [Installation Instructions for Intel® Hardware Accelerated Execution Manager - Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
-   La compilación de código para iOS requiere un ID de Apple, una cuenta del programa de desarrolladores de iOS y un equipo Mac que permita la ejecución de [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) o una versión posterior en OS X Mavericks o versiones posteriores. Para obtener pasos de instalación sencillos, vea [Install tools for iOS](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Obtener las herramientas  
 Visual C++ para desarrollo móvil multiplataforma es un componente instalable incluido en las ediciones Professional y Enterprise de Visual Studio Community. Para obtener Visual Studio, vaya a la página [Descargas de Visual Studio 2015](http://go.microsoft.com/fwlink/p/?linkid=517106) y descargue Visual Studio 2015 con la actualización 2 o una versión posterior.  
  
##  <a name="InstallTheTools"></a> Instalar las herramientas  
 El instalador de Visual Studio 2015 incluye una opción para instalar Visual C++ para el desarrollo móvil multiplataforma. Esto instala las herramientas, plantillas y componentes del lenguaje C++ requeridos para Visual Studio, los conjuntos de herramientas de GCC y Clang necesarios para las compilaciones y depuraciones en Android, y los componentes para la comunicación con un equipo Mac para el desarrollo de iOS. También instala todas las herramientas de terceros y los kits de desarrollo de software necesarios para admitir el desarrollo de aplicaciones iOS y Android. La mayoría de estas herramientas de terceros son aplicaciones de código abierto necesarias para la compatibilidad con la plataforma Android.  
  
-   El kit de desarrollo nativo de Android (NDK) es necesario para compilar el código de C++ destinado a la plataforma Android.  
  
-   El SDK de Android, Apache Ant y el kit de desarrollo para Java SE son necesarios para el proceso de compilación de Android.  
  
-   El emulador de Microsoft Visual Studio para Android es un emulador de alto rendimiento opcional útil para probar y depurar el código.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Para instalar Visual C++ para el desarrollo móvil multiplataforma y las herramientas de terceros  
  
1.  Ejecute el instalador de Visual Studio 2015 que descargó siguiendo el vínculo en [Obtener las herramientas](#GetTheTools). Para instalar componentes opcionales, elija **Personalizado** como tipo de instalación. Elija **Siguiente** para seleccionar los componentes opcionales que desea instalar.  
  
2.  En Seleccionar características, expanda **Desarrollo móvil multiplataforma** y seleccione **Desarrollo móvil de Visual C++**.  
  
     ![Seleccione Desarrollo móvil de Visual C++](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")  
  
     De forma predeterminada, cuando se selecciona **Desarrollo móvil de Visual C++**, la opción **Lenguajes de programación** se establece para instalar **Visual C++** y las opciones **Kits de desarrollo de software y herramientas comunes** se establecen para instalar los componentes de terceros necesarios. Puede elegir componentes adicionales si los necesita. De forma predeterminada, también se selecciona el **Emulador de Microsoft Visual Studio para Android**. Los componentes que ya están instalados aparecen inactivos en la lista.  
  
     Para compilar aplicaciones universales de Windows y compartir código entre ellas y los proyectos de iOS y Android, en **Seleccionar características**, expanda **Desarrollo de Web y de Windows** y active **Herramientas de desarrollo de aplicaciones universales de Windows**. Si no planea compilar aplicaciones universales de Windows, puede omitir esta opción.  
  
     Elija **Siguiente** para continuar.  
  
3.  Los componentes de terceros tienen sus propios términos de licencia. Puede ver los términos de licencia eligiendo el vínculo **Términos de licencia** situado junto a cada componente. Haga clic en **Instalar** para agregar los componentes e instalar Visual Studio y Visual C++ para desarrollo móvil multiplataforma.  
  
4.  Cuando se complete la instalación, cierre el programa de instalación y después reinicie el equipo. Algunas acciones de instalación para los componentes de terceros surtirán efecto cuando se reinicie el equipo.  
  
    > [!IMPORTANT]
    >  Debe reiniciarlo para asegurarse de que todo se ha instalado correctamente.  
  
     Si no se pudo instalar el componente Emulador de Microsoft Visual Studio para Android, es posible que Hyper-V no esté habilitado en el equipo. Use la aplicación del Panel de Control **Activar o desactivar las características de Windows** para habilitar Hyper-V y, después, ejecute de nuevo el programa de instalación de Visual Studio.  
  
    > [!NOTE]
    >  Si su equipo o su versión de Windows no es compatible con Hyper-V, no puede usar el componente Emulador de Microsoft Visual Studio para Android. Windows Home Edition no es compatible con Hyper-V.  
  
5.  Abra Visual Studio. Si es la primera vez que ejecuta Visual Studio, puede tardar algún tiempo en configurar e iniciar sesión. Cuando Visual Studio esté listo, en el menú **Herramientas** , seleccione **Extensiones y actualizaciones**, **Actualizaciones**. Si hay actualizaciones disponibles de Visual Studio para Visual C++ para el desarrollo móvil multiplataforma o para el Emulador de Microsoft Visual Studio para Android, instálelas.  
  
##  <a name="InstallForiOS"></a> Install tools for iOS  
 Puede usar Visual C++ para el desarrollo móvil multiplataforma para editar, depurar e implementar código de iOS en el simulador de iOS o en un dispositivo de iOS; sin embargo, debido a las restricciones de licencia, el código se debe compilar de manera remota en un equipo Mac. Para compilar y ejecutar aplicaciones de iOS con Visual Studio, debe instalar y configurar el agente remoto en el equipo Mac. Para obtener instrucciones de instalación detalladas, información sobre opciones de configuración y requisitos previos, vea [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Si no va a compilar aplicaciones para iOS, puede omitir este paso.  
  
##  <a name="ThirdParty"></a> Instalar o actualizar manualmente las dependencias  
 Si decide no instalar una o más dependencias de terceros mediante el instalador de Visual Studio al instalar la opción de desarrollo móvil de Visual C++, puede instalarlas más adelante siguiendo los pasos que se describen en [Install the tools](#InstallTheTools). También puede instalarlas o actualizarlas independientemente de Visual Studio.  
  
> [!CAUTION]
>  Las dependencias se pueden instalar en cualquier orden, a excepción de Java. Debe instalar y configurar el JDK antes de instalar Android SDK.  
  
 Lea la siguiente información y use estos vínculos para instalar las dependencias manualmente.  
  
-   [Kit de desarrollo de Java SE](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
     De manera predeterminada, el instalador coloca las herramientas de Java en C:\Archivos de programa (x86)\Java.  
  
-   [SDK de Android](https://developer.android.com/sdk/index.html#Other)  
  
     Durante la instalación, actualice las API según se recomienda. Asegúrese de que esté instalado por lo menos el SDK para Android 5.0 Lollipop (nivel de API 21). De manera predeterminada, el instalador coloca el SDK de Android en C:\Archivos de programa (x86)\Android\android-sdk.  
  
     Puede volver a ejecutar la aplicación de administrador de SDK en el directorio del SDK de Android para actualizar el SDK e instalar herramientas opcionales y niveles de API adicionales. Las actualizaciones pueden no instalarse correctamente si no usa la opción **Ejecutar como administrador** para ejecutar la aplicación SDK Manager. Si tiene problemas para crear una aplicación Android, compruebe el SDK Manager por si hay actualizaciones para los SDK instalados.  
  
     Para usar algunos de los emuladores de Android que vienen con el SDK de Android, debe instalar los controladores HAXM de Intel opcionales. Es posible que tenga que quitar la característica Hyper-V de Windows para instalar los controladores HAXM de Intel correctamente. Debe restaurar la característica Hyper-V para usar los emuladores de Windows Phone y el emulador de Microsoft Visual Studio para Android.  
  
-   [NDK de Android](https://developer.android.com/tools/sdk/ndk/index.html)  
  
     De forma predeterminada, el instalador coloca el NDK Android en C:\ProgramData\Microsoft\AndroidNDK. Puede volver a descargar e instalar el NDK de Android para actualizar la instalación del NDK.  
  
-   [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
     De manera predeterminada, el instalador coloca Apache Ant en C:\Archivos de programa (x86)\Microsoft Visual Studio 14.0\Apps.  
  
-   [Emulador de Microsoft Visual Studio para Android](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
     Puede instalar y actualizar el emulador de Microsoft Visual Studio para Android desde la Galería de Visual Studio.  
  
 En la mayoría de los casos, Visual Studio puede detectar las configuraciones del software de terceros que haya instalado y mantiene las rutas de instalación en variables de entorno internas. Puede reemplazar las rutas de acceso predeterminadas de estas herramientas de desarrollo multiplataforma en el IDE de Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Para establecer las rutas de acceso para las herramientas de terceros  
  
1.  En la barra de menús de Visual Studio, seleccione **Herramientas**, **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , expanda **Multiplataforma**, **C++**y seleccione **Android**.  
  
     ![Opciones de ruta de acceso de la herramienta Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")  
  
3.  Para cambiar la ruta de acceso que usa una herramienta, active la casilla situada junto a la ruta de acceso y edite la ruta de acceso de la carpeta en el cuadro de texto. También puede usar el botón Examinar (**...**) para abrir el cuadro de diálogo **Seleccionar ubicación** para seleccionar la carpeta.  
  
4.  Elija **Aceptar** para guardar las ubicaciones de carpeta de la herramienta personalizada.  
  
## <a name="see-also"></a>Vea también  
 [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Desarrollo móvil multiplataforma de Visual Studio C++](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)