---
title: Instalación de Visual Studio para Mac
description: Instrucciones sobre cómo instalar Visual Studio para Mac y los componentes adicionales necesarios para el desarrollo multiplataforma.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 2a179b5d02a3c50e6942a660e845edd546037d86
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896489"
---
# <a name="set-up-and-install-visual-studio-for-mac"></a>Configurar e instalar Visual Studio para Mac

## <a name="requirements"></a>Requisitos

Para empezar a desarrollar aplicaciones multiplataforma nativas al descargar Visual Studio para Mac, hay un par de componentes que debe instalar y configurar como preparación.

Para trabajar con iOS en Visual Studio, necesita los siguientes elementos:

* Un equipo Mac con macOS Sierra 10.12 o superior
* Xcode 8.3 o superior. Por lo general, se recomienda usar la versión estable más reciente.
* Un ID de Apple. Si aún no tiene un ID de Apple, puede crearlo en https://appleid.apple.com. Es necesario tener un ID de Apple para la instalación y el inicio de sesión en Xcode.

> [!TIP]
> [Ya está disponible](install-preview.md) la versión preliminar de Visual Studio 2019 para Mac para realizar pruebas.

## <a name="install"></a>Instalar

1. Descargar Visual Studio para Mac desde [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/)

2. Una vez descargado el paquete del instalador, haga clic en el archivo **VisualStudioInstaller.dmg** para montar el instalador y luego ejecútelo al hacer doble clic en el logotipo, como se muestra en la siguiente imagen:

   ![Cuadro de diálogo del instalador](media/installer-image1.png)

3. Es posible que aparezca un cuadro de diálogo de alerta similar a la siguiente imagen. En este caso, haga clic en **Abrir**:

   ![cuadro de diálogo de alerta](media/installer-image2.png)

4. El instalador inspecciona el sistema para comprobar qué componentes hay que instalar o actualizar:

   ![Evaluación del sistema](media/installer-image3.png)

5. Luego aparece un cuadro de diálogo de alerta que le pide que confirme los términos de licencia y privacidad. Haga clic en el botón **Continuar** para confirmar los términos:

   ![Cuadro de diálogo de licencia](media/installer-image4.png)

6. El instalador muestra una lista de componentes necesarios que faltan y que deben descargarse e instalarse. Seleccione qué productos quiere descargar aquí:

   ![Selección de elementos](media/installer-image5.png)

   Si no desea instalar todas las plataformas, utilice la guía siguiente para ayudarle a elegirlas:

   * **Aplicaciones con Xamarin**:
      - Xamarin.Forms: seleccione las plataformas **Android** y **iOS**.
      - Solo iOS: seleccione la plataforma **iOS** (tenga en cuenta que tendrá que instalar [**Xcode**](https://developer.apple.com/xcode/)).
      - Solo Android: seleccione la plataforma **Android** (tenga en cuenta que tendrá que seleccionar también las dependencias pertinentes).
      - Solo Mac: seleccione la plataforma **MacOS** (tenga en cuenta que tendrá que instalar [**Xcode**](https://developer.apple.com/xcode/)).
      - Aplicaciones de Xamarin completamente multiplataforma: seleccione las plataformas **Android**, **iOS**, y **macOS**.
   * **Aplicaciones de .NET core**: seleccione la plataforma **.NET Core**.
   * **Aplicaciones web ASP.NET Core**: seleccione la plataforma **.NET Core**.
   * **Desarrollo de juegos multiplataforma de Unity**: no es necesario instalar plataformas adicionales más allá de Visual Studio para Mac. Consulte la [guía de instalación de Unity](setup-vsmac-tools-unity.md) para obtener más información acerca de cómo instalar la extensión de Unity.

   Esta pantalla de instalación muestra la versión y el tamaño de cada componente individual. Puede hacer clic en cada componente para mostrar una lista de dependencias de ese componente (para Android), ver paquetes adicionales que descarga (para .NET Core) o ver las aplicaciones adicionales necesarias (para iOS y macOS):

   ![Dependencias adicionales de Android](media/installer-image6.png)

7. Una vez que esté satisfecho con la selección, seleccione el botón **Instalar y actualizar** para iniciar el proceso de instalación.

8. El instalador inicia el proceso de descarga e instalación de los elementos seleccionados:

   ![Inicio de la instalación](media/installer-image7.png)

   ![Descarga de Xamarin.Mac](media/installer-image8.png)

   ![Finalización de la instalación](media/installer-image9.png)

9. Se le puede pedir que eleve los permisos necesarios de componentes individuales necesarios para completar la instalación. Escriba aquí las credenciales de administrador para continuar el proceso de instalación:

   ![Especifique los permisos para continuar con el instalador](media/installer-image10.png)

10. Una vez que la instalación sea correcta, puede empezar a desarrollar aplicaciones en Visual Studio si presiona **Iniciar**:

    ![Apertura de Visual Studio](media/installer-image11.png)

> [!NOTE]
> Si decide no instalar una plataforma o herramienta durante la instalación original (al anular la selección en el paso 6), debe volver a ejecutar el [instalador](https://visualstudio.microsoft.com/vs/) si quiere agregar los componentes más adelante.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalar Visual Studio para Mac detrás de un firewall o servidor proxy

Para instalar Visual Studio para Mac detrás de un firewall, es necesario que determinados puntos de conexión sean accesibles para permitir la descarga de las herramientas y las actualizaciones necesarias para el software.

Configure la red de modo que permita el acceso a las ubicaciones siguientes:

* [Puntos de conexión de Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

## <a name="see-also"></a>Vea también

- [Instalación de Visual Studio 2017 (en Windows)](/visualstudio/install/install-visual-studio)