---
title: Instalar Visual C++ para desarrollo móvil multiplataforma | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: cd8f99ffdba144d475b3d68d7509b57ad7ea4e3c
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281110"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Instalación del desarrollo móvil multiplataforma con C++

Puede usar C++ en Visual Studio para compilar aplicaciones de escritorio de Windows, aplicaciones de la plataforma Universal de Windows (UWP), aplicaciones de Linux y, ahora, aplicaciones para iOS y Android. La carga de trabajo de **Desarrollo móvil con C++** es un conjunto de componentes de Visual Studio que incluye plantillas multiplataforma para iOS, Android y UWP Visual Studio. Instala los SDK y las herramientas multiplataforma y que necesita para comenzar a trabajar rápidamente sin tener que buscarlos, descargarlos y configurarlos usted mismo. Puede usar estas herramientas en Visual Studio para crear, editar, depurar y probar proyectos multiplataforma fácilmente. En este tema se describe cómo instalar las herramientas y el software de terceros que se necesitan para desarrollar aplicaciones multiplataforma en C++ con Visual Studio. Para obtener información general, vea [Desarrollo móvil multiplataforma de Visual C++](https://go.microsoft.com/fwlink/p/?LinkId=536383).

## <a name="requirements"></a>Requisitos

- Para obtener información sobre los requisitos de instalación, vea [Visual Studio Product Family System Requirements](/visualstudio/productinfo/vs2017-system-requirements-vs) (Requisitos del sistema de la familia de productos de Visual Studio).

   > [!IMPORTANT]
   > Si usa Windows 7 o Windows Server 2008 R2, puede desarrollar código para aplicaciones de escritorio de Windows, aplicaciones y bibliotecas de Android Native Activity, así como aplicaciones y bibliotecas de código para iOS, pero no aplicaciones de UWP ni de Windows Phone.

Existen algunos requisitos adicionales para la compilación de aplicaciones para plataformas de dispositivo específicas:

- Los emuladores de Windows Phone y el emulador de Microsoft Visual Studio para Android requieren un equipo que pueda ejecutar Hyper-V. Debe habilitarse la característica de Hyper-V en Windows antes de poder instalar y ejecutar los emuladores. Para más información, vea los [requisitos del sistema](system-requirements-for-the-visual-studio-emulator-for-android.md) del emulador.

- Los emuladores de Android x86 que vienen con el SDK de Android funcionan mejor en equipos que pueden ejecutar el controlador HAXM de Intel. Este controlador requiere un procesador Intel x64 compatible con VT-x y Execute Disable Bit. Para más información, vea [Intel® Hardware Accelerated Execution Manager (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- La compilación de código para iOS requiere un ID de Apple, una cuenta del programa para desarrolladores de iOS y un equipo Mac que permita la ejecución de [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) versión 6 o versiones posteriores en OS X Mavericks (versión 10.9 o versiones posteriores). Para obtener un vínculo a los pasos de instalación, vea [Instalar las herramientas para iOS](#install-tools-for-ios).

## <a name="get-the-tools"></a>Obtener las herramientas

Desarrollo móvil con C++ está disponible en las ediciones Community, Professional y Enterprise de Visual Studio. Para obtener Visual Studio, vaya a la página [Descargas de Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=517106). Las herramientas de desarrollo móvil multiplataforma están disponibles a partir de Visual Studio 2015 Update 2 o posterior.

## <a name="install-the-tools"></a>Instalar las herramientas

El Instalador de Visual Studio para Visual Studio 2017 incluye una carga de trabajo **Desarrollo móvil con C++** que instala las herramientas, las plantillas y los componentes de lenguaje C++ que se requieren para el desarrollo de iOS y Android en Visual Studio 2015. Instala los conjuntos de herramientas de GCC y Clang necesarios para las compilaciones y depuraciones en Android, así como los componentes para la comunicación con un equipo Mac para el desarrollo de iOS. También instala todas las herramientas de terceros y los kits de desarrollo de software necesarios para admitir el desarrollo de aplicaciones iOS y Android. La mayoría de estas herramientas de terceros son aplicaciones de código abierto necesarias para la compatibilidad con la plataforma Android.

- El kit de desarrollo nativo de Android (NDK) es necesario para compilar el código de C++ destinado a la plataforma Android.

- El SDK de Android, Apache Ant y el kit de desarrollo para Java SE son necesarios para el proceso de compilación de Android.

- Intel Hardware Accelerated Execution Manager y Google Android Emulator son componentes opcionales, pero recomendados. Puede desarrollar y depurar directamente en un dispositivo Android, pero a menudo resulta más fácil usar un emulador en el escritorio para la depuración. Microsoft también ofrece un Emulador de Visual Studio para Android que puede instalarse por separado.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>Para instalar la carga de trabajo Desarrollo móvil con C++ en Visual Studio 2017

1. Ejecute el **instalador de Visual Studio** desde el menú **Iniciar**.

1. Si ya ha instalado Visual Studio, elija el botón **Modificar** de la versión instalada de Visual Studio que quiere modificar. En caso contrario, elija **Instalar** para instalar Visual Studio.

1. Con la pestaña **Cargas de trabajo** seleccionada, desplácese hacia abajo y seleccione la carga de trabajo **Desarrollo móvil con C++** del Instalador de Visual Studio. Cuando se selecciona esta carga de trabajo, se seleccionan también otros componentes necesarios para el desarrollo con C++. También puede elegir otras cargas de trabajo y componentes individuales para instalarlos al mismo tiempo. Para compilar código multiplataforma que también tenga como destino UWP, seleccione la carga de trabajo **Desarrollo de la plataforma universal de Windows**.

1. En el panel **Detalles de la instalación**, expanda **Desarrollo móvil con C++**. En la sección **Opcional**, puede elegir otras versiones del NDK, Google Android Emulator, Intel Hardware Accelerated Execution Manager y la herramienta de aceleración de compilación IncrediBuild.

1. De manera predeterminada, la carga de trabajo incluye uno o más componentes de instalación de Android SDK. Hay disponibles otras versiones de Android SDK. Para agregar una a la instalación, elija la pestaña **Componentes individuales** y luego desplácese hacia abajo hasta la sección **SDK, bibliotecas y marcos** para realizar la selección.

1. Elija el botón **Modificar** o **Instalar** para instalar la carga de trabajo **Desarrollo móvil con C++** y los demás componentes opcionales y cargas de trabajo seleccionados.

   Cuando se complete la instalación, cierre el programa de instalación y después reinicie el equipo. Algunas acciones de instalación para los componentes de terceros surtirán efecto cuando se reinicie el equipo.

   > [!IMPORTANT]
   > Debe reiniciarlo para asegurarse de que todo se ha instalado correctamente.

1. Abra Visual Studio. Si es la primera vez que ejecuta Visual Studio, puede tardar algún tiempo en configurar e iniciar sesión. Cuando Visual Studio esté listo, busque las actualizaciones e instálelas.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Para instalar el componente Desarrollo móvil y herramientas de terceros en Visual Studio 2015

Si usa Visual Studio 2015, su instalador incluye una opción para instalar Visual C++ para desarrollo móvil multiplataforma, que instala las herramientas, las plantillas y los componentes de lenguaje C++ que se requieren en Visual Studio 2015.

1. Ejecute el Instalador de Visual Studio 2015. Para instalar componentes opcionales, elija **Personalizado** como tipo de instalación. Elija **Siguiente** para seleccionar los componentes opcionales que desea instalar.

1. En **Seleccionar características**, expanda **Desarrollo móvil multiplataforma** y seleccione **Desarrollo móvil de Visual C++**.

   ![Seleccione Desarrollo móvil de Visual C++](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   De forma predeterminada, cuando se selecciona **Desarrollo móvil de Visual C++**, la opción **Lenguajes de programación** se establece para instalar **Visual C++** y las opciones **Kits de desarrollo de software y herramientas comunes** se establecen para instalar los componentes de terceros necesarios. Puede elegir componentes adicionales si los necesita. De forma predeterminada, también se selecciona el **Emulador de Microsoft Visual Studio para Android**. Los componentes que ya están instalados aparecen inactivos en la lista.

   Para compilar aplicaciones universales de Windows y compartir código entre ellas y los proyectos de iOS y Android, en **Seleccionar características**, expanda **Desarrollo de Web y de Windows** y active **Herramientas de desarrollo de aplicaciones universales de Windows**. Si no planea compilar aplicaciones universales de Windows, puede omitir esta opción.

   Elija **Siguiente** para continuar.

1. Los componentes de terceros tienen sus propios términos de licencia. Puede ver los términos de licencia eligiendo el vínculo **Términos de licencia** situado junto a cada componente. Haga clic en **Instalar** para agregar los componentes e instalar Visual Studio y Visual C++ para desarrollo móvil multiplataforma.

1. Cuando se complete la instalación, cierre el programa de instalación y después reinicie el equipo. Algunas acciones de instalación para los componentes de terceros surtirán efecto cuando se reinicie el equipo.

   > [!IMPORTANT]
   > Debe reiniciarlo para asegurarse de que todo se ha instalado correctamente.

   Si no se pudo instalar el componente Emulador de Microsoft Visual Studio para Android, es posible que Hyper-V no esté habilitado en el equipo. Use la aplicación del Panel de Control **Activar o desactivar las características de Windows** para habilitar Hyper-V y, después, ejecute de nuevo el programa de instalación de Visual Studio.

   > [!NOTE]
   > Si su equipo o su versión de Windows no es compatible con Hyper-V, no puede usar el componente Emulador de Microsoft Visual Studio para Android. Windows Home Edition no es compatible con Hyper-V.

1. Abra Visual Studio. Si es la primera vez que ejecuta Visual Studio, puede tardar algún tiempo en configurar e iniciar sesión. Cuando Visual Studio esté listo, en el menú **Herramientas** , seleccione **Extensiones y actualizaciones**, **Actualizaciones**. Si hay actualizaciones disponibles de Visual Studio para Visual C++ para el desarrollo móvil multiplataforma o para el Emulador de Microsoft Visual Studio para Android, instálelas.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Puede usar Visual C++ para desarrollo móvil multiplataforma para editar, depurar e implementar código de iOS en el simulador de iOS o en un dispositivo de iOS, aunque, debido a las restricciones de licencia, el código se debe compilar de manera remota en un equipo Mac. Para compilar y ejecutar aplicaciones de iOS con Visual Studio, debe instalar y configurar el agente remoto en el equipo Mac. Para obtener instrucciones de instalación detalladas, información sobre opciones de configuración y requisitos previos, vea [Install And Configure Tools to Build using iOS](install-and-configure-tools-to-build-using-ios.md). Si no va a compilar aplicaciones para iOS, puede omitir este paso.

## <a name="install-or-update-dependencies-manually"></a>Instalar o actualizar manualmente las dependencias

Si decide no instalar una o más dependencias de terceros mediante el Instalador de Visual Studio al instalar la carga de trabajo **Desarrollo móvil con C++** (o, en Visual Studio 2015, la opción Desarrollo móvil de Visual C++), puede instalarlas más adelante siguiendo los pasos que se describen en [Instalar las herramientas](#install-the-tools). El Instalador de Visual Studio se actualiza periódicamente para instalar los componentes de terceros más recientes. Puede usarlo para instalar los SDK y los NDK actualizados. También puede instalarlas o actualizarlas independientemente de Visual Studio.

> [!CAUTION]
> Las dependencias se pueden instalar en cualquier orden, a excepción de Java. Debe instalar y configurar el JDK antes de instalar Android SDK.

Lea la siguiente información y use estos vínculos para instalar las dependencias manualmente.

- [Kit de desarrollo de Java SE](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   De manera predeterminada, el instalador coloca las herramientas de Java en C:\Archivos de programa (x86)\Java.

- [SDK de Android](https://developer.android.com/sdk/index.html#command-tools)

   Durante la instalación, actualice las API según se recomienda. Asegúrese de que esté instalado por lo menos el SDK para Android 5.0 Lollipop (nivel de API 21). De manera predeterminada, el instalador coloca el SDK de Android en C:\Archivos de programa (x86)\Android\android-sdk.

   Puede volver a ejecutar la aplicación de administrador de SDK en el directorio del SDK de Android para actualizar el SDK e instalar herramientas opcionales y niveles de API adicionales. Las actualizaciones pueden no instalarse correctamente si no usa la opción **Ejecutar como administrador** para ejecutar la aplicación SDK Manager. Si tiene problemas para crear una aplicación Android, compruebe el SDK Manager por si hay actualizaciones para los SDK instalados.

   Para usar algunos de los emuladores de Android que vienen con el SDK de Android, debe instalar los controladores HAXM de Intel opcionales. Es posible que tenga que quitar la característica Hyper-V de Windows para instalar los controladores HAXM de Intel correctamente. Debe restaurar la característica Hyper-V para usar los emuladores de Windows Phone y el emulador de Microsoft Visual Studio para Android. Para más información, vea [Aceleración de hardware de Android Emulator](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [NDK de Android](https://developer.android.com/tools/sdk/ndk/index.html)

   De forma predeterminada, el instalador coloca el NDK Android en C:\ProgramData\Microsoft\AndroidNDK. Puede volver a descargar e instalar el NDK de Android para actualizar la instalación del NDK.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   De manera predeterminada, el instalador coloca Apache Ant en C:\Archivos de programa (x86)\Microsoft Visual Studio 14.0\Apps.

- [Emulador de Microsoft Visual Studio para Android](https://aka.ms/vscomemudownload)

   El Emulador de Microsoft Visual Studio para Android es un emulador opcional útil para probar y depurar el código. Después del lanzamiento del Emulador de Visual Studio para Android, Google actualizó Android Emulator para utilizar la aceleración de hardware a través del HAXM de Intel. Se recomienda usar el emulador acelerado de Google cuando sea posible, ya que ofrece acceso a Google Play Services y las imágenes del sistema operativo Android más recientes.

En la mayoría de los casos, Visual Studio puede detectar las configuraciones del software de terceros que haya instalado y mantiene las rutas de instalación en variables de entorno internas. Puede reemplazar las rutas de acceso predeterminadas de estas herramientas de desarrollo multiplataforma en el IDE de Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Para establecer las rutas de acceso para las herramientas de terceros

1. En la barra de menús de Visual Studio, seleccione **Herramientas** > **Opciones**.

1. En el cuadro de diálogo **Opciones**, expanda **Multiplataforma** > **C++** > **Android**.

   ![Opciones de ruta de acceso de la herramienta Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Para cambiar la ruta de acceso que usa una herramienta, active la casilla situada junto a la ruta de acceso y edite la ruta de acceso de la carpeta en el cuadro de texto. También puede usar el botón Examinar (**...**) para abrir el cuadro de diálogo **Seleccionar ubicación** para seleccionar la carpeta.

1. Elija **Aceptar** para guardar las ubicaciones de carpeta de la herramienta personalizada.

## <a name="see-also"></a>Vea también

- [Instalar y configurar herramientas para compilar con iOS](install-and-configure-tools-to-build-using-ios.md)
- [Desarrollo móvil multiplataforma de Visual Studio C++](https://go.microsoft.com/fwlink/p/?LinkId=536383)
