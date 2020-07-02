---
title: 'CA1502: Evite una complejidad excesiva | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547841"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Evitar una complejidad excesiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|Identificador de comprobación|CA1502|
|Categoría|Microsoft. mantenibilidad|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un método tiene una complejidad de ciclomática excesiva.

## <a name="rule-description"></a>Descripción de la regla
 La *complejidad ciclomática* mide el número de rutas de acceso independientes de forma lineal a través del método, que viene determinado por el número y la complejidad de las bifurcaciones condicionales. Generalmente, una complejidad de ciclomática baja indica un método que es fácil de entender, probar y mantener. La complejidad ciclomática se calcula a partir de un gráfico de flujo de control del método y se proporciona de la siguiente manera:

 complejidad ciclomática = el número de límites (el número de nodos + 1)

 donde un nodo representa un punto de bifurcación lógico y un borde representa una línea entre los nodos.

 La regla notifica una infracción cuando la complejidad ciclomática es superior a 25.

 Puede obtener más información sobre las métricas de código a [la medida de la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, refactorice el método para reducir su complejidad ciclomática.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la complejidad no se puede reducir fácilmente y el método es fácil de entender, probar y mantener. En concreto, un método que contiene una `switch` instrucción grande ( `Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) es un candidato para la exclusión. El riesgo de desestabilizadoresr la base de código tardíamente en el ciclo de desarrollo o introducir un cambio inesperado en el comportamiento en tiempo de ejecución en el código enviado anteriormente podría superar las ventajas de mantenimiento de la refactorización del código.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Cómo se calcula la complejidad de ciclomática
 La complejidad ciclomática se calcula agregando 1 a lo siguiente:

- Número de bifurcaciones (como `if` , `while` y `do` )

- Número de `case` instrucciones en un`switch`

  En los ejemplos siguientes se muestran métodos que tienen diferentes complejidades de ciclomática.

## <a name="example"></a>Ejemplo
 **Complejidad ciclomática de 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Ejemplo
 **Complejidad ciclomática de 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Ejemplo
 **Complejidad ciclomática de 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Ejemplo
 **Complejidad ciclomática de 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1501: Evitar una herencia excesiva](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Consulte también
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
