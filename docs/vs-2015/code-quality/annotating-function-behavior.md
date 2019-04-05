---
title: Anotar comportamiento de la función | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 39edea3bfb299a49fde9cad14321caa6b4bf674a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989460"
---
# <a name="annotating-function-behavior"></a>Anotar el comportamiento de funciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Además de realizar la anotación [parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md), puede anotar las propiedades de la función completa.  
  
## <a name="function-annotations"></a>Anotaciones de función  
 Las anotaciones siguientes se aplican a la función como un todo y describen cómo se comporta o lo que espera que sea true.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|No se pretende independiente; en su lugar, es un predicado que se usará con el `_When_` anotación. Para obtener más información, consulte [especificar cuando y donde una anotación se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> El `name` parámetro es una cadena arbitraria que también aparece en un `_Function_class_` anotación en la declaración de algunas funciones.  `_Called_from_function_class_` Devuelve cero si se anota utilizando la función que actualmente se está analizando `_Function_class_` que tiene el mismo valor de `name`; de lo contrario, devuelve cero.|  
|`_Check_return_`|Estados que el llamador debe inspeccionar y anota el valor devuelto. El Comprobador de notifica un error si se llama a la función en un contexto de void.|  
|`_Function_class_(name)`|El `name` parámetro es una cadena arbitraria que se haya designado por el usuario.  Existe un espacio de nombres es distinto de otros espacios de nombres. Una función, puntero a función, o, más útiles, un tipo de puntero de función se puede designar como perteneciente a una o más clases de función.|  
|`_Raises_SEH_exception_`|Anota una función que siempre genera una excepción (SEH) del controlador de excepciones estructurado, sujeto a `_When_` y `_On_failure_` condiciones. Para obtener más información, consulte [especificar cuando y donde una anotación se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Anota una función que opcionalmente se puede producir una excepción SEH, sujeto a `_When_` y `_On_failure_` condiciones.|  
|`_Must_inspect_result_`|Anota cualquier valor de salida, como el valor devuelto, los parámetros y variables globales.  El analizador notifica un error si no se ha inspeccionado posteriormente el valor en el objeto anotado. "Inspección" incluye si se utiliza en una expresión condicional, se asigna a un parámetro de salida o global o se pasa como un parámetro.  Para los valores devueltos, `_Must_inspect_result_` implica `_Check_return_`.|  
|`_Use_decl_annotations_`|Se pueden utilizar en una definición de función (también conocido como el cuerpo de una función) en lugar de la lista de anotaciones en el encabezado.  Cuando `_Use_decl_annotations_` es utilizado, se usan las anotaciones que aparecen en un encabezado en el ámbito para la misma función como si también están presentes en la definición que tiene el `_Use_decl_annotations_` anotación.|  
  
## <a name="successfailure-annotations"></a>Anotaciones de éxito/error  
 Una función puede producir un error, y al mismo tiempo, sus resultados pueden estar incompletos o no difieren de los resultados cuando la función se realiza correctamente.  Las anotaciones en la lista siguiente proporcionan maneras de expresar el comportamiento de error.  Para usar estas anotaciones, debe habilitar determinar el éxito; por lo tanto, un `_Success_` anotación es necesaria.  Tenga en cuenta que `NTSTATUS` y `HRESULT` ya tiene un `_Success_` anotación integrada en ellas; sin embargo, si especifica su propia `_Success_` anotación en `NTSTATUS` o `HRESULT`, invalida la anotación integrada.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Equivalente a `anno_list _On_failure_(anno_list)`; es decir, las anotaciones en `anno_list` aplicar la función se realiza correctamente o no.|  
|`_On_failure_(anno_list)`|Para usarse solo cuando `_Success_` también se usa para anotar la función, ya sea explícitamente o implícitamente a través de `_Return_type_success_` en una definición de tipo. Cuando el `_On_failure_` anotación está presente en un función parámetro o valor devuelto, cada anotación en `anno_list` (anno) se comporta como si se se codifica como `_When_(!expr, anno)`, donde `expr` es el parámetro necesario `_Success_` anotación. Esto significa que la aplicación implícita de `_Success_` a todas las condiciones posteriores no se aplica a `_On_failure_`.|  
|`_Return_type_success_(expr)`|Se pueden aplicar a una definición de tipo. Indica que todas las funciones que devuelven que escribe y no tiene explícitamente `_Success_` se anotan como si tuvieran `_Success_(expr)`. `_Return_type_success_` no se puede usar en una función o una definición de tipo de puntero de función.|  
|`_Success_(expr)`|`expr` es una expresión que da como resultado un valor r. Cuando el `_Success_` anotación está presente en una declaración de función o definición, cada anotación (`anno`) en la función y en la condición posterior a la que se comporta como si se se codifica como `_When_(expr, anno)`. El `_Success_` anotación puede usarse solo en una función, no en sus parámetros o el tipo de valor devuelto. Puede haber a lo sumo un `_Success_` anotación en una función y no puede estar en cualquier `_When_`, `_At_`, o `_Group_`. Para obtener más información, consulte [especificar cuando y donde una anotación se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar las clases y estructuras](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
