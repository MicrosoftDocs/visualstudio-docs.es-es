---
title: 'CA1303: no pasar literales como parámetros localizados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539118"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: No pasar literales como parámetros localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|Identificador de comprobación|CA1303|
|Categoría|Microsoft. Globalization|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un método pasa un literal de cadena como un parámetro a un constructor o método en la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteca de clases y esa cadena debe ser localizable.

 Esta advertencia se genera cuando se pasa una cadena literal como un valor a un parámetro o propiedad y se cumple uno o varios de los siguientes casos:

- El <xref:System.ComponentModel.LocalizableAttribute> atributo del parámetro o propiedad está establecido en true.

- El nombre de la propiedad o el parámetro contiene "Text", "message" o "Caption".

- El nombre del parámetro de cadena que se pasa a un método Console. Write o Console. WriteLine es "Value" o "format".

## <a name="rule-description"></a>Descripción de la regla
 Los literales de cadena que están incrustados en el código fuente son difíciles de localizar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el literal de cadena por una cadena recuperada a través de una instancia de la <xref:System.Resources.ResourceManager> clase.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la biblioteca de código no se va a localizar, o si la cadena no se expone al usuario final o a un desarrollador que usa la biblioteca de código.

 Los usuarios pueden eliminar el ruido de los métodos que no deben pasar cadenas localizadas cambiando el nombre del parámetro o la propiedad denominada o marcando estos elementos como condicionales.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que produce una excepción cuando uno de sus dos argumentos está fuera del intervalo. En el primer argumento, se pasa al constructor de la excepción una cadena literal, que infringe esta regla. En el segundo argumento, al constructor se le pasa correctamente una cadena recuperada a través de <xref:System.Resources.ResourceManager> .

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Consulte también
 [Recursos de aplicaciones de escritorio](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
