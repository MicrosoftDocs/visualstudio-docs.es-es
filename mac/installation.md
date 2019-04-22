---
title: Instalación de Visual Studio 2019 para Mac
description: Instrucciones sobre cómo instalar Visual Studio 2019 para Mac y los componentes adicionales necesarios para el desarrollo multiplataforma.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 52f9e5f5d21fe69cde613d8e05b365fc8d795dd8
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857325"
---
# <a name="install-visual-studio-2019-for-mac"></a>Instalación de Visual Studio 2019 para Mac

Para empezar a desarrollar aplicaciones .NET nativas y multiplataforma en macOS, instale Visual Studio 2019 para Mac siguiendo los pasos que encontrará a continuación.

## <a name="requirements"></a>Requisitos

- Equipo Mac con macOS High Sierra 10.12 o una versión posterior.

Para compilar aplicaciones Xamarin para iOS o macOS, también necesitará lo siguiente:

- Xcode 11.0 o una versión posterior. Por lo general, se recomienda usar la versión estable más reciente.
- Un ID de Apple. Si aún no tiene un ID de Apple, puede crearlo en https://appleid.apple.com. Es necesario tener un ID de Apple para la instalación y el inicio de sesión en Xcode.

## <a name="installation-instructions"></a>Instrucciones de instalación

1. Descargue el instalador en la [página de descarga de Visual Studio para Mac](https://aka.ms/vsmac).
2. Una vez completada la descarga, haga clic en **VisualStudioforMacInstaller.dmg** para montar el instalador y ejecútelo haciendo doble clic en el logotipo de flecha:

    [![CHaga clic en la flecha grande para comenzar la instalación.(media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Es posible que se muestre una advertencia en la que se indique que la aplicación se ha descargado de Internet. Haga clic en **Abrir**.
4. Espere mientras el programa de instalación comprueba el sistema:

    [![TEl instalador comprueba si los componentes están instalados en el sistema.(media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Se mostrará una alerta en la que se le solicitará que acepte los términos de licencia y de privacidad. Haga clic en los vínculos para leerlos y, si está de acuerdo, presione **Continuar**:

    [![FHaga clic en los vínculos a los términos de licencia y privacidad y, si está de acuerdo, continúe.(media/install-privacy-sml.png)](media/install-privacy.png#lightbox)

6. Se mostrará una lista de las cargas de trabajo disponibles. Seleccione las que quiera usar:

    [![CElija las características de carga de trabajo opcionales que quiera instalar.(media/install-selection-sml.png)](media/install-selection.png#lightbox)

7. Después de haber realizado las selecciones, presione el botón **Instalar**.
8. El instalador mostrará el progreso a medida que se realice la descarga y la instalación de Visual Studio para Mac, así como de las cargas de trabajo seleccionadas. Es posible que se le solicite que indique la contraseña para conceder los privilegios necesarios para la instalación.

Si tiene problemas de red al instalar un entorno corporativo, revise las instrucciones de [instalación tras un firewall o proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Obtenga más información sobre los cambios en las [notas de la versión](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Si decide no instalar una plataforma o herramienta durante la instalación original (al anular la selección en el paso 6), tendrá que volver a ejecutar el instalador si quiere agregar los componentes más adelante.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalar Visual Studio para Mac detrás de un firewall o servidor proxy

Para instalar Visual Studio para Mac detrás de un firewall, es necesario que determinados puntos de conexión sean accesibles para permitir la descarga de las herramientas y las actualizaciones necesarias para el software.

Configure la red de modo que permita el acceso a las ubicaciones siguientes:

- [Puntos de conexión de Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Pasos siguientes

La instalación de Visual Studio para Mac le permite empezar a escribir código para las aplicaciones. Con las guías siguientes obtendrá orientación acerca de los pasos siguientes relacionados con la escritura y la implementación de sus proyectos.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Device Provisioning](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (Aprovisionamiento de dispositivos) (para ejecutar la aplicación en el dispositivo).

### <a name="android"></a>Android

1. [Uso del administrador de Android SDK de Xamarin](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulador de Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Configurar el dispositivo para el desarrollo](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplicaciones de .NET core, aplicaciones web ASP.NET Core, desarrollo de juegos de Unity

Para otras cargas de trabajo, consulte la página [Cargas de trabajo](/visualstudio/mac/workloads).

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vea también

- [Instalación de Visual Studio (en Windows)](/visualstudio/install/install-visual-studio)
