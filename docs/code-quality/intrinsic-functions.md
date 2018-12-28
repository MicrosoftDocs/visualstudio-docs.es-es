---
title: Funciones intrínsecas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 757db51093dcd7e300831287b5da42cd05430e28
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804505"
---
# <a name="intrinsic-functions"></a>Funciones intrínsecas
Una expresión de SAL puede ser una expresión de C o C++, siempre que sea una expresión que no tiene efectos secundarios, por ejemplo, ++,--y llamadas a función todas tienen efectos en este contexto.  Sin embargo, SAL proporciona algunos objetos de tipo función y algunos símbolos reservadas que se pueden usar en expresiones de SAL. Estos se conocen como *funciones intrínsecas*.

## <a name="general-purpose"></a>Uso general
 Las siguientes anotaciones de la función intrínsecas proporcionan una utilidad general de SAL.

|Anotación|Descripción|
|----------------|-----------------|
|`_Curr_`|Un sinónimo para el objeto que se anota actualmente.  Cuando el `_At_` anotación está en uso, `_Curr_` es el mismo que el primer parámetro `_At_`.  En caso contrario, es el parámetro o el valor completo o valor devuelto de función que está asociada léxicamente la anotación.|
|`_Inexpressible_(expr)`|Expresa una situación donde el tamaño de un búfer es demasiado complejo para representar mediante una expresión de anotación, por ejemplo, cuando se calcula mediante el examen de un conjunto de datos de entrada y, a continuación, el recuento de miembros seleccionados.|
|`_Nullterm_length_(param)`|`param` es el número de elementos en el búfer hasta, pero sin incluir un terminador nulo. Se puede aplicar a cualquier búfer de tipo que no son de agregado y distinto de void.|
|`_Old_(expr)`|Cuando se evalúa en condición previa, `_Old_` devuelve el valor de entrada `expr`.  Cuando se evalúa de condición posterior, devuelve el valor `expr` tal como se habría evaluado en condición previa.|
|`_Param_(n)`|El `n`parámetro a una función, contando desde 1 a `n`, y `n` es una literal constante integral. Si el parámetro se denomina, esta anotación es idéntica al acceder a los parámetros por nombre. **Nota:** `n` pueden hacer referencia a los parámetros posicionales se definen mediante puntos suspensivos, o se pueden usar en prototipos de función donde no se utilizan nombres.|
|`return`|Palabra clave reservada de C o C++ `return` puede utilizarse en una expresión de SAL para indicar el valor devuelto de una función.  El valor sólo está disponible en el estado de publicación. es un error de sintaxis se utiliza en el estado previo.|

## <a name="string-specific"></a>Cadena específica
 Las siguientes anotaciones de la función intrínseca permiten la manipulación de cadenas. Cuatro de estas funciones tienen el mismo propósito: para devolver el número de elementos del tipo que se encuentra antes de un terminador nulo. Las diferencias son los tipos de datos en los elementos que se hace referencia. Tenga en cuenta que si desea especificar la longitud de terminada en null de búferes que no está formado por caracteres, use el `_Nullterm_length_(param)` anotación de la sección anterior.

|Anotación|Descripción|
|----------------|-----------------|
|`_String_length_(param)`|`param` es el número de elementos de la cadena hasta pero sin incluir un terminador nulo. Esta anotación está reservada para los tipos de cadena de caracteres.|
|`strlen(param)`|`param` es el número de elementos de la cadena hasta pero sin incluir un terminador nulo. Esta anotación está reservada para uso en caracteres, matrices y es similar a la función en tiempo de ejecución de C [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` es el número de elementos de la cadena hasta (pero no incluyendo) un terminador nulo. Esta anotación está reservada para uso en caracteres anchos, matrices y es similar a la función en tiempo de ejecución de C [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)