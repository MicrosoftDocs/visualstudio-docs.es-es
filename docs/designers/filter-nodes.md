---
title: Nodos de filtro
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfc74287706976f96a5e565bef3da1493cd44866
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769282"
---
# <a name="filter-nodes"></a>Nodos de filtro

En el Diseñador de sombras, los nodos de filtro transforman una entrada, por ejemplo, una muestra de color o de textura, en un valor de color figurativo. Estos valores de color figurativo se usan normalmente en representación no fotorrealista o como componentes en otros efectos visuales.

## <a name="filter-node-reference"></a>Referencia de nodos de filtro

|Nodo|Detalles|Propiedades|
|----------|-------------|----------------|
|**Desenfoque**|Desenfoca píxeles en una textura mediante una función gausiana.<br /><br /> Se puede usar para reducir el detalle de color y el ruido de la textura.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas de la textura para probar.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> El valor de color difuminado.|**Textura**<br /> El registro de textura asociado a la muestra que se usa durante el desenfoque.|
|**Desaturar**|Reduce la cantidad de color en el color especificado.<br /><br /> A medida que se elimina color, el valor de color se aproxima a su equivalente de escala de grises.<br /><br /> **Entrada:**<br /><br /> `RGB`: `float3`<br /> El color que se va a desaturar.<br /><br /> `Percent`: `float`<br /> El porcentaje de color que se va a quitar, expresado como un valor normalizado en el intervalo [0, 1].<br /><br /> **Resultado:**<br /><br /> `Output`: `float3`<br /> El color desaturado.|**Luminancia**<br /> Las ponderaciones asignadas a los componentes de color rojo, verde y azul.|
|**Detección de bordes**|Detecta los bordes de una textura mediante un detector de bordes Canny. Los píxeles del borde se representan como blanco y los píxeles que no son del borde se representan como negro.<br /><br /> Se puede usar para identificar los bordes de una textura para poder usar efectos adicionales para tratar los píxeles del borde.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas de la textura para probar.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Blanco si la textura está en un borde. De lo contrario, negro.|**Textura**<br /> El registro de textura asociado a la muestra que se usa durante la detección de bordes.|
|**Dar nitidez**|Da nitidez a una textura.<br /><br /> Se puede usar para resaltar detalles finos en una textura.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas de la textura para probar.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> El valor de color difuminado.|**Textura**<br /> El registro de textura asociado a la muestra que se usa durante la operación de dar nitidez.|