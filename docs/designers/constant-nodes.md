---
title: "Nodos de constante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Nodos de constante
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador de sombras, los nodos constantes representan valores literales y atributos de vértices interpolados los cálculos del sombreador de píxeles.  Dado que los atributos de vértices se interpolan y, por ello, son diferentes para cada píxel, cada instancia del sombreador de píxeles recibe una versión diferente de la constante.  Esto proporciona a cada píxel una apariencia única.  
  
## Interpolación de atributos de vértices  
 La imagen de una escena 3D en un juego o una aplicación se crea transformando matemáticamente un número de objetos, definidos por vértices, atributos de vértices y definiciones de primitivas, en píxeles en pantalla.  Toda la información necesaria para asignar a un píxel su aspecto único se proporciona con los atributos del vértice, que se mezclan entre sí según la proximidad del píxel a los distintos vértices que componen su *primitivo*.  Un primitivo es un elemento básico de representación; es decir, una forma simple como un punto, una línea o un triángulo.  Un píxel que está muy cerca de solo uno de los vértices recibe las constantes que son casi idénticas a ese vértice, pero un píxel uniformemente separado entre todos los vértices de un primitivo recibe las constantes que son el promedio de esos vértices.  En la programación de gráficos, las constantes que reciben los píxeles se dice que se *interpolan*.  Proporcionar datos constantes para píxeles de esta manera genera calidad visual muy buena y al mismo tiempo reduce los requisitos de la superficie de memoria y de ancho de banda.  
  
 Aunque cada instancia del sombreador de píxeles recibe solo un conjunto de valores constantes y no puede cambiar estos valores, diferentes instancias del sombreador de píxeles reciben diferentes conjuntos de datos constantes.  Este diseño permite a un programa sombreador generar una salida de color distinta para cada píxel de la primitiva.  
  
## Referencia de constante del nodo  
  
|Nodo|Detalles|Propiedades|  
|----------|--------------|-----------------|  
|**vector de la cámara**|Vector que se extiende desde el píxel actual hasta la cámara en el espacio global.<br /><br /> Se puede usar para calcular las reflexiones en el espacio global.<br /><br /> **Resultados**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a la cámara.|None|  
|**Constante de color**|Valor constante de color.<br /><br /> **Resultados**<br /><br /> `Output`: `float4`<br /> Valor del color.|**Resultados**<br /> Valor del color.|  
|**Constante**|Valor escalar constante.<br /><br /> **Resultados**<br /><br /> `Output`: `float`<br /> Valor escalar.|**Resultados**<br /> Valor escalar.|  
|**Constante 2D**|Constante del vector de dos componentes.<br /><br /> **Resultados**<br /><br /> `Output`: `float2`<br /> Valor del vector.|**Resultados**<br /> Valor del vector.|  
|**Constante 3D**|Constante del vector de tres componentes.<br /><br /> **Resultados**<br /><br /> `Output`: `float3`<br /> Valor del vector.|**Resultados**<br /> Valor del vector.|  
|**Constante 4D**|Constante del vector de cuatro componentes.<br /><br /> **Resultados**<br /><br /> `Output`: `float4`<br /> Valor del color.|**Resultados**<br /> Valor del vector.|  
|**posición normalizada**|Posición del píxel actual expresada en coordenadas de dispositivo normalizadas.<br /><br /> Las coordenadas x e y tienen valores en el intervalo \[\- 1, 1\], la coordenada z tiene un valor en el intervalo \[0, 1\], y el componente w contiene el valor de profundidad de punto en espacio de vista; w no está normalizado.<br /><br /> **Resultados**<br /><br /> `Output`: `float4`<br /> Posición del píxel actual.|None|  
|**punto Color**|El color difuso del píxel actual, que es una combinación del color difuso del material y los atributos de color del vértice.<br /><br /> **Resultados**<br /><br /> `Output`: `float4`<br /> Color difuso del píxel actual.|None|  
|**Profundidad de punto**|Profundidad del píxel actual en el espacio de vistas.<br /><br /> **Resultados**<br /><br /> `Output`: `float`<br /> La profundidad del píxel actual.|None|  
|**Profundidad normalizada de punto**|Profundidad del píxel actual, expresada en coordenadas de dispositivo normalizadas.<br /><br /> El resultado tiene un valor comprendido en el intervalo de \[0, 1\].<br /><br /> **Resultados**<br /><br /> `Output`: `float`<br /> La profundidad del píxel actual.|None|  
|**Posición de la pantalla**|Posición del píxel actual expresada en coordenadas de la pantalla.<br /><br /> Las coordenadas de la pantalla se basan en la ventanilla actual.  Los componentes x e y contienen las coordenadas de la pantalla, el componente z contiene la profundidad normalizada en un intervalo \[0, 1\], y el componente w contiene el valor de profundidad en el espacio de vista.<br /><br /> **Resultados**<br /><br /> `Output`: `float4`<br /> Posición del píxel actual.|None|  
|**normal superficial**|Valor normal de superficie del píxel actual en el espacio de objeto.<br /><br /> Se puede usar para calcular las reflexiones y las contribuciones de la iluminación en el espacio de objeto.<br /><br /> **Resultados**<br /><br /> `Output`: `float3`<br /> Valor normal de superficie del píxel actual.|None|  
|**Vector de la cámara de espacio tangentes**|Vector que se extiende desde el píxel actual hasta la cámara en el espacio tangente.<br /><br /> Se puede usar para calcular las reflexiones en el espacio tangente.<br /><br /> **Resultados**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a la cámara.|None|  
|**Dirección de la luz de espacio tangentes**|Vector que define la dirección en la que se proyecta la luz desde una fuente de luz en el espacio tangente del píxel actual.<br /><br /> Se puede usar para calcular la iluminación y las contribuciones especulares en el espacio tangente.<br /><br /> **Resultado:**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a una fuente de luz.|None|  
|**mundo normal**|Valor normal de superficie del píxel actual en el espacio global.<br /><br /> Se puede usar para calcular las reflexiones y las contribuciones de la iluminación en el espacio global.<br /><br /> **Resultados**<br /><br /> `Output`: `float3`<br /> Valor normal de superficie del píxel actual.|None|  
|**Posición del mundo**|Posición del píxel actual en el espacio global.<br /><br /> **Resultados**<br /><br /> `Output`: `float4`<br /> Posición del píxel actual.|None|