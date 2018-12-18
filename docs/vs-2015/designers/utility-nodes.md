---
title: Nodos de utilidad | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d85735c5fb355163f2003a27a96675ed097d66e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174426"
---
# <a name="utility-nodes"></a>Nodos de utilidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el Diseñador de sombras, los nodos de utilidad representan cálculos de sombreador habituales y útiles que no se ajustan perfectamente a las demás categorías. Algunos nodos de utilidad realizan operaciones simples como anexar vectores o elegir resultados condicionalmente y otros realizan operaciones complejas, como calcular contribuciones de iluminación según los modelos de iluminación populares.  
  
## <a name="utility-node-reference"></a>Referencia de nodos de utilidad  
  
|Nodo|Detalles|Propiedades|  
|----------|-------------|----------------|  
|**Anexar vector**|Crea un vector anexando las entradas especificadas.<br /><br /> **Entrada:**<br /><br /> `Vector`: `float`, `float2` o `float3`<br /> Los valores a los que se va a anexar.<br /><br /> `Value to Append`: `float`<br /> Valor que se va a anexar.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`, `float3` o `float4`, en función del tipo de entrada `Vector`<br /> El nuevo vector.|Ninguna|  
|**Fresnel**|Calcula la reducción de Fresnel según el normal de superficie especificado.<br /><br /> El valor de la reducción de Fresnel expresa en qué medida coincide el valor normal de superficie del píxel actual con el vector de visualización. Cuando los vectores están alineados, el resultado de la función es 0; el resultado se incrementa a medida que los vectores son menos similares y alcanza su valor máximo cuando los vectores son ortogonales. Se puede usar para hacer que un efecto sea más o menos aparente en función de la relación entre la orientación del píxel actual y la cámara.<br /><br /> **Entrada:**<br /><br /> `Surface Normal`: `float3`<br /> La normal de superficie del píxel actual, definida en el espacio tangente del píxel actual. Se puede usar para alterar la normal de superficie aparente, como en la asignación normal.<br /><br /> **Salida:**<br /><br /> `Output`: `float`<br /> La capacidad de reflexión del píxel actual.|**Exponent**<br /> El exponente que se usa para calcular la reducción de Fresnel.|  
|**If**|Elige condicionalmente uno de los tres resultados posibles por componente. La condición se define por la relación entre otras dos entradas especificadas.<br /><br /> Para cada componente del resultado, se elige el componente correspondiente de uno de los tres resultados potenciales en función de la relación entre los componentes correspondientes de las dos primeras entradas.<br /><br /> **Entrada:**<br /><br /> `X`: `float`, `float2`, `float3` o `float4`<br /> El valor del lado izquierdo para comparar.<br /><br /> `Y`: el mismo tipo que la entrada `X`<br /> El valor del lado derecho para comparar.<br /><br /> `X > Y`: el mismo tipo que la entrada `X`<br /> Los valores que se eligen cuando `X` es mayor que `Y`.<br /><br /> `X = Y`: el mismo tipo que la entrada `X`<br /> Los valores que se eligen cuando `X` es igual a `Y`.<br /><br /> `X < Y`: el mismo tipo que la entrada `X`<br /> Los valores que se eligen cuando `X` es menor que a `Y`.<br /><br /> **Salida:**<br /><br /> `Output`: `float3`<br /> El resultado elegido, por componente.|Ninguna|  
|**Lambert**|Calcula el color del píxel actual según el modelo de iluminación Lambert, mediante el normal de superficie especificado.<br /><br /> Este color es la suma de las contribuciones del color ambiental y la iluminación difusa bajo iluminación directa. El color ambiental se aproxima a la contribución total de iluminación indirecta, pero tiene un aspecto plano y apagado sin ayuda de iluminación adicional. La iluminación difusa hace que sea más fácil agregar forma y profundidad a un objeto.<br /><br /> **Entrada:**<br /><br /> `Surface Normal`: `float3`<br /> La normal de superficie del píxel actual, definida en el espacio tangente del píxel actual. Se puede usar para alterar la normal de superficie aparente, como en la asignación normal.<br /><br /> `Diffuse Color`: `float3`<br /> El color difuso del píxel actual, normalmente el **Color de punto**. Si no se proporciona ninguna entrada, el valor predeterminado es blanco.<br /><br /> **Salida:**<br /><br /> `Output`: `float3`<br /> El color difuso del píxel actual.|Ninguna|  
|**Vector de máscara**|Enmascara los componentes de vector especificado.<br /><br /> Se puede usar para quitar canales de color específicos de un valor de color o bien para evitar que determinados componentes afecten a cálculos subsiguientes.<br /><br /> **Entrada:**<br /><br /> `Vector`: `float4`<br /> El vector que se va a enmascarar.<br /><br /> **Salida:**<br /><br /> `Output`: `float4`<br /> El vector enmascarado.|**Rojo / X**<br /> **False** para desenmascarar el componente rojo (X). De lo contrario, **True**.<br /><br /> **Verde / Y**<br /> **False** para desenmascarar el componente verde (Y). De lo contrario, **True**.<br /><br /> **Azul / Z**<br /> **False** para desenmascarar el componente azul (Z). De lo contrario, **True**.<br /><br /> **Alfa / W**<br /> **False** para desenmascarar el componente alfa (W). De lo contrario, **True**.|  
|**Vector de reflexión**|Calcula el vector de la reflexión del píxel actual en el espacio tangente en función de la posición de la cámara.<br /><br /> Se puede usar para calcular reflexiones, coordenadas de mapa de cubo y contribuciones de la iluminación especular.<br /><br /> **Entrada:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> La normal de superficie del píxel actual, definida en el espacio tangente del píxel actual. Se puede usar para alterar la normal de superficie aparente, como en la asignación normal.<br /><br /> **Salida:**<br /><br /> `Output`: `float3`<br /> El vector de reflexión.|Ninguna|  
|**Specular**|Calcula la contribución de iluminación especular según el modelo de iluminación Phong, mediante el normal de superficie especificado.<br /><br /> La iluminación especular proporciona una apariencia reluciente y reflectante a un objeto, por ejemplo, agua, plástico o metales.<br /><br /> **Entrada:**<br /><br /> `Surface Normal`: `float3`<br /> La normal de superficie del píxel actual, definida en el espacio tangente del píxel actual. Se puede usar para alterar la normal de superficie aparente, como en la asignación normal.<br /><br /> **Salida:**<br /><br /> `Output`: `float3`<br /> La contribución de color de los reflejos especulares.|Ninguna|



