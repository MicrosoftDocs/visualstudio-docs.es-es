---
title: Desinstalación de Visual Studio para Mac
description: Instrucciones para desinstalar Visual Studio para Mac y las herramientas relacionadas.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 14afeefac0bb5aa198b2f62ba00ba85831b23ffb
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33884228"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Desinstalación de Visual Studio para Mac

Hay una serie de productos de Xamarin que permiten el desarrollo de aplicaciones entre plataformas, incluidas aplicaciones independientes como Visual Studio para Mac.

Esta guía puede usarse para desinstalar cada producto de manera individual dirigiéndose a la sección correspondiente. El conjunto de aplicaciones completo de Xamarin puede desinstalarse si se sigue esta guía de principio a fin.

Si ya tenía Xamarin Studio instalado en el equipo, es posible que también deba seguir las instrucciones de la guía de [desinstalación](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/uninstalling_xamarin/) de developer.xamarin.com, además de los siguientes pasos.

## <a name="uninstall-script"></a>Script de desinstalación

Puede desinstalar Visual Studio y sus componentes asociados de una vez con el [script de desinstalación](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Este script de desinstalación contiene la mayoría de los comandos que encontrará en el artículo. Hay dos omisiones importantes en el script que no se incluyen debido a posibles dependencias externas:

- **Desinstalación de Mono**
- **Desinstalación de AVD**

Haga lo siguiente para ejecutar el script:

1. Haga clic con el botón derecho en el script y seleccione **Guardar como...** para guardar el archivo en el equipo Mac.
2. Abra Terminal y cambie el directorio de trabajo al lugar donde se haya descargado el script:

    ```bash
    $ cd /location/of/file
    ```
3. Haga que el script sea ejecutable y, después, ejecútelo con **sudo**:

    ```bash
    $ chmod +x ./uninstall-vsmac.sh
    $ sudo ./uninstall-vsmac.sh
    ```
4. Por último, elimine el script de desinstalación.

## <a name="uninstall-visual-studio-for-mac"></a>Desinstalación de Visual Studio para Mac

El primer paso a la hora de desinstalar Visual Studio de un equipo Mac es buscar **Visual Studio.app** en el directorio **/Applications** y arrastrarlo a la **Papelera**. También puede hacer clic con el botón derecho y seleccionar **Trasladar a la Papelera**, como se muestra aquí:

![Traslado de la aplicación Visual Studio a la Papelera](media/uninstall-image1.png)

Al eliminar este lote de aplicaciones, se quita Visual Studio para Mac, aunque pueda haber otros archivos relacionados con Xamarin en un sistema de archivos.

Para quitar todas las trazas de Visual Studio para Mac, deben ejecutarse los siguientes comandos en Terminal:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

## <a name="uninstall-mono-sdk-mdk"></a>Desinstalación del SDK de Mono (MDK)

Mono es una implementación de código abierto de Microsoft .NET Framework que usan todos los productos de Xamarin (Xamarin.iOS, Xamarin.Android y Xamarin.Mac) para permitir el desarrollo de estas plataformas en C#.

> [!WARNING]
> Existen otras aplicaciones fuera de Visual Studio para Mac que también usan Mono, como Unity.
> Asegúrese de que no hay otras dependencias en Mono antes de desinstalarlo.

Para quitar Mono Framework de un equipo, ejecute los siguientes comandos en Terminal:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Desinstalación de Xamarin.Android

Existen varios elementos necesarios para la instalación y el uso de Xamarin.Android, como Android SDK y el SDK de Java.

Use los siguientes comandos para quitar Xamarin.Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Desinstalación de Android SDK y del SDK de Java

Android SDK es necesario para la implementación de aplicaciones de Android. Para quitar completamente todos los elementos de Android SDK, busque el archivo en **~/Library/Developer/Xamarin/** y muévalo a la **Papelera**.

El SDK de Java (JDK) no necesita desinstalarse, ya que se ha empaquetado previamente como parte de Mac OS X o macOS.

### <a name="uninstall-android-avd"></a>Desinstalación de AVD

> [!WARNING]
> Hay otras aplicaciones fuera de Visual Studio para Mac que también usan AVD y estos componentes adicionales de Android, como Android Studio.
> La eliminación de este directorio puede hacer que los proyectos se interrumpan en Android Studio. 

Para quitar cualquier AVD y otros componentes de Android, use el comando siguiente:

```bash
rm -rf ~/.android
```

Para quitar solo los AVD, use el comando siguiente:

```bash
rm -rf ~/.android/avd
```

 

## <a name="uninstall-xamarinios"></a>Desinstalación de Xamarin.iOS

Xamarin.iOS permite el desarrollo de aplicaciones de iOS con C# o F# con Visual Studio para Mac.

Use los siguientes comandos en Terminal para quitar todos los archivos de Xamarin.iOS desde un sistema de archivos:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Desinstalación de Xamarin.Mac

Xamarin.Mac se puede desinstalar del equipo con los siguientes dos comandos para erradicar el producto y la licencia del equipo Mac respectivamente:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Desinstalación de Inspector y Workbooks

A partir de la versión 1.2.2, Xamarin Workbooks y Xamarin Inspector se pueden desinstalar desde Terminal si se ejecuta:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

En cuanto a las versiones anteriores, debe quitar manualmente los siguientes artefactos:

* Eliminar la aplicación Workbooks de `"/Applications/Xamarin Workbooks.app"`
* Eliminar la aplicación Inspector de `"Applications/Xamarin Inspector.app"`
* Eliminar los complementos: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` y `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Eliminar Inspector y los archivos auxiliares aquí: `/Library/Frameworks/Xamarin.Interactive.framework` y `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Desinstalar Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Desinstalar el instalador de Visual Studio

Use los siguientes comandos para quitar todos los seguimientos del instalador universal de Xamarin:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```
