---
title: "Especificar cu&#225;ndo y d&#243;nde se aplica una anotaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Especificar cu&#225;ndo y d&#243;nde se aplica una anotaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando una anotación es condicional, puede exigir otras anotaciones especificar que el analizador.  Por ejemplo, si una función tiene una variable que se puede sincrónica o asincrónica, la función se comporta como sigue: En el caso sincrónico correctamente siempre finalmente, pero en el caso asincrónico notifica un error si no puede tener éxito inmediatamente.  Cuando se llama a la función sincrónicamente, comprobar el valor de resultado no proporciona ningún valor al analizador de código porque no habría vuelto.  Sin embargo, cuando se llama a la función de forma asincrónica y el resultado de la función no se comprueba, un error grave podría aparecer.  Este ejemplo muestra una situación en la que puede utilizar `_When_` anotación\- descrito más adelante en este artículo\- a comprobar de permiso.  
  
## Anotaciones estructurales  
 Para controlar cuándo y donde se aplican las anotaciones, utilice las anotaciones estructurales siguientes.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` es una expresión que produce un valor l.  Las anotaciones en `anno-list` se aplican al objeto que llama `expr`.  Para cada anotaciones en `anno-list`, `expr` se interpreta en la condición previa si la anotación se interpreta en la condición previa y, en POST\- condición si la anotación se interpreta en POST\- condición.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` es una expresión que produce un valor l.  Las anotaciones en `anno-list` se aplican al objeto que llama `expr`.  Para cada anotaciones en `anno-list`, `expr` se interpreta en la condición previa si la anotación se interpreta en la condición previa y, en POST\- condición si la anotación se interpreta en POST\- condición.<br /><br /> `iter` es el nombre de una variable cuyo ámbito a la anotación \(incluidos `anno-list`\).  `iter` tiene un tipo implícito `long`.  Las variables con nombres idénticos en cualquier ámbito de inclusión están ocultas a la evaluación.<br /><br /> `elem-count` es una expresión que se evalúa como un entero.|  
|`_Group_(anno-list)`|Las anotaciones en `anno-list` todas se consideran tener cualquier calificador que se aplican a la anotación de grupo que se aplica a cada anotación.|  
|`_When_(expr, anno-list)`|`expr` es una expresión que se puede convertir en `bool`.  Cuando es distinto de cero \(`true`\), las anotaciones que se especifican en `anno-list` se consideran aplicable.<br /><br /> De forma predeterminada, para cada anotaciones en `anno-list`, `expr` se interpreta como mediante los valores de entrada si la anotación es una condición previa, como mediante los valores de salida si la anotación es una POST\- condición.  Para reemplazar el valor predeterminado, puede utilizar intrínsecos de `_Old_` cuando se evalúa una POST\- condición para indicar que los valores de entrada deben usarse. **Note:**  Varias anotaciones se pueden habilitar como resultado de utilizar `_When_` si el siguiente valor mutable para el ejemplo, `*pLength`— implicado porque el resultado evaluado de `expr` en la condición previa puede diferir del resultado evaluado en POST\- condición.|  
  
## Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)   
 [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)