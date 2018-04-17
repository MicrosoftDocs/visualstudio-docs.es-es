---
title: 'CA1815: Reemplazar equals y el operador equals en los tipos de valor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4f5667977ed25da03d5d651e28c5ae3c3f4a3e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Reemplazar Equals y el operador Equals en los tipos de valor
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|Identificador de comprobación|CA1815|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo de valor público no reemplaza <xref:System.Object.Equals%2A?displayProperty=fullName>, o no implementa el operador de igualdad (==). Esta regla no comprueba las enumeraciones.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Para los tipos de valor, la implementación heredada de <xref:System.Object.Equals%2A> usa la biblioteca de reflexión y compara el contenido de todos los campos. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si se espera que los usuarios a las instancias de comparación u ordenar o utilizarlos tal y como claves de tabla hash, el tipo de valor debe implementar <xref:System.Object.Equals%2A>. Si el lenguaje de programación admite la sobrecarga de operadores, también debe proporcionar una implementación de los operadores de igualdad y desigualdad.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proporcione una implementación de <xref:System.Object.Equals%2A>. Si es posible, implemente el operador de igualdad.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si las instancias del tipo de valor no se comparan entre sí.  
  
## <a name="example-of-a-violation"></a>Ejemplo de una infracción  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra una estructura (tipo de valor) que infringe esta regla.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Ejemplo de cómo reparar  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se corrige la infracción anterior mediante la invalidación <xref:System.ValueType.Equals%2A?displayProperty=fullName> e implementación de los operadores de igualdad (==,! =).  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>