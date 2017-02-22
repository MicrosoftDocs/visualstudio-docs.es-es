---
title: "Nodos de filtro | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Nodos de filtro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador de sombras, los nodos de filtrado transforman una entrada, por ejemplo, un color o muestra de textura un valor de color figurado.  Estos valores de color figurados se suelen utilizar en la representación no fotorrealista o como componentes en otros efectos visuales.  
  
## Referencia al nodo de filtro  
  
|Nodo|Detalles|Propiedades|  
|----------|--------------|-----------------|  
|**Desenfoque**|Enmascara los píxeles en una textura utilizando una función de Gaussian.<br /><br /> Puede utilizar esto para reducir el detalle colores o el ruido en una textura.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas del elemento de textura a probar.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> El valor de color enmascarado.|**Textura**<br /> El registro de textura que se asocia el dechado que se utiliza durante desenfoque.|  
|**Desaturar**|Reduce la cantidad de color en el color especificado.<br /><br /> A medida que se elimina color, el valor de color se aproxima a su equivalente de escala de grises.<br /><br /> **Entrada:**<br /><br /> `RGB`: `float3`<br /> El color que se va desaturar.<br /><br /> `Percent`: `float`<br /> El porcentaje de color a quitar, expresado como un valor normalizado en el intervalo \[0, 1\].<br /><br /> **Resultado:**<br /><br /> `Output`: `float3`<br /> El color desaturado.|**Luminancia**<br /> Ponderaciones asignadas a los componentes de color rojo, verde y azul.|  
|**Detección de bordes**|Detecta los bordes en una textura mediante un detector de bordes Canny.  Los píxeles del borde se representan en blanco; los píxeles que no están en el borde se representan en negro.<br /><br /> Se puede usar para identificar los bordes de una textura con el fin de poder usar efectos adicionales para tratar píxeles del borde.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas del elemento de textura a probar.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Blanco si la textura está en un borde; en caso contrario, negro.|**Textura**<br /> Registro de textura asociado a la muestra que se usa durante la detección de bordes.|  
|**Dar nitidez**|Afila una textura.<br /><br /> Puede utilizar esto para resaltar los detalles finos en una textura.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas del elemento de textura a probar.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> El valor de color enmascarado.|**Textura**<br /> El registro de textura que se asocia el dechado que se utiliza durante la afiladura.|