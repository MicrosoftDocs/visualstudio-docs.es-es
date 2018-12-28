---
title: Especificar cuándo y dónde se aplica una anotación
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 1bc4d00d8c6b1f6b876700066d93b552b7fe5996
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803836"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Especificar cuándo y dónde se aplica una anotación
Cuando una anotación es condicional, puede requerir otras anotaciones para especificar que para el analizador.  Por ejemplo, si una función tiene una variable que puede ser sincrónico o asincrónico, la función se comporta como sigue: En el caso sincrónico siempre al final se realiza correctamente, pero en el caso asincrónico notifica un error si no tiene éxito inmediatamente. Cuando la función se llama sincrónicamente, comprobando el valor de resultado proporciona ningún valor para el analizador de código porque no habría devuelto.  Sin embargo, cuando la función se llama de forma asincrónica y el resultado de la función no está activado, podría producirse un error grave. En este ejemplo se demuestra una situación en que se podría utilizar el `_When_` anotación, se describe más adelante en este artículo, para habilitar la comprobación.

## <a name="structural-annotations"></a>Anotaciones estructurales
 Para controlar cuándo y dónde se aplican las anotaciones, utilice las siguientes anotaciones estructurales.

|Anotación|Descripción|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` es una expresión que da como resultado un valor l. Las anotaciones en `anno-list` se aplican al objeto que recibe el nombre de `expr`. Para cada anotación en `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en condición previa y en if condición posterior se interpreta la anotación en la condición posterior.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` es una expresión que da como resultado un valor l. Las anotaciones en `anno-list` se aplican al objeto que recibe el nombre de `expr`. Para cada anotación en `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en la condición previa y en if condición posterior se interpreta la anotación en la condición posterior.<br /><br /> `iter` es el nombre de una variable de ámbito de la anotación (incluye `anno-list`). `iter` tiene un tipo implícito `long`. Las variables con el mismo nombre en cualquier ámbito de inclusión están ocultos de la evaluación.<br /><br /> `elem-count` es una expresión que se evalúa como un entero.|
|`_Group_(anno-list)`|Las anotaciones en `anno-list` se consideran tener ningún calificador que se aplica a la anotación de grupo que se aplica a cada comentario.|
|`_When_(expr, anno-list)`|`expr` es una expresión que se puede convertir en `bool`. Cuando es distinto de cero (`true`), las anotaciones que se especifican en `anno-list` se consideran aplicable.<br /><br /> De forma predeterminada, para cada anotación en `anno-list`, `expr` se interpreta como con los valores de entrada si la anotación es una condición previa y, como con los valores de salida si la anotación es una condición posterior. Para invalidar el valor predeterminado, puede usar el `_Old_` intrínsecas al evaluar una condición posterior para indicar que se deben usar los valores de entrada. **Nota:**  Distintas anotaciones pueden habilitarse como consecuencia de usar `_When_` si un valor mutable, por ejemplo, `*pLength`: es complejo porque el resultado evaluado de `expr` en condición previa puede diferir de su resultado evaluado de la condición posterior.|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)