---
title: "CA2230: Usar parámetros para argumentos de variable | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3bd98c7dd1874617a8f6d6937c56c742a511f0de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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