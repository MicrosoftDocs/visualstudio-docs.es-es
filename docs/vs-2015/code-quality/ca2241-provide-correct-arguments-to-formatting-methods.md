---
title: 'CA2241: proporcione los argumentos correctos para aplicar formato a los métodos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672030"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Proporcionar argumentos correctos para los métodos de formato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|Identificador de comprobación|CA2241|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 El `format` argumento de cadena que se pasa a un método como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> o <xref:System.String.Format%2A?displayProperty=fullName> no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.

## <a name="rule-description"></a>Descripción de la regla
 Los argumentos para métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> y <xref:System.String.Format%2A> constan de una cadena de formato seguida de varias instancias de <xref:System.Object?displayProperty=fullName>. La cadena de formato consta de texto y elementos de formato incrustados con el formato, {index [, alignment] [: formatString]}. ' index ' es un entero basado en cero que indica a qué objetos se va a dar formato. Si un objeto no tiene un índice correspondiente en la cadena de formato, se omite el objeto. Si el objeto especificado por ' index ' no existe, se produce una <xref:System.FormatException?displayProperty=fullName> en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proporcione un elemento de formato para cada argumento de objeto y proporcione un argumento de objeto para cada elemento de formato.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos infracciones de la regla.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
