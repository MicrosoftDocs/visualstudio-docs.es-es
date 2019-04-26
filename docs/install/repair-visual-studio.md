---
title: Repare Visual Studio.
titleSuffix: ''
description: Obtenga información sobre cómo reparar una instalación de Visual Studio 2017
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3ba5cdf7ba627bc1d6a75368d90da5ce8a726a5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973230"
---
# <a name="repair-visual-studio"></a>Repare Visual Studio.

::: moniker range="vs-2017"

En ocasiones, una instalación de Visual Studio resulta dañada. Una reparación puede solucionar este problema.

1. Busque el **instalador de Visual Studio** en su equipo.

     Por ejemplo, en un equipo que ejecuta la Actualización de aniversario de Windows 10 o posterior, seleccione **Iniciar** y, después, desplácese hasta la letra **V** donde lo verá como **Instalador de Visual Studio**.

   > [!NOTE]
   > En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).
   >
   > Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Abra el instalador, elija **Más** y, luego, **Reparar**.

    ![Reparación de Visual Studio desde el instalador de Visual Studio](media/repair-visual-studio.png "Reparación de Visual Studio desde el instalador de Visual Studio")
    
   > [!NOTE]
   > Al reparar Visual Studio, se restablece el entorno. Se eliminan las personalizaciones locales, como las extensiones por usuario instaladas sin elevación, la configuración de usuario y los perfiles. La configuración sincronizada, como temas, colores o enlaces de teclado, se restaura.
   >

   > [!TIP]
   > La opción **Reparar** solo se muestra para las instancias instaladas de Visual Studio. Si no ve la opción **Reparar**, es posible que haya seleccionado **Más** en una versión mostrada en el instalador de Visual Studio como "Disponible", en lugar de "Instalada".

::: moniker-end

::: moniker range="vs-2019"

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.

     ![Apertura del Instalador de Visual Studio](media/vs2019-visual-studio-installer.png "Apertura del Instalador de Visual Studio")

     > [!NOTE]
     > También pude encontrar el instalador de Visual Studio en la siguiente ubicación:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que tenga instalada. A continuación, elija **Más** y, luego, **Reparar**.

     ![Reparación de Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Repair Visual Studio 2019")

   > [!NOTE]
   > Al reparar Visual Studio, se restablece el entorno. Se eliminan las personalizaciones locales, como las extensiones por usuario instaladas sin elevación, la configuración de usuario y los perfiles. La configuración sincronizada, como temas, colores o enlaces de teclado, se restaura.
   >

   > [!TIP]
   > La opción **Reparar** solo se muestra para las instancias instaladas de Visual Studio. Si no ve la opción **Reparar**, es posible que haya seleccionado **Más** en una versión mostrada en el instalador de Visual Studio como "Disponible", en lugar de "Instalada".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
* [Solución de problemas de instalación y actualización de Visual Studio](troubleshooting-installation-issues.md)
