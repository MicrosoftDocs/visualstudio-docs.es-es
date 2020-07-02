---
title: 'CA2230: usar parámetros para argumentos de variable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540366"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usar parámetros en argumentos de variable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|UseParamsForVariableArguments|
|Identificador de comprobación|CA2230|
|Categoría|Microsoft. Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo público o protegido contiene un método público o protegido que usa la `VarArgs` Convención de llamada.

## <a name="rule-description"></a>Descripción de la regla
 La `VarArgs` Convención de llamada se utiliza con ciertas definiciones de método que toman un número variable de parámetros. Un método que usa la `VarArgs` Convención de llamada no es compatible Common Language Specification (CLS) y puede que no sea accesible a través de lenguajes de programación.

 En C#, la `VarArgs` Convención de llamada se usa cuando la lista de parámetros de un método finaliza con la `__arglist` palabra clave. Visual Basic no admite la `VarArgs` Convención de llamada y Visual C++ solo permite su uso en código no administrado que utiliza la notación de elipse `...` .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla en C#, use la palabra clave [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) en lugar de `__arglist` .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos métodos, uno que infringe la regla y otro que cumple la regla.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Independencia del lenguaje y componentes independientes del lenguaje](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
