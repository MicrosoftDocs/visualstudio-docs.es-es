---
title: Actualizar Visual Studio
titleSuffix: ''
description: Aprenda a actualizar Visual Studio a la versión más reciente, paso a paso.
ms.date: 04/06/2021
ms.custom: vs-acquisition
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8414d745b63eb0e9145208dca97ce9f117c5cf2c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387962"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Actualización de Visual Studio a la versión más reciente

::: moniker range="vs-2017"

Le recomendamos que actualice a la [versión más reciente](/visualstudio/releasenotes/vs2017-relnotes/) de Visual Studio 2017 para recibir siempre las características, correcciones y mejoras más recientes.

Y si desea probar la versión más reciente, puede descargar e instalar [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) en su lugar.

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

   ![Actualización de Visual Studio 2017 mediante el Centro de notificaciones](media/vs-install-notifications-hub-15dot6.png "El Centro de notificaciones en Visual Studio 2017")

      > [!TIP]
      > Una actualización para una edición de Visual Studio 2017 es acumulativa, por lo que siempre debe elegir instalar la que tenga el número de versión más reciente.

1. Cuando aparezca el cuadro de diálogo **Actualizar**, elija **Actualizar ahora**.

    ![Actualización de Visual Studio 2017 mediante el cuadro de diálogo Actualizar del Centro de notificaciones](media/vs-update-now-from-notifications-hub.png "El cuadro de diálogo Actualización del Centro de notificaciones en Visual Studio")

     Si se abre un cuadro de diálogo de Control de acceso de usuario, elija **Sí**. Es posible que aparezca el cuadro de diálogo "Espere" durante un momento, y luego el instalador de Visual Studio se abre para iniciar la actualización.

     ![La nueva experiencia de Instalador de Visual Studio en la versión 15.6](media/visual-studio-15dot6-installer.png "La nueva experiencia de Instalador de Visual Studio en la versión 15.6")

     La actualización continúa. Cuando se haya completado, Visual Studio se reiniciará.

     > [!NOTE]
     > Al ejecutar Visual Studio en modo de administrador, debe reiniciar Visual Studio manualmente después de la actualización.

### <a name="using-the-ide"></a>Uso de el IDE

Puede buscar una actualización y, a continuación, instalarla desde la barra de menús de Visual Studio.

1. No olvide guardar su trabajo.

1. Elija **Ayuda** > **Buscar actualizaciones**.

     ![El nuevo menú Ayuda de la versión 15.6 de Visual Studio](media/vs-help-menu-check-for-updates.png "El nuevo menú Ayuda de la versión 15.6 de Visual Studio")

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

     ![Actualización de Visual Studio 2017 mediante el Instalador de Visual Studio](media/update-visual-studio.png "Actualización de Visual Studio 2017 mediante el Instalador de Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Actualización de Visual Studio 2017, versión 15.5 o anteriores

Si está utilizando una versión anterior, aquí se muestra cómo aplicar una actualización a las versiones de Visual Studio 2017 entre 15.0 y 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Actualizar mediante el centro de Notificaciones

1. Cuando haya actualizaciones, aparecerá la correspondiente marca de notificaciones en Visual Studio.

   ![Marca de notificación de actualización de Visual Studio 2017](media/notification-flag.png "La marca de notificación de actualización en Visual Studio")

   Haga clic en la marca de notificación para abrir la Central de **notificaciones**.

   ![Actualización de Visual Studio 2017 en el centro de notificaciones](media/notifications-hub.png "Actualización de Visual Studio 2017 en el centro de notificaciones")

      > [!TIP]
      > Una actualización para una edición de Visual Studio 2017 es acumulativa, por lo que siempre debe elegir instalar la que tenga el número de versión más reciente.

1. Haga clic en **Está disponible la actualización de Visual Studio** para abrir el cuadro de diálogo **Extensiones y actualizaciones**.

   ![Selección de actualización de Visual Studio](media/notifications-hub-select.png "Selección de actualización de Visual Studio")

1. En el cuadro de diálogo **Extensiones y actualizaciones**, haga clic en el botón **Actualizar**.

   ![Selección de Actualizar en el cuadro de diálogo Extensiones y actualizaciones](media/notifications-extensions-and-updates.png "El cuadro de diálogo Extensiones y actualizaciones de Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Más información sobre las notificaciones de Visual Studio

Visual Studio le avisa cuando una actualización está disponible para Visual Studio o cualquier componente, y también cuando se producen determinados eventos en el entorno de Visual Studio.

* Cuando la marca de notificación es de color amarillo, hay una actualización de producto de Visual Studio disponible para instalar.
* Cuando la marca de notificación es de color rojo, hay un problema con la licencia.
* Cuando la marca de notificación es de color negro, hay mensajes opcionales o informativos para revisar.

Haga clic en la marca de notificaciones para abrir la Central de **notificaciones** y, después, elija las notificaciones sobre las que quiere actuar. O bien, puede optar por omitir o descartar una notificación.

 ![Visualización de un mensaje opcional o informativo en el Centro de notificaciones](media/notification-flag-optional.png "La marca de notificación de mensaje informativo u opcional en Visual Studio")

Si elige ignorar una notificación, Visual Studio deja de mostrarla. Si quiere restablecer la lista de notificaciones omitidas, seleccione el botón **Configuración** en el Centro de notificaciones.

   ![Selección del botón Configuración del Centro de notificaciones para ver las opciones de notificación](media/vs-notifications-hub-settings-button.png "Selección del botón Configuración del Centro de notificaciones para ver las opciones de notificación")

### <a name="update-by-using-the-visual-studio-installer"></a>Actualizar mediante el instalador de Visual Studio

1. Abra el instalador. Es posible que deba actualizar el instalador antes de continuar. Si es así, se le pedirá que lo haga.

   > [!NOTE]
   > En un equipo con Windows 10, encontrará el instalador en la letra **I**, como **Instalador de Visual Studio**, o en la letra **M**, como **Microsoft Visual Studio Installer** (Instalador de Microsoft Visual Studio).

1. En la página **Producto** del instalador, busque la edición de Visual Studio que tenga instalada.

1. Si hay alguna actualización disponible, verá el botón **Actualizar**. (El instalador podría tardar unos segundos en determinar si hay alguna actualización disponible).

   Haga clic en el botón **Actualizar** para instalar las actualizaciones.

     ![Actualización de Visual Studio 2017 mediante el Instalador de Visual Studio](media/update-visual-studio.png "Actualización de Visual Studio mediante el Instalador de Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Se recomienda actualizar a la [versión más reciente](/visualstudio/releases/2019/release-notes/) de Visual Studio para recibir siempre las características, correcciones y mejoras más recientes.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita. Si actualmente utiliza otra versión de Visual Studio, puede [instalar versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md) o [desinstalar versiones anteriores de Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Actualización de Visual Studio para Mac](/visualstudio/mac/update).

Aquí mostramos cómo actualizar Visual&nbsp;Studio&nbsp;2019.

## <a name="use-the-visual-studio-installer"></a>Uso del instalador de Visual Studio

1. Busque el **instalador de Visual Studio** en su equipo.

   En el menú Inicio de Windows, puede buscar "instalador".

   ![Instalador de Visual Studio](media/vs-2019/visual-studio-installer.png "Búsqueda del Instalador de Visual Studio")

   Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que tenga instalada.

   Por ejemplo, si anteriormente ha instalado Visual&nbsp;Studio Community&nbsp;2019 y hay una actualización para esta, aparecerá un mensaje de **Actualización disponible** en el instalador.

     ![Selección de la edición de Visual Studio 2019 que desea actualizar](media/vs-2019/vs-installer-update-visual-studio-community.png "Selección de la edición de Visual Studio 2019 que desea actualizar")

1. Elija **Actualizar** para instalar las actualizaciones.

    ![Selección del botón Actualizar para instalar las actualizaciones](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Selección del botón Actualizar para instalar las actualizaciones")

1. Cuando se complete la actualización, es posible que se le pida reiniciar el equipo. Si es así, hágalo y luego inicie Visual Studio como lo haría habitualmente.

   Si no se le pide reiniciar el equipo, elija **Iniciar** para iniciar Visual Studio desde el instalador.

    ![Selección del botón Iniciar para iniciar Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Selección del botón Iniciar para iniciar Visual Studio")

## <a name="use-the-ide"></a>Uso del IDE

Puede buscar una actualización y, a continuación, instalarla mediante la barra de menús o el cuadro de búsqueda de Visual Studio 2019.

### <a name="open-visual-studio"></a>Abra Visual Studio.

1. En el menú **Inicio** de Windows, elija **Visual Studio 2019**.

    ![Apertura de Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Apertura de Visual Studio 2019 desde Windows")

1. En **Introducción**, elija cualquier opción para abrir el IDE.

    ![Apertura del Instalador de Visual Studio](media/vs2019-choose-option-from-get-started.png "Apertura del Instalador de Visual Studio")

    Se abre Visual Studio. En el IDE, aparece un mensaje **Actualización de Visual Studio 2019**.

    ![En el IDE, aparece un mensaje "Actualización de Visual Studio 2019"](media/vs-2019/update-visual-studio-ide-message.png "En el IDE, aparece un mensaje &quot;Actualización de Visual Studio 2019&quot;")

1. En el mensaje **Actualización de Visual Studio 2019**, elija **Ver detalles**.

   ![Selección del botón Ver detalles en el mensaje de actualización del IDE en Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Selección del botón Ver detalles en el mensaje de actualización del IDE en Visual Studio 2019")

1. En el cuadro de diálogo **La actualización se ha descargado y está lista para instalarse**, elija **Actualizar**.

     ![Selección del botón Actualizar en el cuadro de diálogo "La actualización se ha descargado y está lista para instalarse"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Selección del botón Actualizar en el cuadro de diálogo &quot;La actualización se ha descargado y está lista para instalarse&quot;")

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

### <a name="in-visual-studio"></a>En Visual Studio

1. En la barra de menús, elija **Ayuda** y, a continuación, elija **Buscar actualizaciones**.

     ![Selección de "Buscar actualizaciones" en el menú Ayuda](media/vs-2019/vs-ide-check-updates-help-menu.png "Selección de &quot;Buscar actualizaciones&quot; en el menú Ayuda")

    > [!NOTE]
    > También puede usar el cuadro de búsqueda del IDE para buscar las actualizaciones. Presione **Ctrl**+**Q**, escriba "Buscar actualizaciones" y, a continuación, elija el resultado de la búsqueda coincidente.

1. En el cuadro de diálogo **Actualización disponible**, elija **Actualizar**.

     ![Selección del botón Actualizar en el cuadro de diálogo "Actualización disponible"](media/vs-2019/update-visual-studio-community-from-ide.png "Selección del botón Actualizar en el cuadro de diálogo &quot;Actualización disponible&quot;")

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

## <a name="use-the-notifications-hub"></a>Uso del Centro de notificaciones

1. En Visual Studio, guarde el trabajo.

1. Elija el icono de notificación en la esquina inferior derecha del IDE de Visual Studio para abrir el centro de **notificaciones**.

   ![El icono de notificación en el IDE de Visual Studio](media/vs-2019/notification-bar.png "El icono de notificación en el IDE de Visual Studio")

1. En el **Centro de notificaciones**, elija la actualización que desea instalar y, a continuación, elija **Ver detalles**.

     ![Centro de notificaciones en Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centro de notificaciones en Visual Studio 2019")

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

A continuación, se indica cómo puede hacerlo.

1. En la barra de menús, elija **Herramientas** > **Opciones**.

2. Expanda **Entorno** y, después, elija **Actualizaciones del producto**.

    ![Configuración de las actualizaciones en Visual Studio](media/vs-2019/update-settings-options.png)

3. Elija el modo de instalación y las opciones de descarga automática que quiera para las actualizaciones de Visual Studio.

::: moniker-end

::: moniker range=">=vs-2022"

Se recomienda actualizar a la [versión más reciente](/visualstudio/releases/2022/release-notes/) de Visual Studio para recibir siempre las características, correcciones y mejoras más recientes.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita. Si actualmente utiliza otra versión de Visual Studio, puede [instalar versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md) o [desinstalar versiones anteriores de Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Actualización de Visual Studio para Mac](/visualstudio/mac/update).

Aquí se muestra cómo actualizar Visual&nbsp;Studio&nbsp;2022.

## <a name="use-the-visual-studio-installer"></a>Uso del instalador de Visual Studio

1. Busque el **instalador de Visual Studio** en su equipo.

   En el menú Inicio de Windows, puede buscar "instalador".

   ![Instalador de Visual Studio](media/vs-2019/visual-studio-installer.png "Búsqueda del Instalador de Visual Studio")

   Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que tenga instalada.

   Por ejemplo, si anteriormente ha instalado Visual&nbsp;Studio Community&nbsp;2022 y hay una actualización para esta, aparecerá un mensaje de **Actualización disponible** en el instalador.

     ![Selección de la edición de Visual Studio 2019 que desea actualizar](media/vs-2019/vs-installer-update-visual-studio-community.png "Selección de la edición de Visual Studio 2019 que desea actualizar")

1. Elija **Actualizar** para instalar las actualizaciones.

    ![Selección del botón Actualizar para instalar las actualizaciones](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Selección del botón Actualizar para instalar las actualizaciones")

1. Cuando se complete la actualización, es posible que se le pida reiniciar el equipo. Si es así, hágalo y luego inicie Visual Studio como lo haría habitualmente.

   Si no se le pide reiniciar el equipo, elija **Iniciar** para iniciar Visual Studio desde el instalador.

    ![Selección del botón Iniciar para iniciar Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Selección del botón Iniciar para iniciar Visual Studio")

## <a name="use-the-ide"></a>Uso del IDE

Puede buscar una actualización y, después, instalarla mediante la barra de menús o el cuadro de búsqueda de Visual Studio 2022.

### <a name="open-visual-studio"></a>Abra Visual Studio.

1. Desde el menú **Inicio** de Windows, elija **Visual Studio 2022**.

    ![Apertura de Visual Studio 2022](media/vs-2019/vs-installer-visual-studio-2019.png "Apertura de Visual Studio 2019 desde Windows")

1. En **Introducción**, elija cualquier opción para abrir el IDE.

    ![Apertura del Instalador de Visual Studio](media/vs2019-choose-option-from-get-started.png "Apertura del Instalador de Visual Studio")

    Se abre Visual Studio. En el IDE, aparece un mensaje **Actualización de Visual Studio 2022**.

    ![En el IDE, aparece un mensaje "Actualización de Visual Studio 2019"](media/vs-2019/update-visual-studio-ide-message.png "En el IDE, aparece un mensaje &quot;Actualización de Visual Studio 2019&quot;")

1. En el mensaje **Actualización de Visual Studio 2022**, elija **Ver detalles**.

   ![Selección del botón Ver detalles en el mensaje de actualización del IDE en Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Selección del botón Ver detalles en el mensaje de actualización del IDE en Visual Studio 2019")

1. En el cuadro de diálogo **La actualización se ha descargado y está lista para instalarse**, elija **Actualizar**.

     ![Selección del botón Actualizar en el cuadro de diálogo "La actualización se ha descargado y está lista para instalarse"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Selección del botón Actualizar en el cuadro de diálogo &quot;La actualización se ha descargado y está lista para instalarse&quot;")

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

### <a name="in-visual-studio"></a>En Visual Studio

1. En la barra de menús, elija **Ayuda** y, a continuación, elija **Buscar actualizaciones**.

     ![Selección de "Buscar actualizaciones" en el menú Ayuda](media/vs-2019/vs-ide-check-updates-help-menu.png "Selección de &quot;Buscar actualizaciones&quot; en el menú Ayuda")

    > [!NOTE]
    > También puede usar el cuadro de búsqueda del IDE para buscar las actualizaciones. Presione **Ctrl**+**Q**, escriba "Buscar actualizaciones" y, a continuación, elija el resultado de la búsqueda coincidente.

1. En el cuadro de diálogo **Actualización disponible**, elija **Actualizar**.

     ![Selección del botón Actualizar en el cuadro de diálogo "Actualización disponible"](media/vs-2019/update-visual-studio-community-from-ide.png "Selección del botón Actualizar en el cuadro de diálogo &quot;Actualización disponible&quot;")

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

## <a name="use-the-notifications-hub"></a>Uso del Centro de notificaciones

1. En Visual Studio, guarde el trabajo.

1. Elija el icono de notificación en la esquina inferior derecha del IDE de Visual Studio para abrir el centro de **notificaciones**.

   ![El icono de notificación en el IDE de Visual Studio](media/vs-2019/notification-bar.png "El icono de notificación en el IDE de Visual Studio")

1. En el **Centro de notificaciones**, elija la actualización que desea instalar y, a continuación, elija **Ver detalles**.

     ![Centro de notificaciones en Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centro de notificaciones en Visual Studio 2019")

      > [!TIP]
      > Una actualización para una edición de Visual Studio 2022 es acumulativa, por lo que siempre debe elegir instalar la que tenga el número de versión más reciente.

1. En el cuadro de diálogo **Actualización disponible**, elija **Actualizar**.

   Visual Studio se actualiza, se cierra y vuelve a abrirse.

## <a name="customize-update-settings"></a>Personalización de la configuración de las actualizaciones

Puede personalizar la configuración de las actualizaciones en Visual Studio de diferentes maneras; por ejemplo, puede cambiar el modo de instalación o seleccionar la opción de descargas automáticas.

Hay dos modos de instalación disponibles:

* **Instalación durante la descarga**
* **Descarga e instalación en dos pasos independientes**.

También puede elegir la opción **Descargar actualizaciones automáticamente**, que permite descargar las actualizaciones cuando el equipo está inactivo.

A continuación, se indica cómo puede hacerlo.

1. En la barra de menús, elija **Herramientas** > **Opciones**.

2. Expanda **Entorno** y, después, elija **Actualizaciones del producto**.

    ![Configuración de las actualizaciones en Visual Studio](media/vs-2019/update-settings-options.png)

3. Elija el modo de instalación y las opciones de descarga automática que quiera para las actualizaciones de Visual Studio.
::: moniker-end

## <a name="administrator-updates"></a>Actualizaciones de administrador

Si forma parte de una organización que centraliza la administración de las instalaciones de software, el administrador de la empresa puede hacer que Visual Studio se actualice en la máquina. Para más información sobre cómo controlar o configurar qué tipos de actualizaciones puede aceptar la máquina, consulte [Uso de Configuration Manager para implementar actualizaciones de Visual Studio](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulta también

* [Instalación de distintas versiones de Visual Studio en paralelo](install-visual-studio-versions-side-by-side.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Guía de Visual Studio Enterprise](visual-studio-enterprise-guide.md)
* [Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Modificar Visual Studio](modify-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
