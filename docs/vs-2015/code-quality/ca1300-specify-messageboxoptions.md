---
title: 'CA1300: especifique MessageBoxOptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663606"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Especifique MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|Identificador de comprobación|CA1300|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método llama a una sobrecarga del método <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> que no toma un argumento <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Para mostrar un cuadro de mensaje correctamente para las referencias culturales que usan un orden de lectura de derecha a izquierda, los miembros <xref:System.Windows.Forms.MessageBoxOptions> y <xref:System.Windows.Forms.MessageBoxOptions> de la enumeración <xref:System.Windows.Forms.MessageBoxOptions> se deben pasar al método <xref:System.Windows.Forms.MessageBox.Show%2A>. Examine la propiedad <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> del control contenedor para determinar si se va a usar un orden de lectura de derecha a izquierda.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a una sobrecarga del método <xref:System.Windows.Forms.MessageBox.Show%2A> que toma un argumento <xref:System.Windows.Forms.MessageBoxOptions>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca de código no se localizará para una referencia cultural que use un orden de lectura de derecha a izquierda.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que muestra un cuadro de mensaje con opciones adecuadas para el orden de lectura de la referencia cultural. Un archivo de recursos, que no se muestra, es necesario para compilar el ejemplo. Siga los comentarios del ejemplo para crear el ejemplo sin un archivo de recursos y probar la característica de derecha a izquierda.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [de recursos en aplicaciones de escritorio](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
