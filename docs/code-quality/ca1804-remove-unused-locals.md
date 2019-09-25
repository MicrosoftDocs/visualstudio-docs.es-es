---
title: 'CA1804: Quitar variables locales no utilizadas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233749"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Quitar variables locales no utilizadas

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|Identificador de comprobación|CA1804|
|Categoría|Microsoft.Performance|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un método declara una variable local, pero no utiliza la variable, excepto posiblemente como el destinatario de una instrucción de asignación. Para el análisis de esta regla, el ensamblado probado se debe compilar con información de depuración y el archivo de base de datos de programa (. pdb) asociado debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite o use la variable local.

> [!NOTE]
> El C# compilador quita las variables locales no `optimize` utilizadas cuando se habilita la opción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla si la variable se emitió en el compilador. También es seguro suprimir una advertencia de esta regla o deshabilitar la regla si el rendimiento y el mantenimiento del código no son problemas principales.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran varias variables locales no usadas.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1809: Evitar variables locales excesivas](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Evitar código privado no llamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Evitar clases internas sin instancias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Revisar los parámetros no usados](../code-quality/ca1801-review-unused-parameters.md)