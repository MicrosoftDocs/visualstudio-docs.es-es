---
title: 'CA1802: Usar literales | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987260"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Utilizar literales cuando sea apropiado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|Identificador de comprobación|CA1802|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Se declara un campo `static` y `readonly` (`Shared` y `ReadOnly` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) y se inicializa con un valor que se puede calcular en tiempo de compilación.

## <a name="rule-description"></a>Descripción de la regla
 El valor de un `static``readonly` campo se calcula en tiempo de ejecución cuando se llama al constructor estático para el tipo declarativo. Si el `static``readonly` campo se inicializa cuando se declara y un constructor estático no se ha declarado explícitamente, el compilador emite un constructor estático para inicializar el campo.

 El valor de un `const` campo se calcula en tiempo de compilación y se almacena en los metadatos, lo que aumenta el rendimiento en tiempo de ejecución cuando se compara con un `static``readonly` campo.

 Dado que el valor asignado al campo de destino se calcula en tiempo de compilación, cambie la declaración a un `const` campo para que el valor se calcula en tiempo de compilación en lugar de en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el `static` y `readonly` modificadores con el `const` modificador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla, o deshabilitar la regla de rendimiento no es importante.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `UseReadOnly`, que infringe la regla y un tipo, `UseConstant`, que cumple la regla.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
