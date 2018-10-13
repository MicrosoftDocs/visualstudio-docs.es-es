---
title: 'CA1300: Especifique MessageBoxOptions | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 157cac1ddd200799b0362529c0a434086db77781
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288930"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Especifique MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca de código no se puede adaptar para una referencia cultural que se usa un orden de lectura de derecha a izquierda.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que muestra un cuadro de mensaje que tiene las opciones apropiadas para el orden de lectura de la referencia cultural. Un archivo de recursos que no se muestra, es necesario para compilar el ejemplo. Siga los comentarios en el ejemplo para generar el ejemplo sin un archivo de recursos y probar la característica de derecha a izquierda.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos en aplicaciones de escritorio](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



