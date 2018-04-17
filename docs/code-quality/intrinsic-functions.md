---
title: Funciones intrínsecas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 932d034fb1510a1e73d439d62ad3129c78841bed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="intrinsic-functions"></a>Funciones intrínsecas
Una expresión de SAL puede ser una expresión de C o C++, siempre que sea una expresión que no tiene efectos secundarios, por ejemplo, ++,--y llamadas a función todas tienen efectos secundarios en este contexto.  Sin embargo, SAL proporcionar algunos objetos de tipo de función y algunos símbolos reservados que se pueden usar en expresiones de SAL. Estos se conocen como *funciones intrínsecas*.  
  
## <a name="general-purpose"></a>Uso general  
 Las anotaciones de función intrínsecas siguientes proporcionan utilidad generales para SAL.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Curr_`|Un sinónimo para el objeto que está actualmente que se va a anotar.  Cuando el `_At_` anotación está en uso, `_Curr_` es el mismo que el primer parámetro `_At_`.  En caso contrario, es el parámetro o el valor de todo o valor devuelto de función al que está asociada léxicamente la anotación.|  
|`_Inexpressible_(expr)`|Expresa una situación donde el tamaño de un búfer es demasiado complejo para representar mediante una expresión de anotación, por ejemplo, cuando se calcula mediante el examen de un conjunto de datos de entrada y, a continuación, contar miembros seleccionados.|  
|`_Nullterm_length_(param)`|`param` es el número de elementos en el búfer hasta, pero sin incluir un terminador nulo. Se puede aplicar a cualquier búfer de tipo no agregada y distinto de void.|  
|`_Old_(expr)`|Cuando se evalúa en condición previa, `_Old_` devuelve el valor de entrada `expr`.  Cuando se evalúa en la condición posterior, devuelve el valor `expr` tal y como se habría evaluado en condición previa.|  
|`_Param_(n)`|El `n`parámetro a una función, contando desde 1 a `n`, y `n` es una literal constante integral. Si el parámetro se denomina, esta anotación es idéntica al tener acceso a los parámetros por nombre. **Nota:** `n` pueden hacer referencia a los parámetros posicionales se definen por puntos suspensivos, o pueden utilizarse en prototipos de función donde no se utilizan nombres.  |  
|`return`|Palabra clave reservada de C o C++ `return` puede utilizarse en una expresión de SAL para indicar el valor devuelto de una función.  El valor sólo está disponible en el estado de publicación; es un error de sintaxis se utiliza en el estado anterior.|  
  
## <a name="string-specific"></a>Cadena específica  
 Las siguientes anotaciones de función intrínseca habilitar la manipulación de cadenas. Los cuatro de estas funciones tienen la misma finalidad: para devolver el número de elementos del tipo que se encuentra antes de un terminador nulo. Las diferencias son los tipos de datos en los elementos que se hace referencia. Tenga en cuenta que si desea especificar la longitud de un terminada en null de búferes que no se compone de caracteres, utilice el `_Nullterm_length_(param)` anotación de la sección anterior.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación está reservada para los tipos de cadena de caracteres.|  
|`strlen(param)`|`param` es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación está reservada para uso en carácter de las matrices y es similar a la función en tiempo de ejecución de C [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
|`wcslen(param)`|`param` es el número de elementos de la cadena hasta (sin incluirlo) un terminador nulo. Esta anotación está reservada para uso en caracteres anchos las matrices y se asemeja a la función en tiempo de ejecución de C [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)