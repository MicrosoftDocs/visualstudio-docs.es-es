---
title: 'CA1802: Usar literales cuando resulte apropiado'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 13cfc8b090d289173975b0ef2ee55562955de0c8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548756"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Usar literales cuando resulte apropiado

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|Identificador de comprobación|CA1802|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Se declara un campo `static` y `readonly` (`Shared` y `ReadOnly` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) y se inicializa con un valor que se puede calcular en tiempo de compilación.

## <a name="rule-description"></a>Descripción de la regla
 El valor de un `static``readonly` campo se calcula en tiempo de ejecución cuando se llama al constructor estático para el tipo declarativo. Si el `static``readonly` campo se inicializa cuando se declara y un constructor estático no se ha declarado explícitamente, el compilador emite un constructor estático para inicializar el campo.

 El valor de un `const` campo se calcula en tiempo de compilación y se almacena en los metadatos, lo que aumenta el rendimiento en tiempo de ejecución cuando se compara con un `static``readonly` campo.

 Dado que el valor asignado al campo de destino se calcula en tiempo de compilación, cambie la declaración a un `const` campo para que el valor se calcula en tiempo de compilación en lugar de en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el `static` y `readonly` modificadores con el `const` modificador.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla, o deshabilitar la regla de rendimiento no es importante.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `UseReadOnly`, que infringe la regla y un tipo, `UseConstant`, que cumple la regla.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]