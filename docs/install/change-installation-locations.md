---
title: Seleccionar ubicaciones de instalación
description: Obtenga información sobre cómo reducir la huella de instalación de Visual Studio en la unidad del sistema al cambiar la ubicación de la caché de descarga, los componentes compartidos, los SDK y las herramientas a otras unidades.
ms.date: 11/07/2018
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7e026b85a990e0186decc9c67ebecb169c0fa98
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983902"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Selección de las ubicaciones de instalación en Visual Studio

**Novedades de la versión 15.7**: Puede reducir la huella de instalación de Visual Studio en la unidad del sistema si cambia la ubicación de algunos de sus archivos. En concreto, puede usar otra ubicación para la caché de descarga, los componentes compartidos, los SDK y los archivos de herramientas.

   > [!NOTE]
   > Hay algunas herramientas y SDK que tienen diferentes reglas sobre dónde se pueden instalar. Estas herramientas y SDK se instalan en la unidad del sistema aunque elija otra ubicación.

¿Listo para comenzar? Esta es la manera de hacerlo.

1. Cuando instale Visual Studio, elija la pestaña **Ubicaciones de instalación**.

   ![Selección de la ubicación de instalación de Visual Studio 2017](media/vs-installation-locations.png "Seleccione la ubicación de instalación.")

1. En la sección **IDE de Visual Studio**, acepte el valor predeterminado. Visual Studio instala el producto principal e incluye los archivos que son específicos de esta versión de Visual Studio.

   ![Sección IDE de Visual Studio de la pestaña Ubicaciones de instalación](media/vs-installation-locations-ide.png "Acepte el valor predeterminado de la sección IDE de Visual Studio de la pestaña Ubicaciones de instalación.")

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

   ![Sección Componentes compartidos, herramientas y SDK de la pestaña Ubicaciones de instalación](media/vs-installation-locations-shared.png "Especifique la ubicación donde quiere almacenar los componentes compartidos, las herramientas y los SDK.")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Modificar Visual Studio](update-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
