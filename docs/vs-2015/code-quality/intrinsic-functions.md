---
title: Funciones intrínsecas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277962"
---
# <a name="intrinsic-functions"></a>Funciones intrínsecas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una expresión en SAL puede ser una expresión de C/C++ siempre que se trata de una expresión que no tiene efectos secundarios; por ejemplo, + +,--, y las llamadas de función tienen efectos secundarios en este contexto.  Sin embargo, SAL proporciona algunos objetos similares a funciones y algunos símbolos reservados que se pueden usar en las expresiones SAL. Estas se conocen como *funciones intrínsecas*.  
  
## <a name="general-purpose"></a>De uso general  
 Las siguientes anotaciones de la función intrínsecas proporcionan una utilidad general para SAL.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Curr_`|Sinónimo del objeto que se está anotando actualmente.  Cuando la `_At_` anotación está en uso, `_Curr_` es igual que el primer parámetro de `_At_` .  De lo contrario, es el parámetro o el valor completo de la función o devolución con el que está asociada léxicamente la anotación.|  
|`_Inexpressible_(expr)`|Expresa una situación en la que el tamaño de un búfer es demasiado complejo para representarlo mediante una expresión de anotación; por ejemplo, cuando se calcula examinando un conjunto de datos de entrada y contando a continuación los miembros seleccionados.|  
|`_Nullterm_length_(param)`|`param` es el número de elementos del búfer hasta, pero sin incluir un terminador null. Se puede aplicar a cualquier búfer de tipo no agregado, no void.|  
|`_Old_(expr)`|Cuando se evalúa en condición previa, `_Old_` devuelve el valor de entrada `expr` .  Cuando se evalúa en una condición posterior, devuelve el valor `expr` tal como se hubiera evaluado en condición previa.|  
|`_Param_(n)`|El `n` parámetro TH para una función, contando entre 1 `n` y, y `n` es una constante entera literal. Si el parámetro se denomina, esta anotación es idéntica a tener acceso al parámetro por su nombre. **Nota:** `n` puede hacer referencia a los parámetros posicionales definidos por puntos suspensivos o que se pueden usar en prototipos de función en los que no se usan nombres.  |  
|`return`|La palabra clave reservada de C/C++ `return` se puede usar en una expresión sal para indicar el valor devuelto de una función.  El valor solo está disponible en post State; se trata de un error de sintaxis para usarlo en el estado anterior.|  
  
## <a name="string-specific"></a>Específico de cadena  
 Las siguientes anotaciones de función intrínseca permiten la manipulación de cadenas. Las cuatro funciones tienen el mismo propósito: devolver el número de elementos del tipo que se encuentra antes de un terminador nulo. Las diferencias son los tipos de datos de los elementos a los que se hace referencia. Tenga en cuenta que si desea especificar la longitud de un búfer terminado en null que no está compuesto por caracteres, use la `_Nullterm_length_(param)` anotación de la sección anterior.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación está reservada para tipos de cadena de caracteres.|  
|`strlen(param)`|`param` es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación se reserva para su uso en matrices de caracteres y se parece a la función en tiempo de ejecución de C [strlen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` es el número de elementos de la cadena hasta un terminador nulo (pero no se incluye). Esta anotación se reserva para su uso en matrices de caracteres anchos y se parece a la función de tiempo de ejecución de C [wcslen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Consulte también  
 [Usar anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Descripción de SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
