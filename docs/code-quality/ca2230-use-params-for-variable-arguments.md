---
title: 'CA2230: Usar parámetros para argumentos de variable | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b227f4eeb769f81a07a9a065df214722876a4b50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usar parámetros para argumentos de variable
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|Identificador de comprobación|CA2230|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o protegido contiene un método público o protegido que utiliza la `VarArgs` convención de llamada.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El `VarArgs` convención de llamada se utiliza con determinadas definiciones de método que toman un número variable de parámetros. Un método mediante el `VarArgs` convención de llamada no es compatible con Common Language Specification (CLS) y podría no ser accesible a través de lenguajes de programación.  
  
 En C#, la `VarArgs` convención de llamada se usa cuando la lista de parámetros del método termina con la `__arglist` palabra clave. Visual Basic no admite la `VarArgs` convención de llamada y Visual C++ permite su uso sólo en código no administrado que utiliza la elipse `...` notación.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla en C#, utilice la [params](/dotnet/csharp/language-reference/keywords/params) palabra clave en lugar de `__arglist`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra dos métodos, uno que infringe la regla y otro que cumple la regla.  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)