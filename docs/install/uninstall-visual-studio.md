---
title: Desinstalar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo desinstalar Visual Studio, paso a paso.
ms.date: 05/06/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9d1412d6e015ec7d05e700370c7a379ada9a57b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419099"
---
# <a name="uninstall-visual-studio"></a>Desinstalar Visual Studio

Esta página le guía a través de la desinstalación de Visual Studio, nuestro conjunto integrado de herramientas de productividad para desarrolladores.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Desinstalación de Visual Studio para Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Si tiene problemas con la instancia de Visual Studio, pruebe la herramienta de **reparación**. Para obtener más información, vea [Reparación de Visual Studio](../install/repair-visual-studio.md). 
>
> Si quiere cambiar la ubicación de algunos de los archivos de Visual Studio, es posible hacerlo sin desinstalar la instancia actual. Para obtener más información, consulte [Selección de las ubicaciones de instalación en Visual Studio](../install/change-installation-locations.md).
>
> Para obtener sugerencias para la solución de problemas, consulte [Solución de problemas de instalación y actualización de Visual Studio](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta la Actualización de aniversario de Windows 10 o posterior, seleccione **Iniciar** y desplácese hasta la letra **V** donde lo verá como **Instalador de Visual Studio**.

     ![Instalador de Visual Studio](media/locate-the-visual-studio-installer.png "Búsqueda del Instalador de Microsoft Visual Studio")

   > [!NOTE]
   > En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).<br/><br/> Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. En el instalador, busque la edición de Visual Studio que tenga instalada. A continuación, elija **Más** y, luego, **Desinstalar**.

     ![Desinstalación de Visual Studio 2017](media/uninstall-visual-studio.png "Desinstalar Visual Studio 2017")

1. Haga clic en **Aceptar** para confirmar su elección.

Si cambia de idea más tarde y quiere volver a instalar Visual Studio 2017, inicie el Instalador de Visual Studio de nuevo y, después, seleccione **Instalar** desde la pantalla de selección.

## <a name="uninstall-visual-studio-installer"></a>Desinstalación del instalador de Visual Studio

Para quitar completamente todas las instalaciones de Visual Studio 2017 y el Instalador de Visual Studio de la máquina, desinstálelo desde Aplicaciones y características.

1. En Windows 10, escriba **Aplicaciones y características** en el cuadro "Escriba aquí para ejecutar la búsqueda".
1. Busque **Microsoft Visual Studio 2017** (o **Visual Studio 2017**).
1. Elija **Desinstalar**.
1. Luego busque **Instalador de Microsoft Visual Studio**.
1. Elija **Desinstalar**.

::: moniker-end

::: moniker range="vs-2019"

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.

     ![Apertura del Instalador de Visual Studio](media/vs-2019/vs-installer-windows-start.png "Apertura del Instalador de Visual Studio")

     > [!NOTE]
     > También pude encontrar el instalador de Visual Studio en la siguiente ubicación:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que tenga instalada. A continuación, elija **Más** y, luego, **Desinstalar**.

     ![Desinstalación de Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Desinstalación de Visual Studio 2019")

1. Haga clic en **Aceptar** para confirmar su elección.

     ![Confirmación de desinstalación de Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Confirme que quiere desinstalar Visual Studio 2019")

Si cambia de opinión más tarde y quiere volver a instalar Visual Studio 2019, vuelva a iniciar el Instalador de Visual Studio, elija la pestaña **Disponible**, la edición de Visual Studio que quiere instalar y luego, **Instalar**.

## <a name="uninstall-visual-studio-installer"></a>Desinstalación del instalador de Visual Studio

Para quitar todas las instalaciones de Visual Studio 2019 y el Instalador de Visual Studio de la máquina, desinstálelo desde Aplicaciones y características.

1. En Windows 10, escriba **Aplicaciones y características** en el cuadro "Escriba aquí para ejecutar la búsqueda".
1. Busque **Visual Studio 2019**.
1. Elija **Desinstalar**.
1. Luego busque **Instalador de Microsoft Visual Studio**.
1. Elija **Desinstalar**.

::: moniker-end

## <a name="remove-all-files"></a>Eliminación de todos los archivos

Si se produce un error muy grave y no se puede desinstalar Visual Studio mediante las instrucciones anteriores, existe una opción de "último recurso" cuyo uso puede considerar en su lugar. Para obtener más información sobre cómo quitar completamente todos los archivos de instalación de Visual Studio y la información de producto, consulte la página [Quitar Visual Studio](remove-visual-studio.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Modificar Visual Studio](modify-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
