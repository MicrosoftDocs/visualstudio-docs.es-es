---
title: Navegador de utilización | Microsoft Docs
description: Obtenga información sobre cómo puede usar el navegador de utilización del visualizador de simultaneidad para seleccionar un intervalo de tiempo en un seguimiento.
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
ms.openlocfilehash: 9f209098200333e91f0e5baf9c7a2b73b4a3202f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723223"
---
# <a name="utilization-navigator"></a>Navegador de utilización
Puede utilizar el navegador de utilización del visualizador de simultaneidad para seleccionar un intervalo de tiempo en un seguimiento. El visualizador de simultaneidad muestra la utilización de núcleos de CPU por el proceso de destino a lo largo del tiempo. Esto hace más fácil examinar patrones de uso de CPU y también permite la comparación entre los datos de uso y los datos en otras vistas. El navegador de utilización aparece en la parte superior de cada vista en el visualizador de simultaneidad. En la siguiente ilustración se muestra el navegador de utilización.

 ![Navegador de uso que muestra el período de tiempo seleccionado](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Navegador de uso y un período de tiempo seleccionado

 En la ilustración, el intervalo seleccionado está definido por un rectángulo rojo, conocido como la *miniatura*.

 A continuación se explica cómo puede utilizar el navegador de utilización para manipular el intervalo de tiempo mostrado:

- Puede desplazarse arrastrando la miniatura a la izquierda o a la derecha. (Teclado: mueva el foco a la miniatura y después pulse la tecla de dirección izquierda o derecha.)

- Puede cambiar la extensión del intervalo arrastrando uno de los controladores. (Teclado: mueva el foco al control y después pulse la tecla de dirección izquierda o derecha.)

  Si cambia el intervalo mediante un control de zoom del visualizador de simultaneidad diferente, el navegador de utilización se actualiza para reflejar el cambio.