---
title: Desinstalación de Visual Studio para Mac
description: Instrucciones para desinstalar Visual Studio para Mac y las herramientas relacionadas.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.topic: how-to
ms.openlocfilehash: ee30af4ed578bbc59924fcd8968b97dcf9306619
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950028"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Desinstalación de Visual Studio para Mac

Puede usar esta guía para desinstalar cada componente de Visual Studio para Mac por separado si va a la sección correspondiente, o puede usar los scripts proporcionados en la sección [Script de desinstalación](#uninstall-script) para desinstalar todo.

> [!NOTE]
> Esta información solo quita Visual Studio 2019 o 2017 para Mac del equipo. para desinstalar Visual Studio Code, vea [este problema](https://github.com/Microsoft/vscode/issues/52151) para obtener detalles.

## <a name="uninstall-script"></a>Script de desinstalación

Hay dos scripts que se pueden usar para desinstalar Visual Studio para Mac y todos sus componentes del equipo:

- [Script de Visual Studio y Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Script de .NET Core](#net-core-script)

En las secciones siguientes se ofrece información sobre la descarga y el uso de scripts.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Script de Visual Studio para Mac y Xamarin

Puede desinstalar los componentes de Visual Studio y Xamarin a la vez utilizando el [script de desinstalación](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Este script de desinstalación contiene la mayoría de los comandos que encontrará en el artículo. Hay tres omisiones importantes en el script que no se incluyen debido a posibles dependencias externas. Para quitar esto, vaya a la sección pertinente a continuación y quítelas de forma manual:

- **[Desinstalación de Mono](#uninstall-mono-sdk-mdk)**
- **[Desinstalación de AVD de Android](#uninstall-android-avd)**
- **[Desinstalación de Android SDK y del SDK de Java](#uninstall-android-sdk-and-java-sdk)**

Haga lo siguiente para ejecutar el script:

1. Haga clic con el botón derecho en el script y seleccione **Guardar como** para guardar el archivo en el equipo Mac.
2. Abra Terminal y cambie el directorio de trabajo al lugar donde se haya descargado el script:

    ```bash
    cd /location/of/file
    ```

3. Haga que el script sea ejecutable y, después, ejecútelo con **sudo**:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Por último, elimine el script de desinstalación y quite Visual Studio para Mac del Dock.

### <a name="net-core-script"></a>Script de .NET Core

El script de desinstalación para .NET Core se encuentra en el [repositorio de la cli de dotnet](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh).

Haga lo siguiente para ejecutar el script:

1. Haga clic con el botón derecho en el script y seleccione **Guardar como** para guardar el archivo en el equipo Mac.
2. Abra Terminal y cambie el directorio de trabajo al lugar donde se haya descargado el script:

    ```bash
    cd /location/of/file
    ```

3. Haga que el script sea ejecutable y, después, ejecútelo con **sudo**:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Por último, elimine el script de desinstalación de .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Desinstalación de Visual Studio para Mac

El primer paso a la hora de desinstalar Visual Studio de un equipo Mac es buscar **Visual Studio.app** en el directorio **/Applications** y arrastrarlo a la **Papelera**. También puede hacer clic con el botón derecho y seleccionar **Trasladar a la Papelera**, como se muestra aquí:

![Traslado de la aplicación Visual Studio a la Papelera](media/uninstall-image1.png)

Al eliminar este lote de aplicaciones, se quita Visual Studio para Mac, aunque pueda haber otros archivos relacionados con Xamarin en el sistema de archivos.

Para quitar todas las trazas de Visual Studio para Mac, ejecute los siguientes comandos en Terminal:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
rm -rf ~/Library/Application\ Support/VisualStudio/8.0/LocalInstall/Addins/
```

También es posible que quiera quitar el siguiente directorio que contiene varias carpetas y archivos de Xamarin. Sin embargo, tenga en cuenta que este directorio contiene las claves de firma de Android. Para obtener más información, vea la sección **[Desinstalación de Android SDK y del SDK de Java](#uninstall-android-sdk-and-java-sdk)** :

```bash
rm -rf ~/Library/Developer/Xamarin
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

> [!WARNING]
> También es importante que conozca que las claves de firma de Android generadas por Visual Studio para Mac se encuentran en `~/Library/Developer/Xamarin/Keystore`. Asegúrese de realizar una copia de seguridad de estas, o bien evite eliminar este directorio si quiere mantener el almacén de claves.

El SDK de Java (JDK) no necesita desinstalarse, ya que se ha empaquetado previamente como parte de Mac OS X o macOS.

### <a name="uninstall-android-avd"></a>Desinstalación de AVD

> [!WARNING]
> Hay otras aplicaciones fuera de Visual Studio para Mac que también usan Android AVD y estos otros componentes de Android, como Android Studio. La eliminación de este directorio puede provocar la interrupción de proyectos en Android Studio.

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

* * * 





## <a name="uninstall-visual-studio-2019-for-mac-preview"></a>Desinstalación de Visual Studio 2019 para Mac Preview

Visual Studio 2019 para Mac Preview se lanzó como versión preliminar independiente, lo que permite seguir trabajando con la instalación de Visual Studio 2017 para Mac en paralelo.

Ahora que Visual Studio 2019 para Mac se ha lanzado, puede quitar con seguridad la aplicación Visual Studio 2019 para Mac Preview.

Para desinstalar el conjunto de productos de versión preliminar, seleccione **Visual Studio (Preview)** en la carpeta **Aplicaciones** y haga clic en **Mover a la papelera**, tal y como se describe en la imagen siguiente:

![Selección de la opción "Mover a la papelera" en el buscador](media/uninstall-remove-vspreview.png)

También puede quitar el archivo plist de versión preliminar con el comando siguiente:

```bash
rm -rf ~/Library/Preferences/com.microsoft.visual-studio-preview.plist
```

## <a name="see-also"></a>Vea también

- [Desinstalar Visual Studio (en Windows)](/visualstudio/install/uninstall-visual-studio)