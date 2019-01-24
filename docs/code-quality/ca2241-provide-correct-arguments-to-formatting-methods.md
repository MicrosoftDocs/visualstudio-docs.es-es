---
title: 'CA2241: Proporcionar argumentos correctos a los métodos de formato'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: df71a51336f559f293faad86c161b9939a3a8014
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912982"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Proporcionar argumentos correctos a los métodos de formato

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|Identificador de comprobación|CA2241|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 El `format` pasado a un método como el argumento de cadena <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, o <xref:System.String.Format%2A?displayProperty=fullName> no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.

## <a name="rule-description"></a>Descripción de la regla
 Los argumentos de métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, y <xref:System.String.Format%2A> constan de una cadena de formato, seguida por varios <xref:System.Object?displayProperty=fullName> instancias. La cadena de formato consta de texto y elementos de formato incrustados del formulario, {index [, alignment] [: formatString]}. "index" es un entero basado en cero que indica cuál de los objetos que se va a dar formato. Si un objeto no tiene un índice correspondiente en la cadena de formato, se omite el objeto. Si no existe el objeto especificado por "index", un <xref:System.FormatException?displayProperty=fullName> se produce en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proporcione un elemento de formato para cada argumento de objeto y proporcionar un argumento de objeto para cada elemento de formato.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos infracciones de la regla.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]