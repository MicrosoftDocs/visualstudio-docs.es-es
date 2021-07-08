---
title: Seleccionar ubicaciones de instalación
description: Obtenga información sobre cómo reducir la huella de instalación de Visual Studio en la unidad del sistema al cambiar la ubicación de la caché de descarga, los componentes compartidos, los SDK y las herramientas a otras unidades. Por ejemplo, mover algunos archivos de la unidad C a la unidad D.
ms.date: 03/30/2019
ms.custom: vs-acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5ad065a780a16420727d90605d95038cc5f4080a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387572"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Selección de las ubicaciones de instalación en Visual Studio

::: moniker range=">=vs-2019"

Puede reducir la huella de instalación de Visual Studio en la unidad del sistema si cambia la ubicación de algunos de sus archivos. En concreto, puede usar otra ubicación para la caché de descarga, los componentes compartidos, los SDK y los archivos de herramientas.

::: moniker-end

::: moniker range="vs-2017"

**Novedad de la versión 15.7**: puede reducir la huella de instalación de Visual Studio en la unidad del sistema si cambia la ubicación de algunos de sus archivos. En concreto, puede usar otra ubicación para la caché de descarga, los componentes compartidos, los SDK y los archivos de herramientas.

::: moniker-end

   > [!NOTE]
   > Hay algunas herramientas y SDK que tienen diferentes reglas sobre dónde se pueden instalar. Estas herramientas y SDK se instalan en la unidad del sistema aunque elija otra ubicación.

¿Ya está listo para comenzar? A continuación se muestra cómo hacerlo.

::: moniker range="vs-2017"

1. Cuando instale Visual Studio, elija la pestaña **Ubicaciones de instalación**.

   ![Visual Studio 2017: selección de la ubicación de instalación](media/vs-installation-locations.png "Seleccione la ubicación de la instalación.")

1. En la sección **IDE de Visual Studio**, acepte el valor predeterminado. Visual Studio instala el producto principal e incluye los archivos que son específicos de esta versión de Visual Studio.

   ![Sección IDE de Visual Studio de la pestaña Ubicaciones de instalación](media/vs-installation-locations-ide.png "Acepte el valor predeterminado de la sección IDE de Visual Studio de la pestaña Ubicación de instalaciones.")

   > [!TIP]
   > Si la unidad del sistema es una unidad de estado sólido (SSD), se recomienda aceptar la ubicación predeterminada en la unidad del sistema. ¿El motivo? Al desarrollar con Visual Studio, se lee desde y se escribe en una gran cantidad de archivos, lo que aumenta la actividad de E/S del disco. Es mejor que elija la unidad más rápida para que administre la carga.

1. En la sección **Caché de descarga**, decida si quiere mantener la caché de descarga y luego dónde quiere almacenar sus archivos.

     ![Sección Caché de descarga de la pestaña Ubicaciones de instalación](media/vs-installation-locations-cache.png "Elija si mantiene la caché de descarga después de la instalación y luego especifique la unidad donde quiere almacenar los archivos.")

    1. Active o desactive **Keep download cache after the installation** (Mantener la caché de descarga después de la instalación).

       Si decide no mantener la caché de descarga, la ubicación solo se usará de forma temporal. Esta acción no afecta a los archivos de las instalaciones anteriores ni los elimina.

    1. Especifique la unidad donde quiere almacenar los archivos de instalación y los manifiestos de la caché de descarga.

        Por ejemplo, si selecciona la carga de trabajo “Desarrollo para el escritorio con C++”, el tamaño necesario temporalmente es de 1,58 GB en la unidad del sistema, que se liberará en cuanto finalice la instalación.

       > [!IMPORTANT]
       > Esta ubicación se establece con la primera instalación y no se puede cambiar más adelante desde la interfaz de usuario del instalador. En su lugar, debe [usar parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md) para mover la caché de descarga.

1. En la sección **Shared components, tools, and SDKs** (Componentes compartidos, herramientas y SDK), especifique la unidad donde quiere almacenar los archivos compartidos en paralelo por las instalaciones de Visual Studio. Los SDK y las herramientas también se almacenan en este directorio.

   ![Sección de componentes compartidos, herramientas y SDK de la pestaña Ubicaciones de instalación](media/vs-installation-locations-shared.png "Especifique la ubicación donde desea almacenar los componentes, herramientas y SDK compartidos.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Cuando instale Visual Studio, elija la pestaña **Ubicaciones de instalación**.

   ![Visual Studio 2019: selección de la ubicación de instalación](media/vs-2019/vs-installer-installation-locations.png "Seleccione la ubicación de la instalación.")

1. En la sección **IDE de Visual Studio**, acepte el valor predeterminado. Visual Studio instala el producto principal e incluye los archivos que son específicos de esta versión de Visual Studio.

   > [!TIP]
   > Si la unidad del sistema es una unidad de estado sólido (SSD), se recomienda aceptar la ubicación predeterminada en la unidad del sistema. ¿El motivo? Al desarrollar con Visual Studio, se lee desde y se escribe en una gran cantidad de archivos, lo que aumenta la actividad de E/S del disco. Es mejor que elija la unidad más rápida para que administre la carga.

1. En la sección **Caché de descarga**, decida si quiere mantener la caché de descarga y luego dónde quiere almacenar sus archivos.

    * Active o desactive **Keep download cache after the installation** (Mantener la caché de descarga después de la instalación).

       Si decide no mantener la caché de descarga, la ubicación solo se usará de forma temporal. Esta acción no afecta a los archivos de las instalaciones anteriores ni los elimina.

    * Especifique la unidad donde quiere almacenar los archivos de instalación y los manifiestos de la caché de descarga.

        Por ejemplo, si selecciona la carga de trabajo “Desarrollo para el escritorio con C++”, el tamaño necesario temporalmente es de 1,58 GB en la unidad del sistema, que se liberará en cuanto finalice la instalación.

       > [!IMPORTANT]
       > Esta ubicación se establece con la primera instalación y no se puede cambiar más adelante desde la interfaz de usuario del instalador. En su lugar, debe [usar parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md) para mover la caché de descarga.

1. En la sección **Componentes, herramientas y SDK compartidos**, observe que usa la misma unidad que seleccionó en la sección "Caché de descarga". El directorio \Microsoft\VisualStudio\Shared es donde Visual Studio almacena los archivos que comparten las instalaciones de Visual Studio en paralelo. Los SDK y las herramientas también se almacenan en este directorio.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Modificar Visual Studio](update-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
