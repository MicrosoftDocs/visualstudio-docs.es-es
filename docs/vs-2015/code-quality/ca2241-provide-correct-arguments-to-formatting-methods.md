---
title: 'CA2241: Proporcionar argumentos correctos a los métodos de formato | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a139db3fb1ece41c1d3f18471a286c72a7a576c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201510"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Proporcionar argumentos correctos a los métodos de formato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|Identificador de comprobación|CA2241|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 El `format` pasado a un método como el argumento de cadena <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, o <xref:System.String.Format%2A?displayProperty=fullName> no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.

## <a name="rule-description"></a>Descripción de la regla
 Los argumentos de métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, y <xref:System.String.Format%2A> constan de una cadena de formato, seguida por varios <xref:System.Object?displayProperty=fullName> instancias. La cadena de formato consta de texto y elementos de formato incrustados del formulario, {index [, alignment] [: formatString]}. "index" es un entero basado en cero que indica cuál de los objetos que se va a dar formato. Si un objeto no tiene un índice correspondiente en la cadena de formato, se omite el objeto. Si no existe el objeto especificado por "index", un <xref:System.FormatException?displayProperty=fullName> se produce en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proporcione un elemento de formato para cada argumento de objeto y proporcionar un argumento de objeto para cada elemento de formato.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos infracciones de la regla.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
