---
title: 'CA1300: Especifique MessageBoxOptions'
ms.date: 11/04/2016
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
ms.workload:
- multiple
ms.openlocfilehash: d2d0b28d804dc6932e66de9dcd758fd05fc888f7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
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
 Para mostrar un cuadro de mensaje correctamente para las referencias culturales que usan un orden de lectura de derecha a izquierda, el <xref:System.Windows.Forms.MessageBoxOptions> y <xref:System.Windows.Forms.MessageBoxOptions> los miembros de la <xref:System.Windows.Forms.MessageBoxOptions> enumeración debe pasarse a la <xref:System.Windows.Forms.MessageBox.Show%2A> método. Examine el <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propiedad del control que contiene para determinar si se usa un orden de lectura de derecha a izquierda.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a una sobrecarga de la <xref:System.Windows.Forms.MessageBox.Show%2A> método que toma un <xref:System.Windows.Forms.MessageBoxOptions> argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca de código no se puede adaptar para una referencia cultural que utiliza un orden de lectura de derecha a izquierda.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que muestra un cuadro de mensaje que tiene opciones que son adecuadas para el orden de lectura de la referencia cultural. Se requiere un archivo de recursos, que no se muestra, para generar el ejemplo. Siga los comentarios en el ejemplo para compilar el ejemplo sin un archivo de recursos y probar la característica de escritura de derecha a izquierda.

 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Vea también
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos en aplicaciones de escritorio](/dotnet/framework/resources/index)