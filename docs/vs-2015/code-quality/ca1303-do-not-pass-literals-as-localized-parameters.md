---
title: 'CA1303: No pasar literales parámetros como localizados | Microsoft Docs'
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
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d900abe23dab4d950b5790798916fe728a44af4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886570"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: No pasar literales como parámetros localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|Identificador de comprobación|CA1303|
|Categoría|Microsoft.Globalization|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método pasa una literal de cadena como un parámetro a un constructor o método en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteca de clases y que la cadena debe ser localizable.

 Esta advertencia se produce si una cadena literal se pasa como un valor a un parámetro o propiedad y uno o varios de los casos siguientes son verdadera:

-   El <xref:System.ComponentModel.LocalizableAttribute> atributo del parámetro o la propiedad se establece en true.

-   El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".

-   El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".

## <a name="rule-description"></a>Descripción de la regla
 Literales de cadena que se incrustan en el código fuente son difíciles de localizar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el literal de cadena con una cadena que se recuperan a través de una instancia de la <xref:System.Resources.ResourceManager> clase.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si no se puede adaptar la biblioteca de código, o si la cadena no se expone al usuario final o un desarrollador que utiliza la biblioteca de código.

 Los usuarios pueden eliminar el ruido de los métodos que no se deben pasar cadenas localizadas cambiando el parámetro o una propiedad denominada o marcando estos elementos como condicionales.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que produce una excepción cuando cualquiera de sus dos argumentos están fuera del intervalo. Para el primer argumento, el constructor de la excepción se pasa una cadena literal, lo que infringe esta regla. Para el segundo argumento, se pasa al constructor correctamente una cadena que se recuperan mediante un <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Vea también
 [Recursos de aplicaciones de escritorio](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



