---
title: "Nodos del Dise&#241;ador de sombras | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 6
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 6
---
# Nodos del Dise&#241;ador de sombras
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los casos de esta sección de la documentación contienen información sobre los distintos nodos del Diseñador de sombreadores que puede utilizar para crear varios efectos gráficos.  
  
## Nodos y tipos de nodo  
 El Diseñador de sombras representa los efectos visuales como un gráfico.  Estos gráficos se generan a partir de nodos elegidos específicamente y conectados de maneras precisas para lograr el efecto deseado.  Cada nodo representa bien un fragmento de información o una función matemática y las conexiones entre ellos representan cómo la información recorre el gráfico para generar el resultado.  El Diseñador de sombras proporciona seis tipos de nodo distintos: filtros, nodos de textura, parámetros, constantes, nodos de utilidad y nodos de matemáticas, y cada tipo contiene varios nodos individuales.  Estos nodos y tipos de nodos se describen en los otros artículos de esta sección. Vea los vínculos al final de este documento.  
  
## Estructura del nodo  
 Todos los nodos se componen de una combinación de elementos comunes.  Cada nodo tiene al menos un terminal de salida en el lado derecho \(excepto el nodo de color final, que representa la salida del sombreador\).  Los nodos que representan cálculos o los muestreadores de textura tienen terminales de entrada en sus lados izquierdos, pero los nodos que representan información no tienen ningún terminal de entrada.  Los terminales de salida están conectados a los terminales de entrada para mover información de un nodo a otro.  
  
### Promoción de entradas  
 Dado que el Diseñador de sombras debe generar en última instancia código fuente de HLSL para poder usar el efecto en un juego o una aplicación, los nodos del Diseñador de sombras están sujetos a las reglas de promoción de tipos que usa HLSL.  Dado que el hardware gráfico funciona principalmente en valores de punto flotante, la promoción de tipos entre tipos diferentes, por ejemplo, desde `int` a `float` o desde `float` a `double`, no es frecuente.  En su lugar, dado que el hardware de gráficos usa la misma operación en múltiples fragmentos de información en el acto, otro tipo de promoción puede aparecer en el que se la menor en un número de entradas se amplía para que coincida en tamaño con la entrada más larga.  La forma en que se alarga depende del tipo de entrada y también en la propia operación:  
  
-   **Si el tipo más pequeño es un valor escalar, entonces:**  
  
     El valor del escalar se replica en un vector cuyo tamaño es igual a la entrada más grande.  Por ejemplo, la entrada escalar 5.0 se convierte en el vector \(5.0, 5.0, 5.0\) cuando la entrada más grande de la operación es un vector de tres elementos, independientemente de cuál sea la operación.  
  
-   **Si el tipo más pequeño es un vector y la operación es de multiplicación \(\*, \/, %, etc.\), entonces:**  
  
     El valor del vector se copia en los elementos iniciales de un vector cuyo tamaño es igual a la entrada más grande y los elementos finales se establecen en 1,0.  Por ejemplo, la entrada del vector \(5,0, 5,0\) se convierte en el vector \(5,0, 5,0, 1,0, 1,0\) cuando se multiplica por un vector de cuatro elementos.  Esto conserva los elementos tercero y cuarto de la salida mediante la identidad multiplicativa, 1,0.  
  
-   **Si el tipo más pequeño es un vector y la operación es de adición \(\+, \-, etc.\), entonces:**  
  
     El valor del vector se copia en los elementos principales de un vector que es igual de tamaño a la entrada mayor y los elementos finales se establecen en 0,0.  Por ejemplo, la entrada del vector \(5,0, 5,0\) se convierte en el vector \(5,0, 5,0, 0,0, 0,0\) cuando se agrega a un vector de cuatro elementos.  Esto conserva los elementos tercero y cuarto de la salida mediante la identidad aditiva, 0,0.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Nodos de constante](../designers/constant-nodes.md)|Describe los nodos que puede usar para representar valores literales e información interpolada sobre el estado del vértice en cálculos del sombreador.  Dado que estado del vértice se interpola y, por tanto, es diferente para cada píxel, cada instancia de sombreador de píxeles recibe una versión diferente de la constante.|  
|[Nodos de parámetros](../designers/parameter-nodes.md)|Describe los nodos que puede usar para representar la posición de la cámara, propiedades materiales, parámetros de iluminación, tiempo y otra información sobre el estado de la aplicación en los cálculos del sombreador.|  
|[Nodos de textura](../designers/texture-nodes.md)|Describe los nodos que puede usar para muestrear diversos tipos de textura y geometrías y para generar o transformar coordenadas de textura de formas comunes.|  
|[Nodos matemáticos](../designers/math-nodes.md)|Describe los nodos que puede usar para realizar operaciones de álgebra, lógicas, trigonométricas y otras operaciones matemáticas que se asignan directamente a las instrucciones de HLSL.|  
|[Nodos de utilidad](../designers/utility-nodes.md)|Describe los nodos que puede usar para realizar los cálculos comunes de iluminación y otras operaciones comunes que no se asignan directamente a las instrucciones de HLSL.|  
|[Nodos de filtro](../designers/filter-nodes.md)|Describe los nodos que puede usar para realizar el filtrado de texturas y de colores.|