---
title: 'CA1802: Utilizar cuando sea necesario | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: f3bef3fe8627f93b2d4fe7f3ec46f4834be5c01b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591217"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Usar literales cuando resulte apropiado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1802: usar literales donde corresponda](https://docs.microsoft.com/visualstudio/code-quality/ca1802-use-literals-where-appropriate).

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



