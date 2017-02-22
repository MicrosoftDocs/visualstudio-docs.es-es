---
title: "Nodos de textura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Nodos de textura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador de sombras, los nodos de textura muestrean varios tipos de textura y geometrías y generan o transforman coordenadas de textura.  Las texturas proporcionan color y detalles de iluminación en objetos.  
  
## Referencia de nodo de textura  
  
|Nodo|Detalles|Propiedades|  
|----------|--------------|-----------------|  
|**Muestra de mapa de cubo**|Toma una muestra de color de un mapa de cubo en las coordenadas especificadas.<br /><br /> Un mapa de este tipo se puede usar para proporcionar detalles de color para efectos de reflexión, o bien aplicar una textura a un objeto esférico con menor distorsión que una textura 2D.<br /><br /> **Entrada:**<br /><br /> `UVW`: `float3`<br /> Vector que especifica la ubicación en el cubo de textura donde se toma el ejemplo.  El ejemplo se toma donde este vector forma una intersección con el cubo.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Ejemplo de color.|**Textura**<br /> Registro de textura asociado a la muestra.|  
|**Ejemplo normal de mapa**|Toma una muestra normal de un mapa normal en 2D en las coordenadas especificadas<br /><br /> Un mapa normal se puede usar para simular la apariencia de un detalle geométrico adicional en la superficie de un objeto.  Los mapas normales contienen datos empaquetados que representan un vector unitario en lugar de datos de color.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas donde se toma el ejemplo.<br /><br /> **Resultado:**<br /><br /> `Output`: `float3`<br /> El ejemplo normal.|**Ajuste de ejes**<br /> Factor usado para ajustar la muestra de mapa normal para diestros o zurdos.<br /><br /> **Textura**<br /> Registro de textura asociado a la muestra.|  
|**panorámica ULTRAVIOLETA**|Critica las coordenadas especificadas de textura en función del tiempo.<br /><br /> Se puede usar para mover un mapa normal o de textura por la superficie de un objeto.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas para aplicar la panorámica.<br /><br /> `Time`: `float`<br /> El tiempo de aplicar la panorámica por, en segundos.<br /><br /> **Resultado:**<br /><br /> `Output`: `float2`<br /> Las coordenadas distribuidas.|**Velocidad X**<br /> Número de elementos de textura distribuidos en el eje x por segundo.<br /><br /> **Velocidad Y**<br /> Número de elementos de textura distribuidos en el eje y por segundo.|  
|**paralaje ULTRAVIOLETA**|Desplaza las coordenadas de textura especificadas como función de alto y ángulo de visión.<br /><br /> El efecto que esto crea se conoce como *asignación de paralaje* o desplazamiento virtual.  Se puede usar para crear una ilusión de profundidad en una superficie plana.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas a desplazar.<br /><br /> `Height`: `float`<br /> El valor de heightmap asociado con las coordenadas `UV`.<br /><br /> **Resultado:**<br /><br /> `Output`: `float2`<br /> Las coordenadas desplazadas.|**Plano de profundidad**<br /> Profundidad de referencia para el efecto de paralaje.  de forma predeterminada, el valor es 0.5.  Los valores inferiores elevan la textura y los superiores la ocultan en la superficie.<br /><br /> **Escala de profundidad**<br /> La escala del efecto de paralaje.  Esto hace que la profundidad aparente sea más o menos pronunciada.  El intervalo de valores típicos oscila entre 0,02 y 0,1.|  
|**Active ULTRAVIOLETA**|Gira las coordenadas de textura especificadas alrededor de un punto central como una función de tiempo.<br /><br /> Se puede usar para girar un mapa normal o de textura en la superficie de un objeto.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas para el giro.<br /><br /> `Time`: `float`<br /> El tiempo de aplicar la panorámica por, en segundos.<br /><br /> **Resultado:**<br /><br /> `Output`: `float2`<br /> Las coordenadas giradas.|**Centrar X**<br /> Coordenada x que define el centro de rotación.<br /><br /> **Centrar Y**<br /> Coordenada y que define el centro de rotación.<br /><br /> **Velocidad**<br /> Ángulo, en radianes, por el que la textura rota por segundo.|  
|**Coordenadas de textura**|Las coordenadas de textura del píxel actual.<br /><br /> Las coordenadas de textura quedan determinadas al interpolar entre los atributos de coordenada de textura de los vértices cercanos.  Puede considerarse como la posición del píxel actual en el espacio de textura.<br /><br /> **Resultado:**<br /><br /> `Output`: `float2`<br /> Las coordenadas de textura.|None|  
|**Dimensiones de textura**|Genera el ancho y alto de un 2d mapa de textura.<br /><br /> Puede utilizar las dimensiones de textura para ver el ancho y alto de textura en un sombreador.<br /><br /> **Resultado:**<br /><br /> `Output`: `float2`<br /> El ancho y alto de textura, expresados como vector.  El ancho se almacena en el primer elemento de vector.  El alto se almacena en el segundo elemento.|**Textura**<br /> El registro de textura que está asociado a las dimensiones de textura.|  
|**Delta del elemento de textura**|Genera el delta \(distancia\) entre los texels de un 2d mapa de textura.<br /><br /> Puede utilizar el delta de texel a valores vecinos de texel de ejemplo en un sombreador.<br /><br /> **Resultado:**<br /><br /> `Output`: `float2`<br /> El delta \(distancia\) de un texel al texel siguiente \(que desplaza diagonalmente en la dirección positiva\), expresado como un vector de espacio normalizado de textura.  Puede derivar las posiciones de todos los texels vecinos selectivamente omitiendo o negando las coordenadas de o de V delta.|**Textura**<br /> El registro de textura que se asocia el delta de texel.|  
|**Ejemplo de textura**|Toma una muestra de color de un mapa de textura en 2D en las coordenadas especificadas.<br /><br /> Puede usar un mapa de texturas para proporcionar detalles de color sobre la superficie de un objeto.<br /><br /> **Entrada:**<br /><br /> `UV`: `float2`<br /> Las coordenadas donde se toma el ejemplo.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Ejemplo de color.|**Textura**<br /> Registro de textura asociado a la muestra.|