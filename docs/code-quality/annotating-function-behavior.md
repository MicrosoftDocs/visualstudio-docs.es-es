---
title: Anotar el comportamiento de funciones
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: c7ff2551f3a99bf13909f9db3b1659482246e957
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919626"
---
# <a name="annotating-function-behavior"></a>Anotar el comportamiento de funciones
Además de anotar [parámetros de función y valores](../code-quality/annotating-function-parameters-and-return-values.md)devueltos, puede anotar las propiedades de toda la función.

## <a name="function-annotations"></a>Anotaciones de función
Las anotaciones siguientes se aplican a la función en su totalidad y describen cómo se comporta o lo que espera que sea true.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|No está diseñado para ser independiente; en su lugar, es un predicado que se va a `_When_` usar con la anotación. Para obtener más información, vea [especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> El `name` parámetro es una cadena arbitraria que también aparece en una `_Function_class_` anotación en la declaración de algunas funciones.  `_Called_from_function_class_`Devuelve un valor distinto de cero si la función que se está analizando actualmente se `_Function_class_` anota con que tiene el mismo `name`valor de; de lo contrario, devuelve cero.|
|`_Check_return_`|Anota un valor devuelto y indica que el autor de la llamada debería inspeccionarlo. El comprobador informa de un error si se llama a la función en un contexto void.|
|`_Function_class_(name)`|El `name` parámetro es una cadena arbitraria designada por el usuario.  Existe en un espacio de nombres que es distinto de otros espacios de nombres. Una función, un puntero A función o, lo que es más útil, un tipo de puntero de función se puede designar como perteneciente a una o varias clases de función.|
|`_Raises_SEH_exception_`|Anota una función que siempre genera una excepción de controlador de excepciones estructurado (SEH), sujeto `_When_` a `_On_failure_` las condiciones y. Para obtener más información, vea [especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Anota una función que puede generar opcionalmente una excepción SEH, sujeta a `_When_` las condiciones y. `_On_failure_`|
|`_Must_inspect_result_`|Anota cualquier valor de salida, incluidos el valor devuelto, los parámetros y las variables globales.  El analizador informa de un error si el valor del objeto anotado no se inspecciona posteriormente. "Inspección" incluye si se usa en una expresión condicional, se asigna a un parámetro de salida o global, o se pasa como un parámetro.  Para los valores devueltos, `_Must_inspect_result_` implica. `_Check_return_`|
|`_Use_decl_annotations_`|Se puede utilizar en una definición de función (también conocida como cuerpo de la función) en lugar de la lista de anotaciones en el encabezado.  Cuando `_Use_decl_annotations_` se utiliza, las anotaciones que aparecen en un encabezado en el ámbito de la misma función se usan como si también estuvieran presentes en la definición que tiene la `_Use_decl_annotations_` anotación.|

## <a name="successfailure-annotations"></a>Anotaciones de éxito o error
Una función puede producir un error y, cuando lo hace, sus resultados pueden estar incompletos o ser diferentes de los resultados cuando la función se ejecuta correctamente.  Las anotaciones de la siguiente lista proporcionan formas de expresar el comportamiento del error.  Para usar estas anotaciones, debe habilitarlas para determinar si se han realizado correctamente. por lo tanto `_Success_` , se requiere una anotación.  Tenga en `NTSTATUS` cuenta `HRESULT` que y ya `_Success_` tienen una anotación incorporada; sin embargo, si especifica su propia `_Success_` anotación en `NTSTATUS` o `HRESULT`, reemplazará a la anotación integrada.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Always_(anno_list)`|Equivalente a `anno_list _On_failure_(anno_list)`; es decir, las anotaciones de `anno_list` se aplican tanto si la función se ejecuta correctamente como si no.|
|`_On_failure_(anno_list)`|Para usarse solo cuando `_Success_` se usa también para anotar la función, ya sea explícitamente o implícitamente `_Return_type_success_` a través de una definición de tipo. Cuando la `_On_failure_` anotación está presente en un parámetro de función o en un valor devuelto, cada `anno_list` anotación de (anno) se comporta como si estuviera codificada como `_When_(!expr, anno)`, donde `expr` es el parámetro de la anotación `_Success_` requerida. Esto significa que la aplicación implícita de `_Success_` a todas las condiciones posteriores no se `_On_failure_`aplica a.|
|`_Return_type_success_(expr)`|Se puede aplicar a una definición de tipo. Indica que todas las funciones que devuelven ese tipo y no `_Success_` tienen explícitamente se anotan como `_Success_(expr)`si tuvieran. `_Return_type_success_`no se puede usar en una función o en una definición de tipo de puntero de función.|
|`_Success_(expr)`|`expr`es una expresión que produce un valor r. Cuando la `_Success_` anotación está presente en una declaración o definición de función, cada anotación (`anno`) de la función y de la condición posterior se comporta como si estuviera codificada como `_When_(expr, anno)`. La `_Success_` anotación solo se puede usar en una función, no en sus parámetros o tipo de valor devuelto. Puede haber como máximo `_Success_` una anotación en una función y no puede estar en ningún `_When_`, `_At_`o `_Group_`. Para obtener más información, vea [especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)