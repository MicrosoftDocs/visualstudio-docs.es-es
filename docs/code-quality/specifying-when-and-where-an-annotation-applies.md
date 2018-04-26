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
ms.openlocfilehash: 9d99ebce3adc27039763e11ed4882a20199e8469
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Especificar cuándo y dónde se aplica una anotación
Cuando una anotación es condicional, puede requerir otras anotaciones para especificar el analizador.  Por ejemplo, si una función tiene una variable que puede ser sincrónico o asincrónico, la función se comporta como sigue: en el caso sincrónico siempre al final se realiza correctamente, pero en el caso asincrónico notifica un error si no se logra inmediatamente. Cuando se llama a la función de forma sincrónica, comprobando el valor de resultado proporciona ningún valor para el analizador de código porque no habría devuelto.  Sin embargo, cuando la función se llama de forma asincrónica y el resultado de la función no está activado, puede producirse un error grave. Este ejemplo muestra una situación en que se puede utilizar el `_When_` anotación: se describe más adelante en este artículo: para habilitar la comprobación.

## <a name="structural-annotations"></a>Anotaciones estructurales
 Para controlar cuándo y dónde se aplican las anotaciones, utilice las siguientes anotaciones estructurales.

|Anotación|Descripción|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` es una expresión que da como resultado un valor l. Las anotaciones en `anno-list` se aplican al objeto al que se denomina por `expr`. Para cada anotación en `anno-list`, `expr` se interpreta en la condición previa si la anotación se interpreta en la condición previa y posterior a la condición if se interpreta la anotación en la condición posterior.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` es una expresión que da como resultado un valor l. Las anotaciones en `anno-list` se aplican al objeto al que se denomina por `expr`. Para cada anotación en `anno-list`, `expr` se interpreta en la condición previa si la anotación se interpreta en la condición previa y posterior a la condición if se interpreta la anotación en la condición posterior.<br /><br /> `iter` es el nombre de una variable que tiene un ámbito para la anotación (incluye `anno-list`). `iter` tiene un tipo implícito `long`. Las variables con el mismo nombre en cualquier ámbito de inclusión se ocultan en la evaluación.<br /><br /> `elem-count` es una expresión que se evalúa como un número entero.|
|`_Group_(anno-list)`|Las anotaciones en `anno-list` se consideran que cualquier calificador que se aplica a la anotación del grupo que se aplica a cada anotación.|
|`_When_(expr, anno-list)`|`expr` es una expresión que se puede convertir en `bool`. Si es distinto de cero (`true`), las anotaciones que se especifican en `anno-list` se consideran aplicable.<br /><br /> De forma predeterminada, para cada anotación en `anno-list`, `expr` se interpreta como con los valores de entrada si la anotación es una condición previa, y como con los valores de salida si la anotación es una condición posterior. Para invalidar el valor predeterminado, puede utilizar el `_Old_` intrínseco al evaluar una condición posterior para indicar que se deben usar los valores de entrada. **Nota:** distintas anotaciones pueden habilitarse en consecuencia usando `_When_` si un valor mutable: por ejemplo, `*pLength`: es complejo porque el resultado evaluado de la `expr` en condición previa puede diferir del su evaluado como resultado de la condición posterior.|

## <a name="see-also"></a>Vea también
 [Utilizar anotaciones SAL para reducir defectos de código de C o C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [descripción SAL](../code-quality/understanding-sal.md) [anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md) [anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md) [Anotar Structs y clases](../code-quality/annotating-structs-and-classes.md) [anotar el comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md) [funciones intrínsecas](../code-quality/intrinsic-functions.md) [procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)