---
title: 'CA1300: Especificar MessageBoxOptions'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 746475e60bbe72c4ebfc51f13d0b2d4d0552ff62
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235188"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Especificar MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|Identificador de comprobación|CA1300|
|Categoría|Microsoft. Globalization|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método llama a una sobrecarga del <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> método que no toma un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descripción de la regla

Para mostrar un cuadro de mensaje correctamente para las <xref:System.Windows.Forms.MessageBox.Show%2A> referencias culturales que usan un orden de lectura de derecha a izquierda, pase los campos [messageboxoptions. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) y [messageboxoptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) al método. Examine la <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propiedad del control contenedor para determinar si se va a usar un orden de lectura de derecha a izquierda.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a una sobrecarga <xref:System.Windows.Forms.MessageBox.Show%2A> del método que toma <xref:System.Windows.Forms.MessageBoxOptions> un argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando la biblioteca de código no se localizará para una referencia cultural que use un orden de lectura de derecha a izquierda.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un método que muestra un cuadro de mensaje con opciones adecuadas para el orden de lectura de la referencia cultural. Un archivo de recursos, que no se muestra, es necesario para compilar el ejemplo. Siga los comentarios del ejemplo para crear el ejemplo sin un archivo de recursos y probar la característica de derecha a izquierda.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index)