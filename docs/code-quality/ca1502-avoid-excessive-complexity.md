---
title: 'CA1502: Evite la excesiva complejidad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfa12a2a1ade8d32c5518660c46ce79bc997d776
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819308"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Evite la excesiva complejidad

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|Identificador de comprobación|CA1502|
|Categoría|Microsoft.Maintainability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un método tiene una complejidad ciclomática excesiva.

## <a name="rule-description"></a>Descripción de la regla

*Complejidad ciclomática* mide el número de rutas de acceso independientes linealmente a través del método, que viene determinado por el número y la complejidad de las bifurcaciones condicionales. Una complejidad ciclomática baja generalmente indica un método que es fácil de entender, probar y mantener. La complejidad ciclomática se calcula a partir de un gráfico de flujo de control del método y se proporciona como sigue:

complejidad ciclomática = número de bordes - el número de nodos + 1

donde un nodo representa un punto de bifurcación lógica y un borde representa una línea entre los nodos.

La regla emite una infracción cuando la complejidad ciclomática es más de 25.

Puede aprender más acerca de las métricas de código en [medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, refactorice el método para reducir su complejidad ciclomática.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si no se puede reducir fácilmente la complejidad y el método es fácil de entender, probar y mantener. En concreto, un método que contiene una gran `switch` (`Select` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrucción es un candidato para la exclusión. El riesgo de desestabilizar el código base en tiempo de ejecución en el ciclo de desarrollo o introducir un cambio inesperado en el comportamiento de tiempo de ejecución en código previamente distribuido puede descompensar las ventajas de mantenimiento de refactorización del código.

## <a name="how-cyclomatic-complexity-is-calculated"></a>¿Cómo se calcula la complejidad ciclomática

La complejidad ciclomática se calcula sumando 1 al siguiente:

- Número de bifurcaciones (como `if`, `while`, y `do`)

- Número de `case` instrucciones en un `switch`

## <a name="example"></a>Ejemplo

Los ejemplos siguientes muestran los métodos que tienen diferentes complejidad ciclomática.

**Complejidad ciclomática de 1**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>Ejemplo

**Complejidad ciclomática de 2**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>Ejemplo

**Complejidad ciclomática de 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Ejemplo

**Complejidad ciclomática de 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1501: Evite una herencia excesiva](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Vea también

- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)