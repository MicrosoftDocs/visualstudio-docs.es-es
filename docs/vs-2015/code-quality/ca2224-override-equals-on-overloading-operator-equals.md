---
title: 'CA2224: Invalidar equals al sobrecargar operadores de igualdad | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4c16ed5858f18456af59c4cc26f2e0d56e6006a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987988"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Invalidar Equals al sobrecargar operadores de igualdad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|Identificador de comprobación|CA2224|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo público implementa el operador de igualdad, pero no invalida <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 El operador de igualdad está pensado para ser una manera cómoda sintácticamente para tener acceso a la funcionalidad de la <xref:System.Object.Equals%2A> método. Si implementa el operador de igualdad, su lógica debe ser idéntica de <xref:System.Object.Equals%2A>.

 El compilador de C# emite una advertencia si el código infringe esta regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, debe quitar la implementación del operador de igualdad, o invalidar <xref:System.Object.Equals%2A> y dispone de los dos métodos que devuelven los mismos valores. Si el operador de igualdad no presenta un comportamiento incoherente, puede corregir la infracción proporcionando una implementación de <xref:System.Object.Equals%2A> que llama el <xref:System.Object.Equals%2A> método en la clase base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el operador de igualdad devuelve el mismo valor que la implementación heredada de <xref:System.Object.Equals%2A>. La sección de ejemplo incluye un tipo que se puede suprimir una advertencia de esta regla de forma segura.

## <a name="examples-of-inconsistent-equality-definitions"></a>Ejemplos de definiciones de igualdad incoherentes

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra un tipo con definiciones incoherentes de igualdad. `BadPoint` Cambie el significado de igualdad proporcionando una implementación personalizada del operador de igualdad, pero no invalida <xref:System.Object.Equals%2A> para que se comporte de forma idéntica.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Ejemplo
 El código siguiente comprueba el comportamiento de `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **¿a = a (1,1 [0]) y b = (2,2 [1]) son iguales? No**
**a == b ? ¿No**
**a1 y a son iguales? ¿Sí**
**a1 == una? ¿Sí**
**b y bcopy son iguales? ¿No**
**b == bcopy? Sí**
## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que técnicamente infringe esta regla, pero no se comporta de forma incoherente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Ejemplo
 El código siguiente comprueba el comportamiento de `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **¿a = a (1,1) y b = (2,2) son iguales? No**
**a == b ? ¿No**
**a1 y a son iguales? ¿Sí**
**a1 == una? ¿Sí**
**b y bcopy son iguales? ¿Sí**
**b == bcopy? Sí**
## <a name="class-example"></a>Ejemplo de clase

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra una clase (tipo de referencia) que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción invalidando <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Ejemplo de estructura

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra una estructura (tipo de valor) que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción invalidando <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Invalidar el método GetHashCode al invalidar Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
