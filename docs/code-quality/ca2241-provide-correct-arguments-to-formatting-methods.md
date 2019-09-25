---
title: 'CA2241: Proporcionar argumentos correctos a los métodos de formato'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 10a4cdaa1e2de768cadc569424a490aa4adb7135
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253214"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Proporcionar argumentos correctos a los métodos de formato

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|Identificador de comprobación|CA2241|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
El `format` argumento de cadena que se pasa a un <xref:System.Console.WriteLine%2A>método <xref:System.Console.Write%2A>como, <xref:System.String.Format%2A?displayProperty=fullName> o no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.

## <a name="rule-description"></a>Descripción de la regla
Los argumentos para métodos <xref:System.Console.WriteLine%2A>como, <xref:System.Console.Write%2A>y <xref:System.String.Format%2A> se componen de una cadena de formato seguida <xref:System.Object?displayProperty=fullName> de varias instancias. La cadena de formato consta de texto y elementos de formato incrustados con el formato, {index [, alignment] [: formatString]}. ' index ' es un entero basado en cero que indica a qué objetos se va a dar formato. Si un objeto no tiene un índice correspondiente en la cadena de formato, se omite el objeto. Si el objeto especificado por ' index ' no existe, se produce <xref:System.FormatException?displayProperty=fullName> una excepción en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, proporcione un elemento de formato para cada argumento de objeto y proporcione un argumento de objeto para cada elemento de formato.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran dos infracciones de la regla.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]