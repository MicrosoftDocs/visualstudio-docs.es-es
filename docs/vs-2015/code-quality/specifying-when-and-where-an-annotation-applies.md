---
title: Especificar cuándo y dónde se aplica una anotación | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ca11e9339534c1053a62442f4eb2e4a65ca2a62
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581258"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Especificar cuándo y dónde se aplica una anotación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [especificar cuando y donde una anotación se aplica](https://docs.microsoft.com/visualstudio/code-quality/specifying-when-and-where-an-annotation-applies).  
  
Cuando una anotación es condicional, puede requerir otras anotaciones para especificar que para el analizador.  Por ejemplo, si una función tiene una variable que puede ser sincrónico o asincrónico, la función se comporta como sigue: en el caso sincrónico siempre al final se realiza correctamente, pero en el caso asincrónico notifica un error si no tiene éxito inmediatamente. Cuando la función se llama sincrónicamente, comprobando el valor de resultado proporciona ningún valor para el analizador de código porque no habría devuelto.  Sin embargo, cuando la función se llama de forma asincrónica y el resultado de la función no está activado, podría producirse un error grave. En este ejemplo se demuestra una situación en que se podría utilizar el `_When_` anotación, se describe más adelante en este artículo, para habilitar la comprobación.  
  
## <a name="structural-annotations"></a>Anotaciones estructurales  
 Para controlar cuándo y dónde se aplican las anotaciones, utilice las siguientes anotaciones estructurales.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` es una expresión que da como resultado un valor l. Las anotaciones en `anno-list` se aplican al objeto que recibe el nombre de `expr`. Para cada anotación en `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en condición previa y en if condición posterior se interpreta la anotación en la condición posterior.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` es una expresión que da como resultado un valor l. Las anotaciones en `anno-list` se aplican al objeto que recibe el nombre de `expr`. Para cada anotación en `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en la condición previa y en if condición posterior se interpreta la anotación en la condición posterior.<br /><br /> `iter` es el nombre de una variable de ámbito de la anotación (incluye `anno-list`). `iter` tiene un tipo implícito `long`. Las variables con el mismo nombre en cualquier ámbito de inclusión están ocultos de la evaluación.<br /><br /> `elem-count` es una expresión que se evalúa como un entero.|  
|`_Group_(anno-list)`|Las anotaciones en `anno-list` se consideran tener ningún calificador que se aplica a la anotación de grupo que se aplica a cada comentario.|  
|`_When_(expr, anno-list)`|`expr` es una expresión que se puede convertir en `bool`. Cuando es distinto de cero (`true`), las anotaciones que se especifican en `anno-list` se consideran aplicable.<br /><br /> De forma predeterminada, para cada anotación en `anno-list`, `expr` se interpreta como con los valores de entrada si la anotación es una condición previa y, como con los valores de salida si la anotación es una condición posterior. Para invalidar el valor predeterminado, puede usar el `_Old_` intrínsecas al evaluar una condición posterior para indicar que se deben usar los valores de entrada. **Nota:** distintas anotaciones pueden habilitarse en consecuencia usando `_When_` si un valor mutable, por ejemplo, `*pLength`: es complejo porque el resultado evaluado de `expr` en condición previa puede diferir su evaluado como resultado de condición posterior.|  
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar las clases y estructuras](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)



