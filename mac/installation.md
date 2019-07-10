---
title: Instalación de Visual Studio 2019 para Mac
description: Instrucciones sobre cómo instalar Visual Studio 2019 para Mac y los componentes adicionales necesarios para el desarrollo multiplataforma.
author: asb3993
ms.author: amburns
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 2086532f0602b4a2509358cbb6d57178a9a1a0d4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691459"
---
# <a name="install-visual-studio-2019-for-mac"></a>Instalación de Visual Studio 2019 para Mac

Para empezar a desarrollar aplicaciones .NET nativas y multiplataforma en macOS, instale Visual Studio 2019 para Mac siguiendo los pasos que encontrará a continuación.

 > [!div class="button"]
 > [Descargar Visual Studio para Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=navigation+cta&utm_content=download+vsmac2019)

## <a name="requirements"></a>Requisitos

- Equipo Mac con macOS High Sierra 10.12 o una versión posterior.

Para compilar aplicaciones Xamarin para iOS o macOS, también necesitará lo siguiente:

- Xcode 10.0 o una versión posterior. Por lo general, se recomienda usar la versión estable más reciente.
- Un ID de Apple. Si aún no tiene un ID de Apple, puede crearlo en https://appleid.apple.com. Es necesario tener un ID de Apple para la instalación y el inicio de sesión en Xcode.

## <a name="installation-instructions"></a>Instrucciones de instalación

1. Descargue el instalador en la [página de descarga de Visual Studio para Mac](https://aka.ms/vsmac).
2. Una vez completada la descarga, haga clic en **VisualStudioforMacInstaller.dmg** para montar el instalador y ejecútelo haciendo doble clic en el logotipo de flecha:

    [![Haga clic en la flecha grande para comenzar la instalación.](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Es posible que se muestre una advertencia en la que se indique que la aplicación se ha descargado de Internet. Haga clic en **Abrir**.
4. Espere mientras el programa de instalación comprueba el sistema:

    [![El instalador comprueba si los componentes están instalados en el sistema.](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Se mostrará una alerta en la que se le solicitará que acepte los términos de licencia y de privacidad. Haga clic en los vínculos para leerlos y, si está de acuerdo, presione **Continuar**:

    [![Haga clic en los vínculos a los términos de licencia y privacidad y, si está de acuerdo, continúe.](media/install-privacy-sml.png)](media/install-privacy.png#lightbox)

6. Se mostrará una lista de las cargas de trabajo disponibles. Seleccione los componentes que quiere usar:

    [![Elija las características de carga de trabajo opcionales que quiera instalar.](media/install-selection.png)](media/install-selection.png#lightbox)

   Si no desea instalar todas las plataformas, utilice la guía siguiente para ayudarle a elegirlas:

   * **Aplicaciones con Xamarin**:
      - Xamarin.Forms: seleccione las plataformas **Android** y **iOS**.
      - Solo iOS: seleccione la plataforma **iOS** (tenga en cuenta que tendrá que instalar [**Xcode**](https://developer.apple.com/xcode/)).
      - Solo Android: seleccione la plataforma **Android** (tenga en cuenta que tendrá que seleccionar también las dependencias pertinentes).
      - Solo Mac: seleccione la plataforma **MacOS** (tenga en cuenta que tendrá que instalar [**Xcode**](https://developer.apple.com/xcode/)).
      - Aplicaciones de Xamarin completamente multiplataforma: seleccione las plataformas **Android**, **iOS**, y **macOS**.
   * **Aplicaciones de .NET core**: seleccione la plataforma **.NET Core**.
   * **Aplicaciones web ASP.NET Core**: seleccione la plataforma **.NET Core**.
   * **Desarrollo de juegos multiplataforma de Unity**: no es necesario instalar plataformas adicionales más allá de Visual Studio para Mac. Consulte la [guía de instalación de Unity](/visualstudio/mac/setup-vsmac-tools-unity) para obtener más información acerca de cómo instalar la extensión de Unity.

7. Después de haber realizado las selecciones, presione el botón **Instalar**.
8. El instalador mostrará el progreso a medida que se realice la descarga y la instalación de Visual Studio para Mac, así como de las cargas de trabajo seleccionadas. Es posible que se le solicite que indique la contraseña para conceder los privilegios necesarios para la instalación.

Si tiene problemas de red al instalar un entorno corporativo, revise las instrucciones de [instalación tras un firewall o proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Obtenga más información sobre los cambios en las [notas de la versión](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Si decide no instalar una plataforma o herramienta durante la instalación original (al anular la selección en el paso 6), tendrá que volver a ejecutar el instalador si quiere agregar los componentes más adelante.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalar Visual Studio para Mac detrás de un firewall o servidor proxy

Para instalar Visual Studio para Mac detrás de un firewall, es necesario que determinados puntos de conexión sean accesibles para permitir la descarga de las herramientas y las actualizaciones necesarias para el software.

Configure la red de modo que permita el acceso a las ubicaciones siguientes:

- [Puntos de conexión de Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Pasos siguientes

La instalación de Visual Studio para Mac le permite empezar a escribir código para las aplicaciones. Con las guías siguientes obtendrá orientación acerca de los pasos siguientes relacionados con la escritura y la implementación de sus proyectos.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Device Provisioning](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (Aprovisionamiento de dispositivos) (para ejecutar la aplicación en el dispositivo).

### <a name="android"></a>Android

1. [Uso del administrador de Android SDK de Xamarin](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulador de Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Configurar el dispositivo para el desarrollo](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplicaciones de .NET core, aplicaciones web ASP.NET Core, desarrollo de juegos de Unity

Para otras cargas de trabajo, consulte la página [Cargas de trabajo](workloads.md).

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vea también

- [Instalación de Visual Studio (en Windows)](/visualstudio/install/install-visual-studio)
