---
title: Instalación de la versión preliminar de Visual Studio 2019 para Mac
description: Instrucciones sobre cómo instalar la versión preliminar de Visual Studio 2019 para Mac y los componentes adicionales necesarios para el desarrollo multiplataforma.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 17acdd63b5632cf141cc5407ce8e09be3e3a69a0
ms.sourcegitcommit: a260df15214b3198a28ca4e312263942cf6f4ce7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2019
ms.locfileid: "54443785"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>Instalación de la versión preliminar de Visual Studio 2019 para Mac

> [!NOTE]
> La versión preliminar de Visual Studio 2019 para Mac se puede instalar en paralelo con la última versión estable de Visual Studio para Mac. Durante la instalación, se le pedirá que actualice la instalación existente de Visual Studio si no es la versión estable más reciente.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Requisitos de la versión preliminar de Visual Studio 2019 para Mac

- Equipo Mac con macOS High Sierra 10.13 o una versión posterior.

Para compilar aplicaciones Xamarin para iOS o macOS, también necesitará lo siguiente:

- Xcode 10.0 o una versión posterior. Por lo general, se recomienda usar la versión estable más reciente.
- Un ID de Apple. Si aún no tiene un ID de Apple, puede crearlo en https://appleid.apple.com. Es necesario tener un ID de Apple para la instalación y el inicio de sesión en Xcode.

## <a name="installing-the-preview"></a>Instalación de la versión preliminar

1. Descargue el instalador en la [página de la versión preliminar de Visual Studio para Mac](https://aka.ms/vs4mac-preview).
2. Una vez completada la descarga, haga clic en **VisualStudioforMacPreviewInstaller.dmg** para montar el instalador y ejecútelo haciendo doble clic en el logotipo de flecha:

    [![Haga clic en la flecha grande para comenzar la instalación.](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Es posible que se muestre una advertencia en la que se indique que la aplicación se ha descargado de Internet. Haga clic en **Abrir**.
4. Espere mientras el programa de instalación comprueba el sistema:

    [![El instalador comprueba si los componentes están instalados en el sistema.](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Se mostrará una alerta en la que se le solicitará que acepte los términos de licencia y de privacidad. Haga clic en los vínculos para leerlos y, si está de acuerdo, presione **Continuar**:

    [![Haga clic en los vínculos a los términos de licencia y privacidad y, si está de acuerdo, continúe.](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Se mostrará una lista de las cargas de trabajo disponibles. Seleccione las que quiera usar:

    [![Elija las características de carga de trabajo opcionales que quiera instalar.](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Si la versión actual de Visual Studio 2017 para Mac es anterior a la 7.7, se le solicitará que apruebe una actualización a la última versión estable, lo que es necesario para poder realizar la instalación en paralelo. Presione **Continuar** para aprobar la actualización:

    ![Es necesario efectuar la actualización a la versión estable 7.7.](media/install-preview-older-upgrade.png)

7. Después de haber realizado las selecciones, presione el botón **Instalar**.
8. El instalador mostrará el progreso a medida que se realice la descarga y la instalación de Visual Studio para Mac, así como de las cargas de trabajo seleccionadas. Es posible que se le solicite que indique la contraseña para conceder los privilegios necesarios para la instalación.
9. Use **Visual Studio (versión preliminar)** siempre que quiera probar dicha versión preliminar o use la última versión estable para realizar trabajos de producción. Aquí se muestran los dos iconos:

    ![Diferencias entre los iconos de la versión estable y la preliminar](media/install-preview-icons-sml.png)

Si tiene problemas de red al instalar un entorno corporativo, revise las instrucciones de [instalación tras un firewall o proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Obtenga más información sobre los cambios en las [notas de la versión](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

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

Para otras cargas de trabajo, consulte la página [Cargas de trabajo](/visualstudio/mac/workloads).

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vea también

- [Instalación de Visual Studio 2017 (en Windows)](/visualstudio/install/install-visual-studio)
