---
title: Modificar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo modificar Visual Studio, paso a paso.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/03/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23e44479bedfdb44b2375baae9f342f47b38700b
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810055"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modificación de Visual Studio mediante la incorporación o la eliminación de cargas de trabajo y componentes

::: moniker range="vs-2019"

Es fácil modificar Visual Studio para que incluya solo aquello que quiera y en el momento que quiera. Para ello, abra el Instalador de Visual Studio para agregar o quitar componentes y cargas de trabajo.

::: moniker-end

::: moniker range="vs-2017"

No solo le hemos facilitado la personalización de Visual Studio para que se adapte a las tareas que quiere realizar, sino que también hemos facilitado su personalización. Para ello, inicie el nuevo instalador de Visual Studio y realice los cambios que quiera.

::: moniker-end

Esta es la manera de hacerlo.

>[!IMPORTANT]
>Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, consulte [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>Modificar cargas de trabajo

::: moniker range="vs-2017"

 Las [cargas de trabajo](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) contienen las características que necesita para el lenguaje de programación o la plataforma que está usando. Use cargas de trabajo para modificar Visual Studio de manera que admita el trabajo que quiere realizar, cuando quiera.

::: moniker-end

::: moniker range="vs-2019"

 Las cargas de trabajo contienen las características que necesita para el lenguaje de programación o la plataforma que está usando. Use cargas de trabajo para modificar Visual Studio de manera que admita el trabajo que quiere realizar, cuando quiera.

::: moniker-end

>[!NOTE]
> En el siguiente procedimiento se da por hecho que tiene una conexión a Internet.
>
> Para obtener más información sobre cómo modificar una [instalación sin conexión](create-an-offline-installation-of-visual-studio.md) creada anteriormente de Visual Studio, consulte las páginas [Actualización de una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md) y [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md).

::: moniker range="vs-2017"

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.

     ![Instalador de Visual Studio](media/locate-the-visual-studio-installer.png "Búsqueda del Instalador de Microsoft Visual Studio")

     >[!TIP]
     >En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).<br/><br/> Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Haga clic o pulse para iniciar el instalador y, después, elija **Modificar**.

     ![Inicio o modificación de Visual Studio](media/modify-visual-studio.png "Modificación de Visual Studio 2017")

     Si tiene una actualización pendiente, el botón Modificar se encuentra en otro lugar. De este modo, puede modificar Visual Studio sin actualizar, si decide hacerlo. Haga clic en **Más** y, a continuación, elija **Modificar**.

     ![Actualización o modificación de Visual Studio](media/modify-or-update-visual-studio.png "Actualización o modificación de Visual Studio 2017")

1. Desde la pantalla **Cargas de trabajo**, seleccione o anule la selección de las cargas de trabajo que quiere instalar o desinstalar.

    ![Cuadro de diálogo del programa de instalación de Visual Studio 2017](media/modify-workloads.png "Elección de una carga de trabajo en Visual Studio 2017")

1. Vuelva a elegir **Modificar**.

1. Después de que se instalen los nuevos componentes y cargas de trabajo, elija **Iniciar**.

::: moniker-end

::: moniker range="vs-2019"

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.

     ![Abra el Instalador de Visual Studio desde Windows](media/vs-2019/vs-installer-windows-start.png "Apertura del Instalador de Visual Studio")

     > [!NOTE]
     > También pude encontrar el instalador de Visual Studio en la siguiente ubicación:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que haya instalado y, luego, elija **Modificar**.

     ![Actualización o modificación de Visual Studio](media/vs-2019/vs-installer-modify.png "Actualización o modificación de Visual Studio 2019")

1. En la pestaña **Cargas de trabajo**, seleccione o anule la selección de las cargas de trabajo que quiera instalar o desinstalar.

    ![Cuadro de diálogo del programa de instalación de Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Elección de una carga de trabajo en Visual Studio 2019")

1. Elija si quiere aceptar la opción predeterminada, **Instalar durante la descarga**, o la opción **Descargar e instalar todo**.

    ![Opciones del programa de instalación de Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Selección de la opción de instalar durante la descarga o descargar primero e instalar después")

    La opción "Descargar e instalar todo" resulta útil si quiere realizar la descarga en primer lugar e instalar el producto más adelante.

1. Elija **Modificar**.

1. Cuando se hayan instalado los nuevos componentes y las nuevas cargas de trabajo, elija **Iniciar** en el Instalador de Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modificar componentes individuales

Si no quiere instalar cargas de trabajo para personalizar la instalación de Visual Studio, elija la pestaña **Componentes individuales** del Instalador de Visual Studio, seleccione lo que quiera y, después, siga las indicaciones.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Lista de identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
