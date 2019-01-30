---
title: Administrador de paquetes para R
description: Describe cómo usar el administrador de paquetes de R en Visual Studio para instalar y administrar paquetes de R.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 966a05e0b339409a5dc4df247b4ea2101a8a768d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922852"
---
# <a name="package-manager"></a>Administrador de paquetes

El administrador de paquetes de las herramientas de R para Visual Studio (RTVS) es una interfaz de usuario para administrar los paquetes de R. Para abrirlo, seleccione **Herramientas de R** > **Ventanas** > **Paquetes** o presione **Ctrl**+**7**.

El administrador de paquetes tiene tres pestañas. Cada pestaña muestra una lista de paquetes relevantes a la izquierda y detalles específicos para el paquete seleccionado a la derecha, incluida la versión del paquete, la descripción, la licencia, la ubicación de instalación y vínculos a otra información relevante. El cuadro de búsqueda en la esquina superior derecha le permite filtrar la lista.

> [!Tip]
> El término del cuadro de búsqueda sigue vigente a medida que cambia entre pestañas.

- **Disponible** le permite examinar paquetes que se van a instalar. Si el paquete ya está instalado, el botón **Instalar** de la derecha cambia a **Desinstalar**.

    ![Pestaña paquetes disponibles en las herramientas de R para el administrador de paquetes de Visual Studio](media/package-manager-available.png)

- **Instalado** muestra todos los paquetes instalados y cargados. Un punto verde junto a un paquete indica que está cargado en la sesión de R. Para desinstalar el paquete se pueden usar el icono de la X roja de la lista izquierda o el botón **Desinstalar** situado a la derecha. Una flecha azul hacia arriba situada a la derecha del paquete realiza la actualización si existe una versión más reciente del paquete instalado.

    ![Pestaña paquetes instalados en las herramientas de R para el administrador de paquetes de Visual Studio](media/package-manager-installed.png)

- **Cargado** muestra solo los paquetes que están cargados en la sesión de R, que aparecen con un punto verde. También puede desinstalar y actualizar paquetes aquí.

    ![Pestaña paquetes cargados en las herramientas de R para el administrador de paquetes de Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Ubicaciones de los paquetes

Los paquetes están instalados en las siguientes ubicaciones:

- Los paquetes principales que se incluyen con RTVS están instalados en *C:\Archivos de programa\Microsoft\R Client\R_SERVER\library*
- Los paquetes adicionales se instalan en *%userprofile%\Documentos\R\win-library\3.3*
