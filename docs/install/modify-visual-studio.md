---
title: Modificación de cargas de trabajo, componentes y paquetes de idioma de Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo modificar Visual Studio, paso a paso.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: contperf-fy21q2
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 30b28af562e5dbaa8c05624f6cc9d531cf652419
ms.sourcegitcommit: 8d3d51042261df603487169a7a008fe8f71404ec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2021
ms.locfileid: "109501777"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Modificación de cargas de trabajo, componentes y paquetes de idioma de Visual Studio

::: moniker range="vs-2019"

Es fácil modificar Visual Studio para que incluya solo aquello que quiera y en el momento que quiera. Para ello, abra el Instalador de Visual Studio para agregar o quitar componentes y cargas de trabajo.

::: moniker-end

::: moniker range="vs-2017"

No solo le hemos facilitado la personalización de Visual Studio para que se adapte a las tareas que quiere realizar, sino que también hemos facilitado su personalización. Para ello, abra el nuevo Instalador de Visual Studio y realice los cambios que quiera.

::: moniker-end

## <a name="prerequisites"></a>Requisitos previos

+ Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, consulte [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ En los siguientes procedimientos se da por hecho que tiene una conexión a Internet. Para obtener más información sobre cómo modificar una [instalación sin conexión](create-an-offline-installation-of-visual-studio.md) creada anteriormente de Visual Studio, consulte las páginas [Actualización de una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md) y [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md).

## <a name="launch-the-installer"></a>Inicie el programa de instalación.

Para realizar modificaciones en la instalación, debe iniciar el programa de instalación de Visual Studio.

::: moniker range="vs-2017"

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.

     ![Instalador de Visual Studio](media/locate-the-visual-studio-installer.png "Búsqueda del Instalador de Microsoft Visual Studio")

     >[!TIP]
     >En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).<br/><br/> Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Abra el instalador y, después, elija **Modificar**.

     ![Inicio o modificación de Visual Studio](media/modify-visual-studio.png "Modificación de Visual Studio 2017")

     > [!IMPORTANT]
     > Si tiene una actualización pendiente, el botón Modificar se encuentra en otro lugar. De este modo, puede modificar Visual Studio sin actualizar, si decide hacerlo. Haga clic en **Más** y, a continuación, elija **Modificar**.
     >
     > ![Actualización o modificación de Visual Studio](media/modify-or-update-visual-studio.png "Actualización o modificación de Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Busque el **instalador de Visual Studio** en su equipo.

     En el menú Inicio de Windows, puede buscar "instalador".

     ![Instalador de Visual Studio](media/vs-2019/visual-studio-installer.png "Búsqueda del Instalador de Visual Studio")

     > [!NOTE]
     > También pude encontrar el instalador de Visual Studio en la siguiente ubicación:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que haya instalado y, luego, elija **Modificar**.

     ![Selección de la edición de Visual Studio y posterior modificación](media/vs-2019/vs-installer-modify.png "Selección de la edición Visual Studio 2019 y posterior modificación")

     > [!IMPORTANT]
     > Si tiene una actualización pendiente, el botón Modificar se encuentra en otro lugar. De este modo, puede modificar Visual Studio sin actualizar, si decide hacerlo. Elija **Más** y, a continuación, **Modificar**.
     >
     > ![Actualización o modificación de Visual Studio](media/vs-2019/modify-update-visual-studio.png "Actualización o modificación de Visual Studio 2019")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Cambio de cargas de trabajo o componentes individuales

::: moniker range="vs-2017"

 Las [cargas de trabajo](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) contienen las características que necesita para el lenguaje de programación o la plataforma que está usando. Use cargas de trabajo para modificar Visual Studio de manera que admita el trabajo que quiere realizar, cuando quiera.

1. En el Instalador de Visual Studio, elija la pestaña **Cargas de trabajo** y, a continuación, seleccione o anule la selección de las cargas de trabajo que desee.

   Alternativamente, si no quiere usar cargas de trabajo para personalizar la instalación de Visual Studio, elija la pestaña **Componentes individuales** del Instalador de Visual Studio y seleccione los componentes que quiera. Después, siga las indicaciones.

    ![Cuadro de diálogo del programa de instalación de Visual Studio 2017](media/modify-workloads.png "Elección de una carga de trabajo en Visual Studio 2019")

1. Elija si quiere aceptar la opción predeterminada, **Instalar durante la descarga**, o la opción **Descargar e instalar todo**.

    ![Opciones del programa de instalación de Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Selección de la opción de instalar durante la descarga o descargar primero e instalar después")

    La opción "Descargar e instalar todo" resulta útil si quiere realizar la descarga en primer lugar e instalar el producto más adelante.

1. Elija **Modificar**.

1. Si lo desea, elija la pestaña **Cargas de trabajo** y, a continuación, seleccione o anule la selección de las cargas de trabajo que desee.


1. Cuando se hayan instalado las nuevas cargas de trabajo, elija **Iniciar** en el Instalador de Visual Studio para abrir Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Las cargas de trabajo contienen las características que necesita para el lenguaje de programación o la plataforma que está usando. Use cargas de trabajo para modificar Visual Studio de manera que admita el trabajo que quiere realizar, cuando quiera.

 > [!TIP]
>Para más información sobre qué herramientas y paquetes de componentes necesita para el desarrollo, consulte [Cargas de trabajo de Visual Studio](https://visualstudio.microsoft.com/vs/#workloads).

1. En el Instalador de Visual Studio, elija la pestaña **Cargas de trabajo** y, a continuación, seleccione o anule la selección de las cargas de trabajo que desee.

    ![Cuadro de diálogo del programa de instalación de Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Elección de una carga de trabajo en Visual Studio 2019")

1. Elija si quiere aceptar la opción predeterminada, **Instalar durante la descarga**, o la opción **Descargar e instalar todo**.

    ![Opciones del programa de instalación de Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Selección de la opción de instalar durante la descarga o descargar primero e instalar después")

    La opción "Descargar e instalar todo" resulta útil si quiere realizar la descarga en primer lugar e instalar el producto más adelante.

1. Elija **Modificar**.

1. Cuando se hayan instalado las nuevas cargas de trabajo, elija **Iniciar** en el Instalador de Visual Studio para abrir Visual Studio.

::: moniker-end


>[!TIP]
> Para más información sobre SQL Server Data Tools (SSDT), vea [Descarga e instalación de SQL Server Data Tools (SSDT) para Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Modificación de paquetes de idioma

De manera predeterminada, el programa instalador hace coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. Sin embargo, puede cambiar el idioma siempre que lo desee. 

Para ello:
1. Elija la pestaña **Paquetes de idioma** en el instalador de Visual Studio.
2. Seleccione el idioma que prefiera.
3. Siga las instrucciones.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Lista de identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
