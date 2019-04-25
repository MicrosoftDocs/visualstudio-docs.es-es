---
title: Nodos de constante
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af585d77176e52442d5eee37f3d16fcbafd31ef9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910810"
---
# <a name="constant-nodes"></a>Nodos de constante

En el Diseñador de sombras, los nodos de constante representan valores literales y atributos de vértice interpolados en los cálculos de sombreador de píxeles. Dado que los atributos de vértice se interpolan, y por tanto son diferentes para cada píxel, cada instancia de sombreador de píxeles recibe una versión diferente de la constante. Esto proporciona a cada píxel una apariencia única.

## <a name="vertex-attribute-interpolation"></a>Interpolación de atributos de vértice

La imagen de una escena 3D en un juego o aplicación se crea mediante la transformación matemática de un número de objetos —que se definen por los vértices, atributos de vértice y definiciones primitivas— en píxeles en pantalla. Toda la información necesaria para proporcionar a un píxel su aspecto único se proporciona a través de los atributos de vértice, que se fusionan según la proximidad del píxel a los vértices diferentes que componen su *primitiva*. Una primitiva es un elemento de representación básico, es decir, una forma sencilla como un punto, una línea o un triángulo. Un píxel que está muy cerca de solo uno de los vértices recibe constantes que son casi idénticas a ese vértice, pero un píxel que tenga un espaciado uniforme entre todos los vértices de una primitiva recibe constantes que son el promedio de esos vértices. En la programación de gráficos, las constantes que reciben los píxeles se consideran *interpoladas*. Proporcionar datos constantes a los píxeles de este modo produce muy buena calidad visual y al mismo tiempo reduce los requisitos de superficie de memoria y ancho de banda.

Aunque cada instancia de sombreador de píxeles recibe solo un conjunto de valores constantes y no puede cambiar estos valores, las instancias de sombreador de píxeles diferentes reciben conjuntos diferentes de datos constantes. Este diseño permite que un programa de sombreador produzca una salida de color diferente para cada píxel de la primitiva.

## <a name="constant-node-reference"></a>Referencia de nodos de constante

|Nodo|Detalles|Propiedades|
|----------|-------------|----------------|
|**Vector de cámara**|El vector que se extiende desde el píxel actual a la cámara en el espacio global.<br /><br /> Puede usarlo para calcular los reflejos en el espacio global.<br /><br /> **Salida**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a la cámara.|Ninguna|
|**Constante de color**|Un valor de color constante.<br /><br /> **Salida**<br /><br /> `Output`: `float4`<br /> Valor del color.|**Salida**<br /> Valor del color.|
|**Constante**|Un valor escalar constante.<br /><br /> **Salida**<br /><br /> `Output`: `float`<br /> Valor escalar.|**Salida**<br /> Valor escalar.|
|**Constante 2D**|Una constante de vector de dos componentes.<br /><br /> **Salida**<br /><br /> `Output`: `float2`<br /> Valor del vector.|**Salida**<br /> Valor del vector.|
|**Constante 3D**|Una constante de vector de tres componentes.<br /><br /> **Salida**<br /><br /> `Output`: `float3`<br /> Valor del vector.|**Salida**<br /> Valor del vector.|
|**Constante 4D**|Una constante de vector de cuatro componentes.<br /><br /> **Salida**<br /><br /> `Output`: `float4`<br /> Valor del color.|**Salida**<br /> Valor del vector.|
|**Posición normalizada**|La posición del píxel actual, expresada en coordenadas de dispositivo normalizadas.<br /><br /> Las coordenadas X e Y tienen valores en el intervalo de [-1, 1], la coordenada Z tiene un valor en el intervalo de [0, 1] y el componente W contiene el valor de profundidad de punto en el espacio de vista y no está normalizado.<br /><br /> **Salida**<br /><br /> `Output`: `float4`<br /> La posición del píxel actual.|Ninguna|
|**Color de punto**|El color difuso del píxel actual, que es una combinación de los atributos de color difuso de material y de color de vértice.<br /><br /> **Salida**<br /><br /> `Output`: `float4`<br /> El color difuso del píxel actual.|Ninguna|
|**Profundidad de punto**|La profundidad del píxel actual en el espacio de la vista.<br /><br /> **Salida**<br /><br /> `Output`: `float`<br /> La profundidad del píxel actual.|Ninguna|
|**Profundidad de punto normalizada**|La profundidad del píxel actual, expresada en coordenadas de dispositivo normalizadas.<br /><br /> El resultado tiene un valor en el intervalo de [0, 1].<br /><br /> **Salida**<br /><br /> `Output`: `float`<br /> La profundidad del píxel actual.|Ninguna|
|**Posición de pantalla**|La posición del píxel actual, expresada en coordenadas de pantalla.<br /><br /> Las coordenadas de pantalla se basan en la ventanilla actual. Los componentes X e Y contienen las coordenadas de pantalla, el componente Z contiene la profundidad normalizada en un intervalo de [0, 1] y el componente W contiene el valor de profundidad en el espacio de vista.<br /><br /> **Salida**<br /><br /> `Output`: `float4`<br /> La posición del píxel actual.|Ninguna|
|**Normal a la superficie**|El valor normal a la superficie del píxel actual en el espacio de objeto.<br /><br /> Se puede usar para calcular las reflexiones y las contribuciones de la iluminación en el espacio de objeto.<br /><br /> **Salida**<br /><br /> `Output`: `float3`<br /> El valor normal a la superficie del píxel actual.|Ninguna|
|**Vector de cámara de espacio tangente**|El vector que se extiende desde el píxel actual a la cámara en el espacio tangente.<br /><br /> Se puede usar para calcular las reflexiones en el espacio tangente.<br /><br /> **Salida**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a la cámara.|Ninguna|
|**Dirección de la luz de espacio tangente**|El vector que define la dirección en la que se proyecta la luz desde una fuente de luz en el espacio tangente del píxel actual.<br /><br /> Se puede usar para calcular las contribuciones de reflexión especular y de iluminación en el espacio tangente.<br /><br /> **Salida:**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a una fuente de luz.|Ninguna|
|**Normal global**|El valor normal a la superficie del píxel actual en el espacio global.<br /><br /> Se puede usar para calcular las reflexiones y las contribuciones de la iluminación en el espacio global.<br /><br /> **Resultado**<br /><br /> `Output`: `float3`<br /> El valor normal a la superficie del píxel actual.|Ninguna|
|**Posición global**|Posición del píxel actual en el espacio global.<br /><br /> **Salida**<br /><br /> `Output`: `float4`<br /> La posición del píxel actual.|Ninguna|