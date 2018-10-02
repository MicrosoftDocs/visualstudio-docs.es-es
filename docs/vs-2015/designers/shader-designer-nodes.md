---
title: Nodos del Diseñador de sombras | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f718faebef46308cf74847f75b3a05cd12386704
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577054"
---
# <a name="shader-designer-nodes"></a>Nodos del Diseñador de sombras
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [nodos del Diseñador de sombras](https://docs.microsoft.com/visualstudio/designers/shader-designer-nodes).  
  
Los artículos de esta sección de la documentación contienen información sobre los distintos nodos del Diseñador de sombras que puede usar para crear efectos gráficos.  
  
## <a name="nodes-and-node-types"></a>Nodos y tipos de nodo  
 El Diseñador de sombras representa los efectos visuales como un gráfico. Estos gráficos se generan a partir de nodos que se eligen de manera específica y se conectan de forma precisa para lograr el efecto buscado. Cada nodo representa un fragmento de información o una función matemática, y las conexiones entre ellos representan cómo fluye la información a través del gráfico para generar el resultado. El Diseñador de sombras proporciona seis tipos de nodo diferentes (filtros, nodos de textura, parámetros, constantes, nodos de utilidad y nodos matemáticos) y varios nodos individuales pertenecen a cada tipo. En el resto de los artículos de esta sección se describen estos nodos y tipos de nodo; vea los vínculos al final de este documento.  
  
## <a name="node-structure"></a>Estructura de los nodos  
 Todos los nodos se componen de una combinación de elementos comunes. Cada nodo tiene al menos un terminal de salida en el lado derecho (excepto el nodo de color final, que representa la salida del sombreador). Los nodos que representan cálculos o muestras de textura tienen terminales de entrada en el lado izquierdo, pero los nodos que representan información no tienen terminales de entrada. Las terminales de salida se conectan a las terminales de entrada para mover información de un nodo a otro.  
  
### <a name="promotion-of-inputs"></a>Promoción de entradas  
 Dado que en última instancia el Diseñador de sombras debe generar código fuente HLSL para que el efecto se pueda usar en un juego o aplicación, los nodos del Diseñador de sombras están sujetos a las reglas de promoción de tipos que se usan en HLSL. Como el hardware gráfico funciona principalmente sobre valores de punto flotante, no es habitual la promoción entre tipos diferentes, por ejemplo, de `int` a `float` o de `float` a `double`. En su lugar, como el hardware gráfico usa la misma operación en varios fragmentos de información a la vez, puede producirse un tipo de promoción diferente en la que la entrada más corta de varias entradas se alarga para que coincida con el tamaño de la entrada más larga. La forma en que se alargue depende del tipo de la entrada y también de la propia operación:  
  
-   **Si el tipo más pequeño es un valor escalar, entonces:**  
  
     el valor de la expresión escalar se replica en un vector que es del mismo tamaño que la entrada más grande. Por ejemplo, la entrada escalar 5,0 se convierte en el vector (5,0, 5,0, 5,0) cuando la entrada más grande de la operación es un vector de tres elementos, sea cual sea la operación.  
  
-   **Si el tipo más pequeño es un vector y la operación es de multiplicación (\*, /, %, etc.), entonces:**  
  
     el valor del vector se copia en los elementos iniciales de un vector del mismo tamaño que la entrada más grande, y los elementos finales se establecen en 1,0. Por ejemplo, la entrada de vector (5,0, 5,0) se convierte en el vector (5,0, 5,0, 1,0, 1,0) cuando se multiplica por un vector de cuatro elementos. Esto conserva el tercer y cuarto elemento de la salida mediante el uso de la identidad de multiplicación, 1,0.  
  
-   **Si el tipo más pequeño es un vector y la operación es de suma (+, -, etc.), entonces:**  
  
     el valor del vector se copia en los elementos iniciales de un vector del mismo tamaño que la entrada más grande, y los elementos finales se establecen en 0,0. Por ejemplo, la entrada de vector (5,0, 5,0) se convierte en el vector (5,0, 5,0, 0,0, 0,0) cuando se suma a un vector de cuatro elementos. Esto conserva el tercer y cuarto elemento de la salida mediante el uso de la identidad de suma, 0,0.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Nodos de constante](../designers/constant-nodes.md)|Describe los nodos que se pueden usar para representar valores literales y la información de estado de vértice interpolada en los cálculos del sombreador. Como el estado de los vértices se interpola, y por tanto es diferente para cada píxel, cada instancia de sombreador de píxeles recibe una versión diferente de la constante.|  
|[Nodos de parámetros](../designers/parameter-nodes.md)|Describe los nodos que se pueden usar para representar la posición de la cámara, propiedades de los materiales, parámetros de iluminación, hora y otra información de estado de la aplicación en los cálculos del sombreador.|  
|[Nodos de textura](../designers/texture-nodes.md)|Describe los nodos que se pueden usar para muestrear diversos tipos de textura y geometrías, y formas habituales de generar o transformar las coordenadas de textura.|  
|[Nodos matemáticos](../designers/math-nodes.md)|Describe los nodos que se pueden usar para realizar operaciones algebraicas, lógicas, trigonométricas y otras operaciones matemáticas que se asignan directamente a las instrucciones de HLSL.|  
|[Nodos de utilidad](../designers/utility-nodes.md)|Describe los nodos que se pueden usar para realizar operaciones de iluminación y otras operaciones comunes que no se asignan directamente a las instrucciones de HLSL.|  
|[Nodos de filtro](../designers/filter-nodes.md)|Describe los nodos que se pueden usar para realizar el filtrado de textura y de color.|



