---
title: Crear una aplicación de OpenGL ES en iOS y Android | Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b235576f21b63a7be4170f36abf58bed9fab9df3
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923901"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Crear una aplicación de OpenGL ES en Android e iOS

Puede crear soluciones y proyectos de Visual Studio para aplicaciones iOS y Android que comparten código común. Este articulo le guía a través de una plantilla de solución que crea una aplicación iOS simple y una aplicación Android Native Activity. Las aplicaciones tienen código de C++ en común que usa OpenGL ES para mostrar el mismo cubo giratorio animado en cada plataforma. OpenGL ES (OpenGL para sistemas incrustados o GLES) es una API de gráficos 2D y 3D compatible con muchos dispositivos móviles.

## <a name="requirements"></a>Requisitos

Antes de crear una aplicación de OpenGL ES para iOS y Android, asegúrese de que cumple todos los requisitos del sistema. Si aún no lo ha hecho, instale la carga de trabajo Desarrollo móvil con C++ en el Instalador de Visual Studio. Para compilar para iOS, incluya las herramientas de desarrollo de iOS para C++ opcionales. Para compilar para Android, instale las herramientas de desarrollo de Android para C++ y las herramientas de terceros necesarias: Android NDK, Apache Ant, Google Android Emulator e Intel Hardware Accelerated Execution Manager. A continuación, configure Intel HAXM y Android Emulator para que se ejecuten en su sistema. Para más información e instrucciones detalladas, consulte [Instalar Visual C++ para el desarrollo móvil multiplataforma](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Para compilar y probar la aplicación de iOS, necesitará un equipo Mac configurado de acuerdo con las instrucciones de instalación. Para más información sobre la configuración para el desarrollo en iOS, consulte [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="create-a-new-opengles-application-project"></a>Crear un nuevo proyecto de aplicación OpenGLES

En este tutorial, primero debe crear un nuevo proyecto de aplicación de OpenGL ES y, a continuación, compilar y ejecutar la aplicación predeterminada en el emulador de Visual Studio para Android. A continuación, compile la aplicación para iOS y ejecute la aplicación en un dispositivo de iOS.

1. En Visual Studio, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, debajo de **Plantillas**, elija **Visual C++**  > **Multiplataforma** y luego elija la plantilla **Aplicación de OpenGLES(Android, iOS)** .

1. Ponga a la aplicación un nombre como `MyOpenGLESApp`y luego elija **Aceptar**.

   ![Nuevo proyecto de aplicación OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio crea la solución nueva y abre el Explorador de soluciones.

   ![MyOpenGLESApp en el Explorador de soluciones](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

   La nueva solución de aplicación de OpenGL ES incluye tres proyectos de biblioteca y dos proyectos de aplicación. La carpeta de bibliotecas incluye un proyecto de código compartido y dos proyectos para plataformas específicas que hacen referencia al código compartido:

- `MyOpenGLESApp.Android.NativeActivity` contiene las referencias y el código de adherencia que implementa su aplicación como Native Activity en Android. Los puntos de entrada desde el código de adherencia se implementan en *main.cpp*, que incluye el código común compartido en `MyOpenGLESApp.Shared`. Los encabezados precompilados están en *pch.h*. Su proyecto de aplicación de Native Activity se compila en un archivo de biblioteca compartida ( *.so*) que selecciona el proyecto `MyOpenGLESApp.Android.Packaging`.

- `MyOpenGLESApp.iOS.StaticLibrary` crea un archivo de biblioteca estática de iOS ( *.a*) que contiene el código compartido en `MyOpenGLESApp.Shared`. Este archivo está vinculado a la aplicación creada por el proyecto `MyOpenGLESApp.iOS.Application`.

- `MyOpenGLESApp.Shared` contiene el código compartido que funciona en las distintas plataformas. Dicho código usa macros de preprocesador para la compilación condicional de código específico de plataforma. La referencia de proyecto selecciona el código compartido en `MyOpenGLESApp.Android.NativeActivity` y `MyOpenGLESApp.iOS.StaticLibrary`.

La solución tiene dos proyectos para compilar las aplicaciones para las plataformas iOS y Android:

- `MyOpenGLESApp.Android.Packaging` crea el archivo *.apk* para la implementación en un dispositivo o emulador Android. Este archivo contiene los recursos y el archivo AndroidManifest.xml donde se establecen las propiedades del manifiesto. También contiene el archivo *build.xml* que controla el proceso de compilación de Ant. Se establece como proyecto de inicio de manera predeterminada para que se pueda implementar y ejecutar directamente desde Visual Studio.

- **MyOpenGLESApp.iOS.Application** contiene los recursos y el código de adherencia Objective-C para crear una aplicación de iOS que se vincula al código de biblioteca estática de C++ en `MyOpenGLESApp.iOS.StaticLibrary`. Este proyecto crea un paquete de compilación que Visual Studio y el agente remoto transfieren a su Mac. Cuando se compila este proyecto, Visual Studio envía los archivos y comandos para compilar e implementar su aplicación en Mac.

## <a name="build-and-run-the-android-app"></a>Compilar y ejecutar la aplicación Android

La solución creada por la plantilla establece la aplicación Android como proyecto predeterminado.  Puede compilar y ejecutar esta aplicación para comprobar la instalación y la configuración. Para realizar una prueba inicial, ejecute la aplicación en uno de los perfiles de dispositivo que instala el emulador para Android. Si prefiere probar la aplicación en otro destino, cargue el emulador de destino o conecte el dispositivo a su equipo.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Para compilar y ejecutar la aplicación Android Native Activity

1. Si aún no está seleccionada, elija la opción **x86** en la lista desplegable **Plataformas de solución**.

   ![Establecer la plataforma de soluciones en x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Use x 86 como destino del emulador. Si desea usar un dispositivo como destino, elija la plataforma de solución según el procesador del dispositivo. Si no se muestra la lista **Plataformas de solución** , seleccione **Plataformas de solución** de la lista **Agregar o quitar botones** y luego seleccione la plataforma.

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto `MyOpenGLESApp.Android.Packaging` y, después, seleccione **Compilar**.

   ![Compilar un proyecto de empaquetado de Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   La ventana Salida muestra la salida del proceso de compilación de la biblioteca compartida de Android y la aplicación Android.

   ![Resultados de compilación para proyectos Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Elija uno de los perfiles del dispositivo Android emulado como destino de la implementación.

   ![Seleccionar el destino de la implementación](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Si ha instalado otros emuladores o ha conectado un dispositivo Android, puede elegirlos en la lista desplegable de destinos de implementación. Para ejecutar la aplicación, la plataforma de solución compilada debe coincidir con la plataforma del dispositivo de destino.

1. Presione F5 para iniciar la depuración o Mayús+F5 para iniciar sin depurar.

   Visual Studio inicia el emulador, que tarda varios segundos en cargarse e implementar el código. Así es como aparece la aplicación en el emulador:

   ![Aplicación que se ejecuta en el emulador de Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Cuando la aplicación se inicia, puede establecer puntos de interrupción y usar el depurador para ver el código, examinar los locales e inspeccionar los valores.

1. Presione **MAYÚS**+**F5** para detener la depuración.

   El emulador es un proceso independiente que sigue ejecutándose. Puede editar, compilar e implementar el código varias veces en el mismo emulador. La aplicación aparece en la colección de aplicaciones en el emulador y puede iniciarse desde allí directamente.

   La aplicación de Android Native Activity generada y los proyectos de biblioteca colocan el código C++ compartido en una biblioteca dinámica que incluye código de "adherencia" para interactuar con la plataforma Android. La mayoría del código de la aplicación está en la biblioteca, y el manifiesto, los recursos y las instrucciones de compilación están en el proyecto de empaquetado. El código compartido se llama desde main.cpp en el proyecto NativeActivity. Para más información sobre cómo programar Android Native Activity, vea la página Conceptos sobre Android Developer [NDK](https://developer.android.com/ndk/guides/concepts.html) .

   Visual Studio compila proyectos de Android Native Activity mediante el uso de Android NDK, que usa Clang como conjunto de herramientas de la plataforma. Visual Studio asigna las propiedades del proyecto NativeActivity a las opciones que se usan para compilar, vincular y depurar en la plataforma de destino. Para más información, abra el cuadro de diálogo **Páginas de propiedades** para el proyecto MyOpenGLESApp.Android.NativeActivity. Para obtener más información sobre los modificadores de la línea de comandos, vea el [manual del usuario del compilador de Clang](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Compilación y ejecución de la aplicación iOS en un dispositivo iOS

El proyecto de aplicación iOS se crea y modifica en Visual Studio; sin embargo, debido a restricciones de licencia, debe compilarse e implementarse en un equipo MAC. Visual Studio se comunica con un agente remoto que se ejecuta en el equipo Mac para transferir archivos de proyecto y ejecutar la compilación, la implementación y los comandos de depuración. Instale y configure su equipo Mac y Visual Studio para comunicarse antes de generar la aplicación iOS. Para obtener instrucciones detalladas, consulte [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Una vez que se ejecuta el agente remoto en su equipo Mac y se empareja con Visual Studio, puede compilar y ejecutar la aplicación iOS para comprobar su instalación y configuración.

Para implementar una aplicación iOS en un dispositivo iOS, debe configurar la firma automática de Xcode en el equipo Mac. La firma automática administra automáticamente la firma de aplicaciones y crea un perfil de aprovisionamiento para firmar una compilación de la aplicación.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Para configurar la firma automática en Xcode

1. Si aún no lo ha hecho, instale la versión 10.2.1 o posterior de [Xcode](https://developer.apple.com/xcode/downloads/) en el equipo Mac.

1. Abra la aplicación de Xcode en el equipo Mac.

1. Cree un nuevo proyecto **Aplicación de vista única** de Xcode. Rellene los campos obligatorios durante la creación del proyecto. Los valores pueden ser arbitrarios, ya que el proyecto solo se usa para crear un perfil de aprovisionamiento que se utilizará posteriormente para firmar una compilación de la aplicación.

1. Agregue el ID de Apple inscrito en una cuenta del [Apple Developer Program](https://developer.apple.com/programs/) a Xcode. El ID de Apple se utiliza como identidad de firma para firmar las aplicaciones. Para agregar la identidad de firma en Xcode, abra el menú **Xcode** y elija **Preferencias**. Seleccione **Cuentas** y haga clic en el botón Agregar (+) para agregar el ID de Apple. Vea [Add your Apple ID account](https://help.apple.com/xcode/mac/current/#/devaf282080a) (Agregar una cuenta de ID de Apple) para ver instrucciones detalladas.

1. Desde la configuración de "General" del proyecto DE Xcode, cambie el valor de **	Identificador del lote** a `com.<NameOfVSProject>`, donde `<NameOfVSProject>` es el mismo nombre que el proyecto de solución de Visual Studio que creó. Por ejemplo, si ha creado un proyecto denominado `MyOpenGLESApp` en Visual Studio, establezca **	Identificador del lote** en `com.MyOpenGLESApp`.

   ![Identificador del lote de Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Para habilitar la firma automática, active Automatically manage signing** (Administrar la firma automáticamente).

   ![Firma automática de Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Seleccione el nombre de equipo del ID de Apple que agregó como **equipo** de desarrollo.

   ![Equipo de Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Para compilar y ejecutar la aplicación iOS en un dispositivo iOS

1. Ejecute el agente remoto en el equipo Mac y compruebe que Visual Studio está emparejado con el agente remoto. Para iniciar el agente remoto, abra una ventana de aplicación de terminal y escriba `vcremote`. Para más información, vea [Configurar el agente remoto en Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Ventana de terminal Mac que ejecuta vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Asocie un dispositivo iOS al equipo Mac. Cuando asocie el dispositivo a un equipo por primera vez, se le preguntará si confía en que el equipo acceda al dispositivo. Permita que el dispositivo confíe en el equipo Mac.

1. En Visual Studio, si aún no está seleccionado, elija la plataforma de solución de la lista desplegable **Plataformas de solución** en función del procesador del dispositivo. En este ejemplo, es un procesador **ARM64**.

   ![Establecimiento de la plataforma de solución en ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. En el Explorador de soluciones, abra el menú contextual del proyecto MyOpenGLESApp.iOS.Application y elija **Descargar proyecto** para descargar el proyecto.

1. De nuevo, abra el menú contextual para el proyecto MyOpenGLESApp.iOS.Application descargado y elija **Edit project.pbxproj** (Editar project.pbxproj) para editar el archivo de proyecto. En el archivo `project.pbxproj`, busque el atributo `buildSettings` y agregue `DEVELOPMENT_TEAM` mediante su ID de equipo de Apple. La captura de pantalla siguiente muestra un valor de ejemplo de `123456ABC` para el ID de equipo de Apple. Puede encontrar el valor de su ID de equipo de Apple en Xcode. Vaya a **Configuración de compilación** y mantenga el puntero sobre el nombre del equipo de desarrollo para mostrar la información sobre herramientas. La información sobre herramientas muestra el identificador de equipo.

   ![Establecimiento del equipo de desarrollo](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Cierre el archivo `project.pbxproj`, abra a continuación el menú contextual para el proyecto MyOpenGLESApp.iOS.Application descargado y elija **Volver a cargar el proyecto** para volver a cargar el proyecto.

1. Ahora, compile el proyecto MyOpenGLESApp.iOS.Application; para ello, abra el menú contextual del proyecto y elija **Compilar**.

   ![Compilar un proyecto de aplicación para iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   La ventana Salida muestra la salida del proceso de compilación de la biblioteca estática de iOS y la aplicación iOS. En el equipo Mac, la ventana de terminal que ejecuta el agente remoto muestra el comando y la actividad de transferencia de archivo.

   En el equipo Mac, se le pedirá que permita que la firma de código tenga acceso a la cadena de claves. Seleccione **Permitir** para continuar.

1. Elija el dispositivo iOS en la barra de herramientas para ejecutar la aplicación en el dispositivo asociado a su equipo Mac. Si no se inicia la aplicación, compruebe que el dispositivo concede permiso para que la aplicación implementada se ejecute en el dispositivo. Para configurar este permiso, vaya a **Configuración** > **General** > **Administración de dispositivos** en el dispositivo. Seleccione la cuenta de la aplicación de desarrolladores, confíe en ella y verifique la aplicación. Intente volver a ejecutar la aplicación desde Visual Studio.

   ![Aplicación iOS en dispositivos iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")

   Cuando la aplicación se inicia, puede establecer puntos de interrupción y usar el depurador de Visual Studio para examinar locales, ver la pila de llamadas e inspeccionar los valores.

   ![Depurador en un punto de interrupción en una aplicación para iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Presione **MAYÚS**+**F5** para detener la depuración.

   Los proyectos de biblioteca y aplicación iOS generados colocan el código C++ en una biblioteca estática que implementa solo el código compartido. La mayoría del código de aplicación está en el proyecto `Application`. Las llamadas al código de biblioteca compartido de este proyecto de plantilla se realizan en el archivo *GameViewController.m*. Para compilar la aplicación iOS, Visual Studio usa el conjunto de herramientas de la plataforma Xcode, que requiere comunicación con un cliente remoto que se ejecuta en un equipo MAC.

   Visual Studio transfiere los archivos del proyecto y envía comandos al cliente remoto para compilar la aplicación mediante Xcode. El cliente remoto envía información sobre el estado de la compilación de nuevo a Visual Studio. Cuando la aplicación se ha compilado correctamente, puede usar Visual Studio para enviar comandos para la ejecución y depurar la aplicación. El depurador de Visual Studio controla la aplicación en ejecución en el dispositivo iOS asociado a su Mac. Visual Studio asigna las propiedades del proyecto StaticLibrary a las opciones que se usan para compilar, vincular y depurar en la plataforma iOS de destino. Para obtener detalles de las opciones de línea de comandos del compilador, abra el cuadro de diálogo **Páginas de propiedades** del proyecto MyOpenGLESApp.iOS.StaticLibrary.

## <a name="customize-your-apps"></a>Personalizar las aplicaciones

Puede modificar el código de C++ compartido para agregar o cambiar la funcionalidad común. Debe cambiar las llamadas al código compartido en los proyectos `MyOpenGLESApp.Android.NativeActivity` y `MyOpenGLESApp.iOS.Application` para que coincidan. Puede usar macros de preprocesador para especificar secciones específicas de la plataforma en el código común. La macro de preprocesador `__ANDROID__` está predefinida al compilar para Android. La macro de preprocesador `__APPLE__` está predefinida al compilar para iOS.

Para ver IntelliSense para una plataforma de proyecto determinado, elija el proyecto en la lista desplegable de modificador de contexto en la barra de navegación de la parte superior de la ventana del editor.

![Menú desplegable del conmutador de contextos de proyecto en el Editor](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

Los problemas de IntelliSense en el código que se utiliza por el proyecto actual se marcan con una línea roja ondulada. Los problemas de otros proyectos se marcan con una línea ondulada de color púrpura. Visual Studio no admite el código en colores o IntelliSense para los archivos Java u Objective-C. Sin embargo, puede modificar los archivos de origen y cambiar los recursos para establecer el nombre de la aplicación, el icono y otros detalles de implementación.
