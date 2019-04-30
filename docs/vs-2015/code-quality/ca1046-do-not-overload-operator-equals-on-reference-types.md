---
title: 'CA1046: No sobrecargar el operador de igualdad en los tipos de referencia | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b5543b2d968e96cbd5bf8c9f6dd015b2acf31b4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536118"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: No sobrecargar el operador de igualdad en los tipos de referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|Identificador de comprobación|CA1046|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia público o público anidado sobrecarga el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite la implementación del operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando el tipo de referencia se comporta como un tipo de valor integrado. Si tiene sentido realizar la suma o resta en instancias del tipo, es probablemente sean correcto implementar el operador de igualdad y suprimir la infracción.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra el comportamiento predeterminado al comparar dos referencias.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente compara algunas referencias.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **¿un = nuevo (2,2) y b = nuevo (2,2) son iguales? ¿No**
**c y a son igual? ¿Sí**
**b y a son ==? ¿No**
**c y a son ==? Sí**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1013: Operador de sobrecarga es igual al sobrecargar la suma y resta](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Vea también
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Operadores de igualdad](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
