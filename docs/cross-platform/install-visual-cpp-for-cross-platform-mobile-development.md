---
title: Instalación del desarrollo móvil multiplataforma con C++ | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 25bd88886b6bed447ec7d091543fccdb478db9c5
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588884"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Instalación del desarrollo móvil multiplataforma con C++

Puede usar C++ en Visual Studio para compilar aplicaciones de escritorio de Windows, aplicaciones de la plataforma Universal de Windows (UWP), aplicaciones de Linux y, ahora, aplicaciones para iOS y Android. La carga de trabajo de **Desarrollo móvil con C++** es un conjunto de componentes de Visual Studio que incluye plantillas multiplataforma para iOS, Android y UWP Visual Studio. Instala los SDK y las herramientas multiplataforma y que necesita para comenzar a trabajar rápidamente sin tener que buscarlos, descargarlos y configurarlos usted mismo. Puede usar estas herramientas en Visual Studio para crear, editar, depurar y probar proyectos multiplataforma fácilmente. En este artículo se describe cómo instalar las herramientas y el software de terceros que se necesitan para desarrollar aplicaciones multiplataforma en C++ con Visual Studio. Para obtener información general, vea [Desarrollo móvil multiplataforma de Visual C++](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/).

## <a name="requirements"></a>Requisitos

::: moniker range="vs-2017"

- Para obtener información sobre los requisitos de instalación, vea [Visual Studio Product Family System Requirements](/visualstudio/productinfo/vs2017-system-requirements-vs) (Requisitos del sistema de la familia de productos de Visual Studio).

   > [!IMPORTANT]
   > Si usa Windows 7 o Windows Server 2008 R2, puede desarrollar código para aplicaciones de escritorio de Windows, aplicaciones y bibliotecas native-activity para Android, así como aplicaciones y bibliotecas de código para iOS, pero no aplicaciones de UWP ni de Windows Store.

::: moniker-end
::: moniker range=">=vs-2019"

- Para obtener información sobre los requisitos de instalación, vea [Visual Studio Product Family System Requirements](/visualstudio/releases/2019/system-requirements) (Requisitos del sistema de la familia de productos de Visual Studio).

   > [!IMPORTANT]
   > Si usa Windows 7 o Windows Server 2008 R2, puede desarrollar código para aplicaciones de escritorio de Windows, aplicaciones y bibliotecas de Android Native Activity, así como aplicaciones y bibliotecas de código para iOS, pero no aplicaciones de UWP ni de Windows Phone.

::: moniker-end

Existen algunos requisitos adicionales para la compilación de aplicaciones para plataformas de dispositivo específicas:

- Los emuladores de Android x86 que se ofrecen con Android SDK funcionan mejor en equipos que pueden usar la aceleración de hardware, como por ejemplo Intel Hardware Accelerated Execution Manager (HAXM). Para más información, vea [Aceleración de hardware para el rendimiento del emulador (Hyper-V y HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- La compilación de código para iOS requiere un ID de Apple, una cuenta del programa para desarrolladores de iOS y un equipo Mac que permita la ejecución de [Xcode](https://developer.apple.com/xcode/) versión 10.2 o versiones posteriores en OS X Mavericks (versión 10.9 o versiones posteriores). Para obtener un vínculo a los pasos de instalación, vea [Instalar las herramientas para iOS](#install-tools-for-ios).

- Los emuladores de Windows Phone requieren un equipo que pueda ejecutar Hyper-V. Debe habilitarse la característica de Hyper-V en Windows antes de poder instalar y ejecutar los emuladores. Para obtener más información, vea los [requisitos del sistema](system-requirements-for-the-visual-studio-emulator-for-android.md)del emulador.

## <a name="get-the-tools"></a>Obtener las herramientas

Desarrollo móvil con C++ está disponible en las ediciones Community, Professional y Enterprise de Visual Studio. Para obtener Visual Studio, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/). Las herramientas de desarrollo móvil multiplataforma están disponibles a partir de Visual Studio 2015.

## <a name="install-the-tools"></a>Instalar las herramientas

El Instalador de Visual Studio incluye la carga de trabajo **Desarrollo móvil con C++** . Esta carga de trabajo instala las herramientas, las plantillas y los componentes necesarios del lenguaje C++ para el desarrollo de iOS y Android en Visual Studio. Incluye los conjuntos de herramientas de GCC y Clang necesarios para las compilaciones y depuraciones en Android, Android SDK y los componentes para la comunicación con un equipo Mac para el desarrollo de iOS. También instala todas las demás herramientas de terceros y los kits de desarrollo de software necesarios para admitir el desarrollo de aplicaciones iOS y Android. La mayoría de estas herramientas de terceros son aplicaciones de código abierto necesarias para la compatibilidad con la plataforma Android.

- El kit de desarrollo nativo de Android (NDK), Apache Ant, y las herramientas de desarrollo de Android en C++ son necesarios para compilar el código de C++ destinado a la plataforma Android.

- Intel Hardware Accelerated Execution Manager (HAXM) y Google Android Emulator son componentes opcionales, pero recomendados. (Los controladores de HAXM de Intel solo funcionan en procesadores de Intel y son incompatibles con algunas máquinas virtuales, incluido Hyper-V). Puede desarrollar y depurar directamente en un dispositivo Android, pero a menudo resulta más fácil usar un emulador en el escritorio para la depuración.

- Las herramientas de desarrollo de iOS en C++ son necesarias para compilar código de C++ destinado a la plataforma iOS.

> [!NOTE]
> Si usa Visual Studio 2015, consulte el artículo sobre la [instalación de Visual C++ para desarrollo móvil multiplataforma (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015).

### <a name="install-the-mobile-development-with-c-workload"></a>Instalación de la carga de trabajo Desarrollo móvil con C++

1. Ejecute el **instalador de Visual Studio** desde el menú **Iniciar**.

1. Si ya ha instalado Visual Studio, elija el botón **Modificar** de la versión instalada de Visual Studio que quiere modificar. En caso contrario, elija **Instalar** para instalar Visual Studio.

1. Con la pestaña **Cargas de trabajo** seleccionada, desplácese hacia abajo y seleccione la carga de trabajo **Desarrollo móvil con C++** del Instalador de Visual Studio. Cuando se selecciona esta carga de trabajo, se seleccionan también otros componentes necesarios para el desarrollo con C++. También puede elegir otras cargas de trabajo y componentes individuales para instalarlos al mismo tiempo. Para compilar código multiplataforma que también tenga como destino UWP, seleccione la carga de trabajo **Desarrollo de la plataforma universal de Windows**.

1. En el panel **Detalles de la instalación**, expanda **Desarrollo móvil con C++** . En la sección **Opcional**, puede elegir otras versiones del NDK, Google Android Emulator, Intel Hardware Accelerated Execution Manager y la herramienta de aceleración de compilación IncrediBuild.

1. De manera predeterminada, la carga de trabajo incluye uno o más componentes de instalación de Android SDK. Hay disponibles otras versiones de Android SDK. Para agregar una a la instalación, elija la pestaña **Componentes individuales** y luego desplácese hacia abajo hasta la sección **SDK, bibliotecas y marcos** para realizar la selección.

1. Elija el botón **Modificar** o **Instalar** para instalar la carga de trabajo **Desarrollo móvil con C++** y los demás componentes opcionales y cargas de trabajo seleccionados.

   Cuando se complete la instalación, cierre el programa de instalación y después reinicie el equipo. Algunas acciones de instalación para los componentes de terceros surtirán efecto cuando se reinicie el equipo.

   > [!IMPORTANT]
   > Debe reiniciarlo para asegurarse de que todo se ha instalado correctamente.

1. Abra Visual Studio.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Puede usar Visual Studio para editar, depurar e implementar código de iOS en el simulador de iOS o en un dispositivo iOS. Sin embargo, debido a las restricciones de licencia, el código debe compilarse de forma remota en un equipo Mac. Para compilar y ejecutar aplicaciones de iOS con Visual Studio, debe instalar y configurar el agente remoto en el equipo Mac. Para obtener instrucciones de instalación detalladas, información sobre opciones de configuración y requisitos previos, vea [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Si no va a compilar aplicaciones para iOS, puede omitir este paso.

## <a name="install-or-update-dependencies-manually"></a>Instalar o actualizar manualmente las dependencias

Si decide no instalar una o más dependencias de terceros mediante el Instalador de Visual Studio al instalar la carga de trabajo **Desarrollo móvil con C++** (o, en Visual Studio 2015, la opción Desarrollo móvil de Visual C++), puede instalarlas más adelante siguiendo los pasos que se describen en [Instalar las herramientas](#install-the-tools). El Instalador de Visual Studio se actualiza periódicamente para instalar los componentes de terceros más recientes. Puede usarlo para instalar los SDK y los NDK actualizados. También puede instalarlas o actualizarlas independientemente de Visual Studio.

Puede volver a ejecutar la aplicación de administrador de SDK en el directorio del SDK de Android para actualizar el SDK e instalar herramientas opcionales y niveles de API adicionales. Las actualizaciones pueden no instalarse correctamente si no usa la opción **Ejecutar como administrador** para ejecutar la aplicación SDK Manager. Si tiene problemas para crear una aplicación Android, compruebe el SDK Manager por si hay actualizaciones para los SDK instalados.

Para usar algunos de los emuladores de Android que vienen con Android SDK, puede que tenga que instalar la aceleración de hardware. Para más información, vea [Aceleración de hardware para el rendimiento del emulador (Hyper-V y HAXM)](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

En la mayoría de los casos, Visual Studio puede detectar las configuraciones del software de terceros que haya instalado y mantiene las rutas de instalación en variables de entorno internas. Puede reemplazar las rutas de acceso predeterminadas de estas herramientas de desarrollo multiplataforma en el IDE de Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Para establecer las rutas de acceso para las herramientas de terceros

1. En la barra de menús de Visual Studio, seleccione **Herramientas** > **Opciones**.

1. En el cuadro de diálogo **Opciones**, expanda **Multiplataforma** > **C++**  > **Android**.

   ![Opciones de ruta de acceso de la herramienta de Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Para cambiar la ruta de acceso que usa una herramienta, active la casilla situada junto a la ruta de acceso y edite la ruta de acceso de la carpeta en el cuadro de texto. También puede usar el botón Examinar ( **...** ) para abrir el cuadro de diálogo **Seleccionar ubicación** para seleccionar la carpeta.

1. Elija **Aceptar** para guardar las ubicaciones de carpeta de la herramienta personalizada.

## <a name="see-also"></a>Vea también

- [Instalar y configurar herramientas para compilar con iOS](install-and-configure-tools-to-build-using-ios.md)
- [Desarrollo móvil multiplataforma de Visual Studio C++](https://go.microsoft.com/fwlink/p/?LinkId=536383)
