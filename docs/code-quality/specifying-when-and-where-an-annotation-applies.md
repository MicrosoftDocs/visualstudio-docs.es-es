---
title: Especificar cuándo y dónde se aplica una anotación
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 37bee4665040b8792cdc0fa521fc75cbfe9ae1de
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018360"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Especificar cuándo y dónde se aplica una anotación
Cuando una anotación es condicional, puede requerir que otras anotaciones lo especifiquen en el analizador.  Por ejemplo, si una función tiene una variable que puede ser sincrónica o asincrónica, la función se comporta de la siguiente manera: En el caso sincrónico, siempre se realiza correctamente, pero en el caso asincrónico informa de un error si no puede realizarse inmediatamente. Cuando se llama a la función de forma sincrónica, la comprobación del valor del resultado no proporciona ningún valor al analizador de código porque no habría devuelto.  Sin embargo, cuando se llama a la función de forma asincrónica y no se comprueba el resultado de la función, podría producirse un error grave. En este ejemplo se muestra una situación en la que puede usar la anotación `_When_`, que se describe más adelante en este artículo, para habilitar la comprobación.

## <a name="structural-annotations"></a>Anotaciones estructurales
Para controlar cuándo y dónde se aplican las anotaciones, utilice las siguientes anotaciones estructurales.

|Anotación|Descripción|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` es una expresión que produce un valor l. Las anotaciones de `anno-list` se aplican al objeto denominado `expr`. Para cada anotación de `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en condición previa y en condición posterior, si la anotación se interpreta en condición posterior.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` es una expresión que produce un valor l. Las anotaciones de `anno-list` se aplican al objeto denominado `expr`. Para cada anotación de `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en condición previa, y en condición posterior si la anotación se interpreta en condición posterior.<br /><br /> `iter` es el nombre de una variable cuyo ámbito es la anotación (incluido `anno-list`). `iter` tiene un tipo implícito `long`. Las variables con el mismo nombre en cualquier ámbito de inclusión se ocultan de la evaluación.<br /><br /> `elem-count` es una expresión que se evalúa como un entero.|
|`_Group_(anno-list)`|Se considera que las anotaciones de `anno-list` tienen cualquier calificador que se aplique a la anotación de grupo que se aplica a cada anotación.|
|`_When_(expr, anno-list)`|`expr` es una expresión que se puede convertir en `bool`. Cuando es distinto de cero (`true`), se consideran aplicables las anotaciones que se especifican en `anno-list`.<br /><br /> De forma predeterminada, para cada anotación de `anno-list`, `expr` se interpreta como el uso de los valores de entrada si la anotación es una condición previa y como si se usaran los valores de salida si la anotación es una condición posterior. Para reemplazar el valor predeterminado, puede usar la función intrínseca `_Old_` al evaluar una condición posterior para indicar que se deben usar los valores de entrada. **Nota:**  Es posible que se habiliten distintas anotaciones como consecuencia del uso de `_When_` si se usa un valor mutable (por ejemplo, `*pLength`) porque el resultado evaluado de `expr` en la condición previa puede diferir del resultado evaluado en la condición posterior.|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)