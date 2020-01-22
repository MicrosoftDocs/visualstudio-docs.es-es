---
title: Desinstalar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo desinstalar Visual Studio, paso a paso.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
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
ms.openlocfilehash: fd21f01f89cb4fe4507775670968496cbb5f99f5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115019"
---
# <a name="uninstall-visual-studio"></a>Desinstalar Visual Studio

Esta página le guía a través de la desinstalación de Visual Studio, nuestro conjunto integrado de herramientas de productividad para desarrolladores.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Desinstalación de Visual Studio para Mac](/visualstudio/mac/uninstall).

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
