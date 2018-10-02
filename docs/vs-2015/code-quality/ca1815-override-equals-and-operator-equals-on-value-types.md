---
title: 'CA1815: Reemplazar equals y el operador equals en los tipos de valor | Microsoft Docs'
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
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09f9ef7ecb9dce361c2a060501e18fc4b36dd18a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592309"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Reemplazar Equals y el operador Equals en los tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1815: reemplazar equals y el operador equals en los tipos de valor](https://docs.microsoft.com/visualstudio/code-quality/ca1815-override-equals-and-operator-equals-on-value-types).

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|Identificador de comprobación|CA1815|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de valor público no invalida <xref:System.Object.Equals%2A?displayProperty=fullName>, o no implementa el operador de igualdad (==). Esta regla no comprueba las enumeraciones.

## <a name="rule-description"></a>Descripción de la regla
 Para los tipos de valor, la implementación heredada de <xref:System.Object.Equals%2A> usa la biblioteca de reflexión y compara el contenido de todos los campos. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si se espera que los usuarios comparar u ordenar las instancias o usarlas como claves de tabla hash, el tipo de valor debe implementar <xref:System.Object.Equals%2A>. Si el lenguaje de programación admite la sobrecarga de operadores, también debe proporcionar una implementación de los operadores de igualdad y desigualdad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proporcione una implementación de <xref:System.Object.Equals%2A>. Si es posible, implemente el operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si no se compararán las instancias del tipo de valor entre sí.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra una estructura (tipo de valor) que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Ejemplo de cómo corregir

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior invalidando <xref:System.ValueType.Equals%2A?displayProperty=fullName> e implementar los operadores de igualdad (==,! =).

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Vea también
 <xref:System.Object.Equals%2A?displayProperty=fullName>



