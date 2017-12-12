---
title: Instalar Visual Studio para Mac | Microsoft Docs
description: "Instrucciones sobre cómo instalar Visual Studio para Mac y los componentes adicionales necesarios para el desarrollo multiplataforma."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 25d3227bcf8a18a2fc6ba68c194e9cac75b2e919
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Configuración e instalación de Visual Studio para Mac

## <a name="setup"></a>Programa de instalación

Para empezar a desarrollar aplicaciones multiplataforma nativas al descargar Visual Studio para Mac, hay un par de componentes que debe instalar y configurar como preparación.

Para trabajar con iOS en Visual Studio, necesita los siguientes elementos:

* Un equipo Mac con macOS Sierra 10.12 o superior
* Xcode 8.3
* Un ID de Apple. Si aún no tiene un ID de Apple, puede crearlo en https://appleid.apple.com. Es necesario tener un ID de Apple para la instalación y el inicio de sesión en Xcode.

## <a name="install"></a>Instalar

1. Descargue Visual Studio para Mac desde [https://www.visualstudio.com/](https://www.visualstudio.com/)

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
Si decide no instalar una plataforma o herramienta durante la instalación original (al anular la selección en el paso 6), debe volver a ejecutar el [instalador](https://www.visualstudio.com/vs/) si quiere agregar los componentes más adelante.

## <a name="manual-installation"></a>Instalación manual

Si se produce un error en la instalación o si se produce un error en cualquier componente de la instalación, es posible que pueda resolver el problema mediante una instalación manual. Para ver los componentes necesarios y descargarlos, siga estos pasos:

1. En la segunda pantalla del Instalador de Visual Studio, vaya a la barra de menús y seleccione **View Manual Installation Instructions** (Ver las instrucciones del manual de instalación):

    ![Opción que muestra el elemento de menú de instalación manual](media/installer-image12.png)

2. Siga las instrucciones para descargar e instalar los componentes manualmente:

  ![Cuadro de diálogo de instalación manual](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalar Visual Studio para Mac detrás de un firewall o servidor proxy

Para instalar Visual Studio para Mac detrás de un firewall, es necesario que determinados puntos de conexión sean accesibles para permitir la descarga de las herramientas y las actualizaciones necesarias para el software.

Configure la red de modo que permita el acceso a las ubicaciones siguientes:

* [Puntos de conexión de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)