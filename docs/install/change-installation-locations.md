---
title: Cambio de las ubicaciones de instalación en Visual Studio 2017
description: Aprenda a reducir la huella de instalación en la unidad del sistema cambiando la ubicación de la caché de descarga, los componentes compartidos, SDK y algunas herramientas a distintas unidades.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 887ebca8645ab30d6d284433baf58451ab10b80c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869384"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Cambio de las ubicaciones de instalación en Visual Studio 2017

**Novedad en 15.7**: Puede reducir la huella de instalación en la unidad del sistema trasladando la caché de descarga, los componentes compartidos, SDK y algunas herramientas a distintas unidades.

Esta es la manera de hacerlo.

1. Cuando instale Visual Studio, elija la pestaña **Opciones de instalación**.

   ![Visual Studio 2017: cambiar la ubicación de instalación](media/installation-options-by-location.png "Change the installation location")

   > [!IMPORTANT]
   > Si pausa la instalación y la reanuda más tarde, Visual Studio la retoma donde se quedó. En otras palabras, el progreso se aplica a lo que queda por descargar e instalar, en lugar de empezar desde el recuento anterior.

2. En la sección **IDE de Visual Studio**, acepte el valor predeterminado. Esto instala el producto principal e incluye los archivos que son específicos para esta versión de Visual Studio.

   > [!IMPORTANT]
   > Si la unidad del sistema es una unidad de estado sólido (SSD),el motivo por el que se recomienda que acepte la ubicación predeterminada en la unidad del sistema es el siguiente: cuando desarrolla con Visual Studio, lee y escribe en una gran cantidad de archivos, lo que aumenta la actividad de E/S del disco.  Es mejor que elija la unidad más rápida para que administre la carga.

3. En la sección **Caché de descarga**, decida si quiere mantener la caché de descarga y, después, active o desactive **Mantener la caché de descarga** en consecuencia. <br><br>Si decide no mantener la caché de descarga, la ubicación solo se usará de forma temporal. Además, esta acción no afecta ni elimina los archivos de las instalaciones anteriores. (Para limpiar todos los paquetes de instalación debe modificar las instalaciones anteriores por separado).

4. En la sección **Caché de descarga**, especifique la unidad donde quiere almacenar los archivos de instalación y los manifiestos. <br><br>Por ejemplo, si selecciona la carga de trabajo “Desarrollo para el escritorio con C++”, el tamaño necesario temporalmente es de 1,58 GB en la unidad del sistema, que se liberará en cuanto finalice la instalación.

   > [!NOTE]
   > Los archivos primero se descargan en una carpeta temporal en la unidad del sistema y luego se eliminan, después de que Visual Studio los compruebe y luego los mueva a la carpeta de caché de descarga. Si opta por mantener la caché de descarga en una unidad diferente, Visual Studio todavía un necesitará espacio en disco equivalente al tamaño de la caché de descarga en la unidad del sistema.
   > [!IMPORTANT]
   > La ubicación se establece con la primera instalación y no se puede cambiar más adelante desde el instalador de la interfaz de usuario. En su lugar, debe [usar parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md) para mover la caché de descarga

5. En la sección **Componentes, herramientas y SDK compartidos**, especifique la unidad donde quiere almacenar los archivos que se comparten entre las instalaciones de Visual Studio en paralelo. Los SDK y las herramientas que permiten que el instalador de Visual Studio cambie su ubicación de instalación también se almacenan en este directorio.

   > [!NOTE]
   > Hay algunas herramientas y SDK que tiene sus propias reglas sobre dónde se pueden instalar. Estas herramientas y SDK todavía se instalarán en la unidad del sistema incluso si elige otra ubicación).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Modificación de Visual Studio 2017](update-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
