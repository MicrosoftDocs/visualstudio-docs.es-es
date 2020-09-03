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
ms.openlocfilehash: af0017a7ee6918a80a93ca90c7cf3de78885d61f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539196"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Especificar MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|Identificador de comprobación|CA1300|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un método llama a una sobrecarga del <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> método que no toma un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descripción de la regla
 Para mostrar un cuadro de mensaje correctamente para las referencias culturales que usan un orden de lectura de derecha a izquierda, los <xref:System.Windows.Forms.MessageBoxOptions> <xref:System.Windows.Forms.MessageBoxOptions> miembros y de la <xref:System.Windows.Forms.MessageBoxOptions> enumeración deben pasarse al <xref:System.Windows.Forms.MessageBox.Show%2A> método. Examine la <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propiedad del control contenedor para determinar si se va a usar un orden de lectura de derecha a izquierda.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a una sobrecarga del <xref:System.Windows.Forms.MessageBox.Show%2A> método que toma un <xref:System.Windows.Forms.MessageBoxOptions> argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca de código no se localizará para una referencia cultural que use un orden de lectura de derecha a izquierda.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que muestra un cuadro de mensaje con opciones adecuadas para el orden de lectura de la referencia cultural. Un archivo de recursos, que no se muestra, es necesario para compilar el ejemplo. Siga los comentarios del ejemplo para crear el ejemplo sin un archivo de recursos y probar la característica de derecha a izquierda.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos de aplicaciones de escritorio](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
