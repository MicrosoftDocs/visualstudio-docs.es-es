---
title: Actualizar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo actualizar Visual Studio a la versión más reciente, paso a paso.
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80ee1a568e30a4898c767533a4f592e2301a097a
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681442"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Actualización de Visual Studio a la versión más reciente

::: moniker range="vs-2017"

Le recomendamos que actualice a la [versión más reciente](/visualstudio/releasenotes/vs2017-relnotes/) de Visual Studio 2017 para recibir siempre las características, correcciones y mejoras más recientes.

Y si desea probar la versión más reciente, puede descargar e instalar [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019) en su lugar.

> [!IMPORTANT]
> Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Actualización de Visual Studio para Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Actualización de Visual Studio 2017, versión 15.6 o posterior

Se ha simplificado la experiencia de instalación y actualización para que resulte más fácil de usar directamente desde el IDE. Aquí se muestra cómo actualizar desde la versión 15.6 y versiones posteriores a versiones más recientes de Visual Studio.

### <a name="using-the-notifications-hub"></a>Uso del centro de notificaciones

Cuando haya una actualización, aparecerá la correspondiente marca de notificaciones en Visual Studio.

1. No olvide guardar su trabajo.

1. Haga clic en la marca de notificaciones para abrir el Centro de **notificaciones** y, después, elija la actualización que desea instalar.

   ![Actualizar Visual Studio 2017 mediante el Centro de Notificaciones](media/vs-install-notifications-hub-15dot6.png "El Centro de notificaciones en Visual Studio 2017")

      > [!TIP]
      > Una actualización para una edición de Visual Studio 2017 es acumulativa, por lo que siempre debe elegir instalar la que tenga el número de versión más reciente.

1. Cuando aparezca el cuadro de diálogo **Actualizar**, elija **Actualizar ahora**.

    ![Actualizar Visual Studio 2017 mediante el Centro de notificaciones](media/vs-update-now-from-notifications-hub.png "Cuadro de diálogo Actualizar en el Centro de notificaciones de Visual Studio")

     Si se abre un cuadro de diálogo de Control de acceso de usuario, elija **Sí**. Es posible que aparezca el cuadro de diálogo "Espere" durante un momento, y luego el instalador de Visual Studio se abre para iniciar la actualización.

     ![La nueva experiencia del instalador de Visual Studio en la versión 15.6](media/visual-studio-15dot6-installer.png "The new Visual Studio Installer experience in version 15.6")

     La actualización continúa. Cuando se haya completado, Visual Studio se reiniciará.

     > [!NOTE]
     > Al ejecutar Visual Studio en modo de administrador, debe reiniciar Visual Studio manualmente después de la actualización.

### <a name="using-the-ide"></a>Uso de el IDE

Puede buscar una actualización y, a continuación, instalarla desde la barra de menús de Visual Studio.

1. No olvide guardar su trabajo.

1. Elija **Ayuda** > **Buscar actualizaciones**.

     ![El nuevo menú Ayuda de Visual Studio, versión 15.6](media/vs-help-menu-check-for-updates.png "The new Help menu in Visual Studio version 15.6")

1. Cuando aparezca el cuadro de diálogo **Actualizar**, elija **Actualizar ahora**.

   La actualización continúa como se describe en la sección anterior y Visual Studio se reinicia una vez que la actualización finalice correctamente.

   > [!NOTE]
   > Al ejecutar Visual Studio en modo de administrador, debe reiniciar Visual Studio manualmente después de la actualización.

### <a name="using-the-visual-studio-installer"></a>Uso del Instalador de Visual Studio

Al igual que en versiones anteriores de Visual Studio, puede usar el Instalador de Visual Studio para instalar una actualización.

1. No olvide guardar su trabajo.

1. Abra el instalador. El instalador de Visual Studio podría necesitar una actualización antes de continuar.

   > [!NOTE]
   > En un equipo con Windows 10, encontrará el instalador en la letra **I**, como **Instalador de Visual Studio**, o en la letra **M**, como **Microsoft Visual Studio Installer** (Instalador de Microsoft Visual Studio).

1. En la página **Producto** del instalador, busque la edición de Visual Studio que haya instalado anteriormente.

1. Si hay alguna actualización disponible, verá el botón **Actualizar**. (El instalador podría tardar unos segundos en determinar si hay alguna actualización disponible).

   Haga clic en el botón **Actualizar** para instalar las actualizaciones.

     ![Actualizar Visual Studio 2017 mediante el instalador de Visual Studio](media/update-visual-studio.png "Actualizar Visual Studio 2017 mediante el instalador de Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Actualización de Visual Studio 2017, versión 15.5 o anteriores

Si está utilizando una versión anterior, aquí se muestra cómo aplicar una actualización a las versiones de Visual Studio 2017 entre 15.0 y 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Actualizar mediante el centro de Notificaciones

1. Cuando haya actualizaciones, aparecerá la correspondiente marca de notificaciones en Visual Studio.

   ![Actualizar Visual Studio 2017 mediante la Central de notificaciones](media/notification-flag.png "Marca de notificación de actualización en Visual Studio")

   Haga clic en la marca de notificación para abrir la Central de **notificaciones**.

   ![Actualizar Visual Studio 2017 mediante el centro de Notificaciones](media/notifications-hub.png "Centro de Notificaciones en Visual Studio")

      > [!TIP]
      > Una actualización para una edición de Visual Studio 2017 es acumulativa, por lo que siempre debe elegir instalar la que tenga el número de versión más reciente.

1. Haga clic en **Está disponible la actualización de Visual Studio** para abrir el cuadro de diálogo **Extensiones y actualizaciones**.

   ![Actualizar Visual Studio 2017 mediante el Hub de notificaciones](media/notifications-hub-select.png "Hub de notificaciones en Visual Studio")

1. En el cuadro de diálogo **Extensiones y actualizaciones**, haga clic en el botón **Actualizar**.

   ![Actualizar Visual Studio 2017 mediante el Hub de notificaciones](media/notifications-extensions-and-updates.png "Cuadro de diálogo Extensiones y actualizaciones en Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Más información sobre las notificaciones de Visual Studio

Visual Studio le avisa cuando una actualización está disponible para Visual Studio o cualquier componente, y también cuando se producen determinados eventos en el entorno de Visual Studio.

* Cuando la marca de notificación es de color amarillo, hay una actualización de producto de Visual Studio disponible para instalar.
* Cuando la marca de notificación es de color rojo, hay un problema con la licencia.
* Cuando la marca de notificación es de color negro, hay mensajes opcionales o informativos para revisar.

Haga clic en la marca de notificaciones para abrir la Central de **notificaciones** y, después, elija las notificaciones sobre las que quiere actuar. O bien, puede optar por omitir o descartar una notificación.

 ![Ver un mensaje informativo u opcional en la Central de notificaciones](media/notification-flag-optional.png "La marca de notificación de mensaje opcional o informativo en Visual Studio")

Si elige ignorar una notificación, Visual Studio deja de mostrarla. Si quiere restablecer la lista de notificaciones omitidas, seleccione el botón **Configuración** en el Centro de notificaciones.

   ![Hacer clic en el botón Configuración en la Central de notificaciones para ver las opciones de notificación](media/vs-notifications-hub-settings-button.png "Hacer clic en el botón Configuración en la Central de notificaciones para ver las opciones de notificación")

### <a name="update-by-using-the-visual-studio-installer"></a>Actualizar mediante el instalador de Visual Studio

1. Abra el instalador. Es posible que deba actualizar el instalador antes de continuar. Si es así, se le pedirá que lo haga.

   > [!NOTE]
   > En un equipo con Windows 10, encontrará el instalador en la letra **I**, como **Instalador de Visual Studio**, o en la letra **M**, como **Microsoft Visual Studio Installer** (Instalador de Microsoft Visual Studio).

1. En la página **Producto** del instalador, busque la edición de Visual Studio que tenga instalada.

1. Si hay alguna actualización disponible, verá el botón **Actualizar**. (El instalador podría tardar unos segundos en determinar si hay alguna actualización disponible).

   Haga clic en el botón **Actualizar** para instalar las actualizaciones.

     ![Actualizar Visual Studio 2017 mediante el instalador de Visual Studio](media/update-visual-studio.png "Actualizar Visual Studio mediante el Instalador de Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Le recomendamos que actualice a la [versión más reciente](/visualstudio/releases/2019/release-notes/) de Visual Studio 2019 para recibir siempre las características, correcciones y mejoras más recientes.

Y, si todavía no ha instalado Visual Studio 2019, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalarlo de forma gratuita.

> [!IMPORTANT]
> Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Actualización de Visual Studio para Mac](/visualstudio/mac/update).

Aquí mostramos cómo actualizar Visual&nbsp;Studio&nbsp;2019.

## <a name="use-the-visual-studio-installer"></a>Uso del instalador de Visual Studio

1. Abra el instalador.

     ![Apertura del Instalador de Visual Studio desde Windows](media/vs-2019/vs-installer-windows-start.png "Apertura del Instalador de Visual Studio")

   Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que tenga instalada.

   Por ejemplo, si anteriormente ha instalado Visual&nbsp;Studio Community&nbsp;2019 y hay una actualización para esta, aparecerá un mensaje de **Actualización disponible** en el instalador.

     ![Selección de la edición de Visual Studio 2019 para actualizar](media/vs-2019/vs-installer-update-visual-studio-community.png "Selección de la edición de Visual Studio 2019 para actualizar")

1. Elija **Actualizar** para instalar las actualizaciones.

    ![Selección del botón Actualizar para instalar las actualizaciones](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Selección del botón Actualizar para instalar las actualizaciones")

1. Cuando se complete la actualización, es posible que se le pida reiniciar el equipo. Si es así, hágalo y luego inicie Visual Studio como lo haría habitualmente.

   Si no se le pide reiniciar el equipo, elija **Iniciar** para iniciar Visual Studio desde el instalador.

    ![Selección del botón Iniciar para abrir Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Selección del botón Iniciar para abrir Visual Studio")

## <a name="use-the-ide"></a>Uso del IDE

Puede buscar una actualización y, a continuación, instalarla mediante la barra de menús o el cuadro de búsqueda de Visual Studio 2019.

### <a name="open-visual-studio"></a>Apertura de Visual Studio

1. En el menú **Inicio** de Windows, elija **Visual Studio 2019**.

    ![Apertura de Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Apertura de Visual Studio 2019 desde Windows")

1. En **Introducción**, elija cualquier opción para abrir el IDE.

    ![Apertura del Instalador de Visual Studio](media/vs2019-choose-option-from-get-started.png "Apertura del Instalador de Visual Studio")

    Se abre Visual Studio. En el IDE, aparece un mensaje **Actualización de Visual Studio 2019**.

    ![Mensaje "Actualización de Visual Studio 2019" en el IDE](media/vs-2019/update-visual-studio-ide-message.png "Mensaje \"Actualización de Visual Studio 2019\" en el IDE")

1. En el mensaje **Actualización de Visual Studio 2019**, elija **Ver detalles**.

   ![Elección del botón Ver detalles en el mensaje de actualización del IDE de Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Elección del botón Ver detalles en el mensaje de actualización de Visual Studio 2019")

1. En el cuadro de diálogo **La actualización se ha descargado y está lista para instalarse**, elija **Actualizar**.

     ![Elección del botón Actualizar en el cuadro de diálogo "La actualización se ha descargado y está lista para instalarse"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Elección del botón Actualizar en el cuadro de diálogo \"La actualización se ha descargado y está lista para instalarse\"")

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

### <a name="in-visual-studio"></a>En Visual Studio

1. En la barra de menús, elija **Ayuda** y, a continuación, elija **Buscar actualizaciones**.

     ![Elija "Buscar actualizaciones" en el menú Ayuda](media/vs-2019/vs-ide-check-updates-help-menu.png "Elija \"Buscar actualizaciones\" en el menú Ayuda")

    > [!NOTE]
    > También puede usar el cuadro de búsqueda del IDE para buscar las actualizaciones. Presione **Ctrl**+**Q**, escriba "Buscar actualizaciones" y, a continuación, elija el resultado de la búsqueda coincidente.

1. En el cuadro de diálogo **Actualización disponible**, elija **Actualizar**.

     ![Elección del botón Actualizar en el cuadro de diálogo "La actualización se ha descargado y está lista para instalarse"](media/vs-2019/update-visual-studio-community-from-ide.png "Elección del botón Actualizar en el cuadro de diálogo \"La actualización se ha descargado y está lista para instalarse\"")

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

## <a name="use-the-notifications-hub"></a>Uso del Centro de notificaciones

1. En Visual Studio, guarde el trabajo.

1. Elija el icono de notificación en la esquina inferior derecha del IDE de Visual Studio para abrir el centro de **notificaciones**.

   ![El icono de notificación del IDE de Visual Studio](media/vs-2019/notification-bar.png "El icono de notificación del IDE de Visual Studio")

1. En el **Centro de notificaciones**, elija la actualización que desea instalar y, a continuación, elija **Ver detalles**.

     ![El Centro de notificaciones de Visual Studio 2019](media/vs-2019/notification-hub-update.png "El Centro de notificaciones de Visual Studio 2019")

      > [!TIP]
      > Una actualización para una edición de Visual Studio 2019 es acumulativa, por lo que siempre debe elegir instalar la que tenga el número de versión más reciente.

1. En el cuadro de diálogo **Actualización disponible**, elija **Actualizar**.

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

## <a name="customize-update-settings"></a>Personalización de la configuración de las actualizaciones

Puede personalizar la configuración de las actualizaciones en Visual Studio de diferentes maneras; por ejemplo, puede cambiar el modo de instalación o seleccionar la opción de descargas automáticas.

Hay dos modos de instalación disponibles:

* **Instalación durante la descarga**
* **Descarga e instalación en dos pasos independientes**.

También puede elegir la opción **Descargar actualizaciones automáticamente**, que permite descargar las actualizaciones cuando el equipo está inactivo.

Esta es la manera de hacerlo:

1. En la barra de menús, seleccione **Herramientas** > **Opciones**.

2. Expanda **Entorno** y, después, elija **Actualizaciones del producto**.

    ![Configuración de las actualizaciones en Visual Studio](media/vs-2019/update-settings-options.png)

3. Elija el modo de instalación y las opciones de descarga automática que quiera para las actualizaciones de Visual Studio.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación de distintas versiones de Visual Studio en paralelo](install-visual-studio-versions-side-by-side.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Modificar Visual Studio](modify-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
