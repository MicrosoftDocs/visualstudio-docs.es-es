---
title: Métricas de código-intervalo de índice de mantenimiento y significado
ms.date: 1/8/2021
description: Obtenga información sobre la métrica de rango de índice de mantenimiento para las métricas de código en Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa825b439b75606da136635d5816ac3e19ea8392
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860469"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Métricas de código-intervalo de índice de mantenimiento y significado

Pregunta: el índice de mantenimiento se ha restablecido para estar entre 0 y 100. ¿Cómo y por qué se hizo esto?

La métrica se calculó originalmente de la siguiente manera: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

El uso de esta fórmula significaba que está comprendido entre 171 y un número negativo sin enlazar.  Dado que el código se repite en 0, era bastante difícil mantener el código y la diferencia entre el código en 0 y algún valor negativo no era útil.  Como resultado de la útil disminución de los números negativos y el deseo de mantener la métrica lo más clara posible, hemos decidido tratar todos 0 o menos índices como 0 y, a continuación, volver a basar el intervalo 171 o menos para que sea de 0 a 100. Por esta razón, la fórmula que usamos es la siguiente:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Además, hemos decidido ser conservador con los umbrales.  El deseo es que si el índice se mostrase en rojo, nos indicaría un alto grado de confianza de que se produjo un problema con el código.  Esto nos dio los siguientes umbrales:

En el caso de los umbrales, hemos decidido dividir este intervalo 0-100 80-20 para mantener el nivel de ruido bajo y el código marcado como sospechoso. Hemos usado los siguientes umbrales:

- 0-9 = rojo
- 10-19 = amarillo
- 20-100 = verde
