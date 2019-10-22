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
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662825"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usar parámetros para argumentos de variable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|Identificador de comprobación|CA2230|
|Categoría|Microsoft. Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene un método público o protegido que usa la Convención de llamada `VarArgs`.

## <a name="rule-description"></a>Descripción de la regla
 La Convención de llamada `VarArgs` se usa con ciertas definiciones de método que toman un número variable de parámetros. Un método que usa la Convención de llamada `VarArgs` no es compatible Common Language Specification (CLS) y puede que no sea accesible a través de lenguajes de programación.

 En C#, se usa la Convención de llamada de `VarArgs` cuando la lista de parámetros de un método finaliza con la palabra clave `__arglist`. Visual Basic no admite la Convención de llamada `VarArgs` y visual C++ permite su uso solo en código no administrado que utiliza la notación de `...` de la elipse.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla C#en, utilice la palabra clave [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) en lugar de `__arglist`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos métodos, uno que infringe la regla y otro que cumple la regla.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Vea también
 [independencia del lenguaje <xref:System.Reflection.CallingConventions?displayProperty=fullName> y componentes independientes del lenguaje](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
