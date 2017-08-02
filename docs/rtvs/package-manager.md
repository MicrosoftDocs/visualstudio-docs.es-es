---
title: Administrador de paquetes en las herramientas de R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>Administrador de paquetes

El administrador de paquetes de las herramientas de R para Visual Studio (RTVS) es una interfaz de usuario para administrar los paquetes de R. Para abrirlo, seleccione **Herramientas de R > Ventanas > Paquetes** o presione Ctrl+7.

El administrador de paquetes tiene tres pestañas como se describe a continuación. Todas las pestañas muestran una lista de paquetes relevantes a la izquierda y detalles específicos para el paquete seleccionado a la derecha, incluida la versión del paquete, la descripción, la licencia, la ubicación de instalación y vínculos a otra información relevante. El cuadro de búsqueda en la esquina superior derecha le permite filtrar la lista.

> [!Tip]
> El término del cuadro de búsqueda sigue vigente a medida que cambia entre pestañas.

- **Disponible** le permite examinar paquetes que se van a instalar. Si el paquete ya está instalado, el botón **Instalar** de la derecha cambiará a **Desinstalar**.

    ![Pestaña paquetes disponibles en las herramientas de R para el administrador de paquetes de Visual Studio](~/docs/rtvs/media/package-manager-available.png)

- **Instalado** muestra todos los paquetes instalados y cargados. Un punto verde junto a un paquete indica que está cargado en la sesión de R. Para desinstalar el paquete se pueden usar el icono de la X roja de la lista izquierda o el botón **Desinstalar** situado a la derecha. Una flecha azul hacia arriba situada a la derecha de un paquete instalado actualiza el paquete si existe una versión más reciente.

    ![Pestaña paquetes instalados en las herramientas de R para el administrador de paquetes de Visual Studio](~/docs/rtvs/media/package-manager-installed.png)

- **Cargado** muestra solo los paquetes que están cargados en la sesión de R y, por lo tanto, aparecerán con un punto verde. También puede desinstalar y actualizar paquetes aquí.

    ![Pestaña paquetes cargados en las herramientas de R para el administrador de paquetes de Visual Studio](~/docs/rtvs/media/package-manager-loaded.png)

## <a name="package-locations"></a>Ubicaciones de los paquetes

Los paquetes están instalados en las siguientes ubicaciones:

- Los paquetes principales que se incluyen con RTV están instalados en `C:\Program Files\Microsoft\R Client\R_SERVER\library`
- Los paquetes adicionales están instalados en `%userprofile%\Documents\R\win-library\3.3`

