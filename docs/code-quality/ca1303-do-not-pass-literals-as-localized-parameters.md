---
title: 'CA1303: No pasar literales como parámetros localizados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2700dc2ade7ba901f15f67045e3170e2bbb40ff8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235114"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: No pasar literales como parámetros localizados

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|Identificador de comprobación|CA1303|
|Categoría|Microsoft. Globalization|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método pasa un literal de cadena como un parámetro a un método o constructor .NET y esa cadena debe ser localizable.

Esta advertencia se genera cuando se pasa una cadena literal como un valor a un parámetro o propiedad y se cumple uno o varios de los siguientes casos:

- El <xref:System.ComponentModel.LocalizableAttribute> atributo del parámetro o propiedad está establecido en true.

- El nombre de la propiedad o el parámetro contiene "Text", "message" o "Caption".

- El nombre del parámetro de cadena que se pasa a un método Console. Write o Console. WriteLine es "Value" o "format".

## <a name="rule-description"></a>Descripción de la regla

Los literales de cadena que están incrustados en el código fuente son difíciles de localizar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, reemplace el literal de cadena por una cadena recuperada a través <xref:System.Resources.ResourceManager> de una instancia de la clase.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si la biblioteca de código no se va a traducir o si la cadena no se expone al usuario final o a un desarrollador que usa la biblioteca de código.

Los usuarios pueden eliminar el ruido de los métodos que no deben pasar cadenas localizadas cambiando el nombre del parámetro o de la propiedad, o marcando estos elementos como condicionales.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un método que produce una excepción cuando uno de sus dos argumentos está fuera del intervalo. En el primer argumento, se pasa al constructor de la excepción una cadena literal, que infringe esta regla. En el segundo argumento, al constructor se le pasa correctamente una cadena recuperada <xref:System.Resources.ResourceManager>a través de.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Vea también

- [Recursos en aplicaciones de escritorio](/dotnet/framework/resources/index)