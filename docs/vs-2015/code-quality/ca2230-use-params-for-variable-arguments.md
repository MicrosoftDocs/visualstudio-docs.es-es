---
title: 'CA2230: Usar parámetros para argumentos de variable | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ad0f43ac18c39d1dfdf6464e5cd260b669e1a0da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892736"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usar parámetros para argumentos de variable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|Identificador de comprobación|CA2230|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene un método público o protegido que utiliza el `VarArgs` convención de llamada.

## <a name="rule-description"></a>Descripción de la regla
 El `VarArgs` convención de llamada se usa con determinadas definiciones de método que toman un número variable de parámetros. Un método mediante el `VarArgs` convención de llamada no es compatible con Common Language Specification (CLS) y podría no ser accesible a través de lenguajes de programación.

 En C#, la `VarArgs` convención de llamada se usa cuando la lista de parámetros de un método termina con la `__arglist` palabra clave. Visual Basic no admite la `VarArgs` convención de llamada y Visual C++ permite su uso solo en código no administrado que utiliza la elipse `...` notación.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla en C#, use el [params](http://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) palabra clave en lugar de `__arglist`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos métodos, uno que infringe la regla y otro que cumple la regla.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Independencia del lenguaje y componentes independientes del lenguaje](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



