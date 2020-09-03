---
title: 'CA1046: no sobrecargar el operador Equals en los tipos de referencia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 118c29473db09d5ed0a4fa447e27e593a88f98b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546762"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: No sobrecargar el operador de igualdad en los tipos de referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|Identificador de comprobación|CA1046|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo de referencia público público o anidado sobrecarga el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite la implementación del operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando el tipo de referencia se comporta como un tipo de valor integrado. Si es significativo realizar sumas o restas en las instancias del tipo, probablemente sea correcto implementar el operador de igualdad y suprimir la infracción.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el comportamiento predeterminado cuando se comparan dos referencias.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Ejemplo
 En la siguiente aplicación se comparan algunas referencias.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **r = New (2, 2) y b = New (2, 2) son iguales? ** 
 **¿No c y a son iguales? Sí** 
 **b y a son =? No** 
 **c y a son = =? Sí**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Consulte también
 <xref:System.Object.Equals%2A?displayProperty=fullName>[Operadores de igualdad](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
