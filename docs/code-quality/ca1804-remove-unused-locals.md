---
title: 'CA1804: Quitar variables locales no utilizadas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b1846c1b8d9173db6d1f4b5acd0544fd601da67a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545468"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Quitar variables locales no utilizadas

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|Identificador de comprobación|CA1804|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método declara una variable local pero no utiliza la variable excepto posiblemente como destinatario de una instrucción de asignación. Para el análisis por esta regla, el ensamblado probado debe compilarse con información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
 Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o use la variable local. Tenga en cuenta que el compilador de C# que se incluye con [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] quita sin usar las variables locales cuando el `optimize` está habilitada.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Suprima una advertencia de esta regla si la variable generó el compilador. También es seguro suprimir una advertencia de esta regla, o para deshabilitar la regla, si el rendimiento y mantenimiento del código no son principales preocupaciones.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra varias variables locales no usadas.

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1809: Evitar variables locales excesivas](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)