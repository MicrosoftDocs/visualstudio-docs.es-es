---
title: Nodos de textura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e43329cb15eaf41ccb8859521bd45eff6f749c10
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187761"
---
# <a name="texture-nodes"></a>Nodos de textura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el Diseñador de sombras, los nodos de textura muestrean diversos tipos de textura y geometrías, y generan o transforman las coordenadas de textura. Las texturas proporcionan detalles de color e iluminación a los objetos.  
  
## <a name="texture-node-reference"></a>Referencia de nodos de textura  
  
|Nodo|Detalles|Properties (Propiedades)|  
|----------|-------------|----------------|  
|**Muestra de mapa de cubo**|Toma una muestra de color de un mapa de cubo en las coordenadas especificadas.<br /><br /> Un mapa de cubo se puede usar para proporcionar detalles de color para efectos de reflexión o para aplicar textura a un objeto esférico con menor distorsión que una textura 2D.<br /><br /> **Entrada:**<br /><br /> `UVW`: `float3`<br /> Un vector que especifica la ubicación en el cubo de textura de la que se toma la muestra. La muestra se toma en la intersección de este vector y el cubo.<br /><br /> **Salida:**<br /><br /> `Output`: `float4`<br /> El ejemplo de color.|**Textura**<br /> El registro de textura asociado a la muestra.|  
|**Muestra de mapa normal**|Toma una muestra normal de un mapa normal en 2D en las coordenadas especificadas.<br /><br /> Un mapa normal se puede usar para simular la apariencia de un detalle geométrico adicional en la superficie de un objeto. Los mapas normales contienen datos empaquetados que representan un vector unitario en lugar de datos de color.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas en las que se toma la muestra.<br /><br /> **Salida:**<br /><br /> `Output`: `float3`<br /> La muestra normal.|**Ajuste de ejes**<br /> El factor que se usa para ajustar la muestra de mapa normal para diestros o zurdos.<br /><br /> **Textura**<br /> El registro de textura asociado a la muestra.|  
|**UV de panorámica**|Mueve en panorámica las coordenadas de textura especificadas como una función de tiempo.<br /><br /> Se puede usar para mover una textura o un mapa normal a través de la superficie de un objeto.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas para el movimiento panorámico.<br /><br /> `Time`: `float`<br /> La duración del movimiento panorámico, en segundos.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`<br /> Las coordenadas de la panorámica.|**Velocidad X**<br /> Número de elementos de textura distribuidos en el eje x por segundo.<br /><br /> **Velocidad Y**<br /> Número de elementos de textura distribuidos en el eje y por segundo.|  
|**UV de paralaje**|Desplaza las coordenadas de textura especificadas como una función del alto y el ángulo de visión.<br /><br /> El efecto se conoce como *asignación de paralaje* o de desplazamiento virtual. Se puede usar para crear una ilusión de profundidad en una superficie plana.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas para el desplazamiento.<br /><br /> `Height`: `float`<br /> El valor de mapa de elevación que está asociado a las coordenadas `UV`.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`<br /> Las coordenadas desplazadas.|**Plano de profundidad**<br /> La profundidad del efecto de paralaje. De forma predeterminada, el valor es 0,5. Los valores menores levantan la textura y los valores mayores la hunden en la superficie.<br /><br /> **Escala de profundidad**<br /> La escala del efecto de paralaje. Esto hace que la profundidad aparente sea más o menos pronunciada. Los valores típicos oscilan entre 0,02 y 0,1.|  
|**UV de rotación**|Gira las coordenadas de textura especificadas alrededor de un punto central como una función de tiempo.<br /><br /> Se puede usar para girar una textura o un mapa normal en la superficie de un objeto.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas para la rotación.<br /><br /> `Time`: `float`<br /> La duración del movimiento panorámico, en segundos.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`<br /> Las coordenadas giradas.|**Centrar X**<br /> Coordenada x que define el centro de rotación.<br /><br /> **Centrar Y**<br /> Coordenada y que define el centro de rotación.<br /><br /> **Velocidad**<br /> Ángulo, en radianes, por el que la textura rota por segundo.|  
|**Coordenada de textura**|Las coordenadas de textura del píxel actual.<br /><br /> Las coordenadas de textura determinadas al interpolar entre los atributos de coordenada de textura de los vértices cercanos. Puede considerarse como la posición del píxel actual en el espacio de textura.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`<br /> Las coordenadas de textura.|None|  
|**Dimensiones de textura**|Muestra el ancho y el alto de un mapa de textura 2D.<br /><br /> Se pueden usar las dimensiones de textura para tener en cuenta el ancho y el alto de la textura en un sombreador.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`<br /> El ancho y el alto de la textura, expresados como un vector. El ancho se almacena en el primer elemento del vector. El alto se almacena en el segundo elemento.|**Textura**<br /> El registro de textura que está asociado con las dimensiones de textura.|  
|**Delta del elemento de textura**|Muestra el delta (distancia) entre los elementos de textura de un mapa de textura 2D.<br /><br /> Se puede usar el delta del elemento de textura para muestrear valores de elemento de textura contiguos de un sombreador.<br /><br /> **Salida:**<br /><br /> `Output`: `float2`<br /> El delta (distancia) desde un elemento de textura al siguiente (con movimiento diagonal en la dirección positiva), expresado como un vector en el espacio de textura normalizado. Se pueden derivar las posiciones de todos los elementos de textura contiguos omitiendo o negando de forma selectiva las coordenadas U o V del delta.|**Textura**<br /> El registro de textura asociado al delta del elemento de textura.|  
|**Muestra de textura**|Toma una muestra de color de un mapa de texturas en 2D en las coordenadas especificadas.<br /><br /> Se puede usar un mapa de texturas para proporcionar detalles de color en la superficie de un objeto.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas en las que se toma la muestra.<br /><br /> **Salida:**<br /><br /> `Output`: `float4`<br /> El ejemplo de color.|**Textura**<br /> El registro de textura asociado a la muestra.|
