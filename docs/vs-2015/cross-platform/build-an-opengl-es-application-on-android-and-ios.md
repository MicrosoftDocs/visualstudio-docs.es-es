---
title: Crear una aplicación de OpenGL ES en iOS y Android | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.openlocfilehash: 1679884d79ee6c3e81af847a68338a93876c03d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193978"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Crear una aplicación de OpenGL ES en iOS y Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cuando se instala la opción Visual C++ para desarrollo móvil multiplataforma, puede crear soluciones de Visual Studio y proyectos de aplicaciones para iOS y Android que comparten código común. Este tema le guía a través de una plantilla de solución que crea una aplicación iOS simple y una aplicación Android Native Activity. Las aplicaciones tienen código de C++ en común que usa OpenGL ES para mostrar el mismo cubo giratorio animado en cada plataforma. OpenGL ES (OpenGL para sistemas incrustados o GLES) es una API de gráficos 2D y 3D compatible con muchos dispositivos móviles.  
  
 [Requisitos](#req)   
 [Crear un nuevo proyecto de aplicación OpenGLES](#Create)   
 [Compilar y ejecutar la aplicación Android](#BuildAndroid)   
 [Compilar y ejecutar la aplicación iOS](#BuildIOS)   
 [Personalizar las aplicaciones](#Customize)  
  
##  <a name="req"></a> Requisitos  
 Antes de crear una aplicación de OpenGL ES para iOS y Android, debe asegurarse de que cumple todos los requisitos del sistema. Debe instalar la opción Visual C++ para desarrollo móvil multiplataforma en Visual Studio 2015. Asegúrese de que las herramientas de terceros y SDK necesarios estén incluidos en la instalación y que está instalado el emulador de Visual Studio para Android. Para obtener más información e instrucciones detalladas, vea [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Para compilar y probar la aplicación de iOS, necesitará un equipo Mac configurado de acuerdo con las instrucciones de instalación. Para más información sobre la configuración para el desarrollo en iOS, vea [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
##  <a name="Create"></a> Crear un nuevo proyecto de aplicación OpenGLES  
 En este tutorial, primero debe crear un nuevo proyecto de aplicación de OpenGL ES y, a continuación, compilar y ejecutar la aplicación predeterminada en el emulador de Visual Studio para Android. A continuación, compile la aplicación para iOS y ejecute la aplicación en el simulador de iOS.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Abra Visual Studio. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , debajo de **Plantillas**, elija **Visual C++**, **Multiplataforma**y luego elija la plantilla **Aplicación de OpenGLES (Android, iOS)** .  
  
3.  Asigne a la aplicación un nombre como `MyOpenGLESApp`y luego elija **Aceptar**.  
  
     ![Nuevo proyecto de aplicación OpenGLES](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
     Visual Studio crea la solución nueva y abre el Explorador de soluciones.  
  
     ![MyOpenGLESApp en el Explorador de soluciones](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
 La nueva solución de aplicación de OpenGL ES incluye tres proyectos de biblioteca y dos proyectos de aplicación. La carpeta de bibliotecas incluye un proyecto de código compartido y dos proyectos para plataformas específicas que hacen referencia al código compartido:  
  
-   **MyOpenGLESApp.Android.NativeActivity** contiene las referencias y el código de adherencia que implementa su aplicación como Native Activity en Android. La implementación de los puntos de entrada desde el código de adherencia están en main.cpp, que incluye el código común compartido en MyOpenGLESApp.Shared. Los encabezados precompilados están en pch.h. Su proyecto de aplicación de Native Activity se compila en un archivo de biblioteca compartida (.so) que usa el proyecto MyOpenGLESApp.Android.Packaging.  
  
-   **MyOpenGLESApp.iOS.StaticLibrary** crea un archivo de biblioteca estática (.a) de iOS que contiene el código compartido en MyOpenGLESApp.Shared. Dicho archivo está vinculado a la aplicación creada por el proyecto MyOpenGLESApp.iOS.Application.  
  
-   **MyOpenGLESApp.Shared** contiene el código compartido que funciona en las distintas plataformas. Dicho código usa macros de preprocesador para la compilación condicional de código específico de plataforma. La referencia de proyecto toma el código compartido en MyOpenGLESApp.Android.NativeActivity y MyOpenGLESApp.iOS.StaticLibrary.  
  
 La solución tiene dos proyectos para compilar las aplicaciones para las plataformas iOS y Android:  
  
-   **MyOpenGLESApp.Android.Packaging** crea el archivo .apk para la implementación en un emulador o dispositivo Android. Este contiene los recursos y el archivo AndroidManifest.xml donde se establecen las propiedades del manifiesto. También contiene el archivo build.xml que controla el proceso de compilación de Ant. Se establece como proyecto de inicio de manera predeterminada para que se pueda implementar y ejecutar directamente desde Visual Studio.  
  
-   **MyOpenGLESApp.iOS.Application** contiene los recursos y el código de adherencia Objective-C para crear una aplicación de iOS que se vincula al código de biblioteca estática de C++ en MyOpenGLESApp.iOS.StaticLibrary. Este proyecto crea un paquete de compilación que Visual Studio y el agente remoto transfieren a su Mac. Cuando se compila este proyecto, Visual Studio envía los archivos y comandos para compilar e implementar su aplicación en Mac.  
  
##  <a name="BuildAndroid"></a> Compilar y ejecutar la aplicación Android  
 La solución creada por la plantilla establece la aplicación Android como proyecto predeterminado.  Puede compilar y ejecutar esta aplicación para comprobar la instalación y la configuración. Para realizar una prueba inicial, ejecute la aplicación en uno de los perfiles de dispositivo que instala el emulador de Visual Studio para Android. Si prefiere probar la aplicación en otro destino, cargue el emulador de destino o conecte el dispositivo a su equipo.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Para compilar y ejecutar la aplicación Android Native Activity  
  
1.  Si aún no está seleccionada, elija la opción **x86** en la lista desplegable **Plataformas de solución** .  
  
     ![Establecer la plataforma de soluciones en x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
     Use x86 como destino del emulador de Android para Windows. Si desea usar un dispositivo como destino, elija la plataforma de solución según el procesador del dispositivo. Si no se muestra la lista **Plataformas de solución** , elija **Plataformas de solución** de la lista **Agregar o quitar botones** y luego elija la plataforma.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual del proyecto MyOpenGLESApp.Android.Packaging y elija **Compilar**.  
  
     ![Compilar un proyecto de empaquetado de Android](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
     La ventana Salida muestra la salida del proceso de compilación de la biblioteca compartida de Android y la aplicación Android.  
  
     ![Resultados de compilación para proyectos Android](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3.  Elija como destino de la implementación uno de los perfiles de VS Emulator Android Phone (x86).  
  
     ![Seleccionar el destino de la implementación](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
     Si ha instalado otros emuladores o ha conectado un dispositivo Android, puede elegirlos en la lista desplegable de destinos de implementación. Para ejecutar la aplicación, la plataforma de solución compilada debe coincidir con la plataforma del dispositivo de destino.  
  
4.  Presione F5 para iniciar la depuración o Mayús+F5 para iniciar sin depurar.  
  
     Visual Studio inicia el emulador, que tarda varios segundos en cargarse e implementar el código. Este es el aspecto que tendrá su aplicación en el emulador de Visual Studio para Android.  
  
     ![Aplicación que se ejecuta en el emulador de Android](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
     Cuando la aplicación se inicia, puede establecer puntos de interrupción y usar el depurador para ver el código, examinar los locales e inspeccionar los valores.  
  
5.  Presione Mayús+F5 para detener la depuración.  
  
     El emulador es un proceso independiente que sigue ejecutándose. Puede editar, compilar e implementar el código varias veces en el mismo emulador. La aplicación aparece en la colección de aplicaciones en el emulador y puede iniciarse desde allí directamente.  
  
 La aplicación de Android Native Activity generada y los proyectos de biblioteca colocan el código C++ compartido en una biblioteca dinámica que incluye código de "adherencia" para interactuar con la plataforma Android. Esto significa que la mayoría del código de la aplicación está en la biblioteca y el manifiesto, recursos y las instrucciones de compilación están en el proyecto de empaquetado. El código compartido se llama desde main.cpp en el proyecto NativeActivity. Para más información sobre cómo programar Android Native Activity, vea la página Conceptos sobre Android Developer [NDK](https://developer.android.com/ndk/guides/concepts.html) .  
  
 Visual Studio compila proyectos de Android Native Activity mediante el uso de Android NDK, que usa Clang como conjunto de herramientas de la plataforma. Visual Studio asigna las propiedades del proyecto NativeActivity a los modificadores de línea de comandos y las opciones que se usan para compilar, vincular y depurar en la plataforma de destino. Para más información, abra el cuadro de diálogo **Páginas de propiedades** para el proyecto MyOpenGLESApp.Android.NativeActivity. Para más información sobre los modificadores de la línea de comandos, vea el [Manual del usuario del compilador de Clang](http://clang.llvm.org/docs/UsersManual.html).  
  
##  <a name="BuildIOS"></a> Compilar y ejecutar la aplicación iOS  
 El proyecto de aplicación iOS se crea y modifica en Visual Studio; sin embargo, debido a restricciones de licencia, debe compilarse e implementarse en un equipo MAC. Visual Studio se comunica con un agente remoto que se ejecuta en el equipo Mac para transferir archivos de proyecto y ejecutar la compilación, la implementación y los comandos de depuración. Debe instalar y configurar su equipo Mac y Visual Studio para comunicarse antes de generar la aplicación iOS. Para obtener instrucciones detalladas, vea [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Una vez que se ejecuta el agente remoto y Visual Studio se empareja con su equipo Mac, puede compilar y ejecutar la aplicación iOS para comprobar su instalación y configuración.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Para compilar y ejecutar la aplicación iOS  
  
1.  Compruebe que el agente remoto se está ejecutando en el equipo Mac y que Visual Studio está emparejado con el agente remoto. Para iniciar el agente remoto, abra una ventana de aplicación de terminal y escriba `vcremote`. Para más información, vea [Configurar el agente remoto en Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
     ![Ventana de terminal Mac que ejecuta vcremote](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2.  Si aún no está seleccionada, elija la opción **x86** en la lista desplegable **Plataformas de solución** .  
  
     ![Establecer la plataforma de soluciones en x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
     Use x 86 como destino del simulador de iOS. Si desea usar un dispositivo iOS como destino, elija la plataforma de solución según el procesador del dispositivo (normalmente un procesador ARM). Si no se muestra la lista **Plataformas de solución** , elija **Plataformas de solución** de la lista **Agregar o quitar botones** y luego elija la plataforma.  
  
3.  En el Explorador de soluciones, abra el menú contextual del proyecto MyOpenGLESApp.iOS.Application y elija **Compilar**.  
  
     ![Compilar un proyecto de aplicación para iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
     La ventana Salida muestra la salida del proceso de compilación de la biblioteca estática de iOS y la aplicación iOS. En el equipo Mac, la ventana de terminal que ejecuta el agente remoto muestra el comando y la actividad de transferencia de archivo.  
  
     En el equipo Mac, es posible que se le pida que acepte una solicitud de firma de código. Seleccione Permitir para continuar.  
  
4.  Elija **Simulador de iOS** en la barra de herramientas para ejecutar la aplicación en el simulador de iOS en el equipo Mac. El simulador puede tardar unos instantes en iniciarse. Puede que tenga que poner el simulador en primer plano en el equipo Mac para ver el resultado.  
  
     ![Aplicación que se ejecuta en el simulador de iOS](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
     Cuando la aplicación se inicia, puede establecer puntos de interrupción y usar el depurador de Visual Studio para examinar locales, ver la pila de llamadas e inspeccionar los valores.  
  
     ![Depurador en un punto de interrupción en una aplicación para iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5.  Presione Mayús+F5 para detener la depuración.  
  
     El simulador de iOS es un proceso independiente que sigue ejecutándose en su equipo Mac. Puede editar, compilar e implementar el código varias veces en el mismo simulador de iOS. También puede ejecutar el código directamente en el simulador después de que se haya implementado.  
  
 Los proyectos de biblioteca y aplicación iOS generados colocan el código C++ en una biblioteca estática que implementa solo el código compartido. La mayoría del código de aplicación está en el proyecto de aplicación. Las llamadas al código de biblioteca compartida de este proyecto de plantilla se realizan en el archivo GameViewController.m. Para compilar la aplicación iOS, Visual Studio usa el conjunto de herramientas de la plataforma Xcode, que requiere comunicación con un cliente remoto que se ejecuta en un equipo MAC.  
  
 Visual Studio transfiere los archivos del proyecto y envía comandos al cliente remoto para compilar la aplicación mediante Xcode. El cliente remoto envía información sobre el estado de la compilación de nuevo a Visual Studio. Cuando la aplicación se ha compilado correctamente, puede usar Visual Studio para enviar comandos para la ejecución y depurar la aplicación. El depurador de Visual Studio controla la aplicación en ejecución en el simulador de iOS que, a su vez, se ejecuta en el equipo Mac o en un dispositivo iOS adjunto. Visual Studio asigna las propiedades del proyecto StaticLibrary a los modificadores de línea de comandos y las opciones que se usan para compilar, vincular y depurar en la plataforma de iOS de destino. Para obtener detalles de las opciones de línea de comandos del compilador, abra el cuadro de diálogo **Páginas de propiedades** del proyecto MyOpenGLESApp.iOS.StaticLibrary.  
  
##  <a name="Customize"></a> Personalizar las aplicaciones  
 Puede modificar el código de C++ compartido para agregar o cambiar la funcionalidad común. Debe cambiar las llamadas al código compartido en los proyectos MyOpenGLESApp.Android.NativeActivity y MyOpenGLESApp.iOS.Application para que coincidan. Puede usar macros de preprocesador para especificar secciones específicas de la plataforma en el código común. La macro de preprocesador `__ANDROID__` está predefinida al compilar para Android. La macro de preprocesador `__APPLE__` está predefinida al compilar para iOS.  
  
 Para ver IntelliSense para una plataforma de proyecto determinado, elija el proyecto en la lista desplegable de modificador de contexto en la barra de navegación de la parte superior de la ventana del editor.  
  
 ![Menú desplegable del conmutador de contextos de proyecto en el Editor](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Los problemas de IntelliSense en el proyecto actual se marcan con una línea roja ondulada. Los problemas de otros proyectos se marcan con una línea ondulada de color púrpura. De forma predeterminada, Visual Studio no admite el código en colores o IntelliSense para los archivos Java u Objective-C. Sin embargo, puede modificar los archivos de origen y cambiar los recursos para establecer el nombre de la aplicación, el icono y otros detalles de implementación.

