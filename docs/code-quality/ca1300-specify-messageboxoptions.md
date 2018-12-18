---
title: 'CA1300: Especifique MessageBoxOptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 815fe7b7f839adeb3204e33bb532b70909d92b53
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056392"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Especifique MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|Identificador de comprobación|CA1300|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un método llama a una sobrecarga de la <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> método que no tome un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descripción de la regla

Para mostrar un cuadro de mensaje correctamente para las referencias culturales que usan un orden de lectura de derecha a izquierda, pase el [MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) y [MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) campos a la <xref:System.Windows.Forms.MessageBox.Show%2A> método. Examine el <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propiedad del control que contiene para determinar si se usa un orden de lectura de derecha a izquierda.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a una sobrecarga de la <xref:System.Windows.Forms.MessageBox.Show%2A> método que toma un <xref:System.Windows.Forms.MessageBoxOptions> argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando la biblioteca de código no se puede adaptar para una referencia cultural que se usa un orden de lectura de derecha a izquierda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un método que muestra un cuadro de mensaje que tiene las opciones apropiadas para el orden de lectura de la referencia cultural. Un archivo de recursos que no se muestra, es necesario para compilar el ejemplo. Siga los comentarios en el ejemplo para generar el ejemplo sin un archivo de recursos y probar la característica de derecha a izquierda.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index)