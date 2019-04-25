---
title: Navegador de utilización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e2562e86af36d935679916c2bfb9669be1758d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615239"
---
# <a name="utilization-navigator"></a>Navegador de utilización
Puede utilizar el navegador de utilización del visualizador de simultaneidad para seleccionar un intervalo de tiempo en un seguimiento. El visualizador de simultaneidad muestra la utilización de núcleos de CPU por el proceso de destino a lo largo del tiempo. Esto hace más fácil examinar patrones de uso de CPU y también permite la comparación entre los datos de uso y los datos en otras vistas. El navegador de utilización aparece en la parte superior de cada vista en el visualizador de simultaneidad. En la siguiente ilustración se muestra el navegador de utilización.

 ![Navegador de uso que muestra el marco de tiempo seleccionado](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Navegador de uso y un marco de tiempo seleccionado

 En la ilustración, el intervalo seleccionado está definido por un rectángulo rojo, conocido como la *miniatura*.

 A continuación se explica cómo puede utilizar el navegador de utilización para manipular el intervalo de tiempo mostrado:

- Puede desplazarse arrastrando la miniatura a la izquierda o a la derecha. (Teclado: Mueva el foco a la miniatura y después presione la tecla de dirección izquierda o derecha).

- Puede cambiar la extensión del intervalo arrastrando uno de los controladores. (Teclado: Mueva el foco a un manipulador y después presione la tecla de dirección izquierda o derecha).

  Si cambia el intervalo mediante un control de zoom del visualizador de simultaneidad diferente, el navegador de utilización se actualiza para reflejar el cambio.