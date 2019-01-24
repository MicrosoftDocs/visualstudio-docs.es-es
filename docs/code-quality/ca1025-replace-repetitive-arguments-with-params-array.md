---
title: 'CA1025: Reemplazar argumentos repetitivos por una matriz de parámetros'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e4d2bb3330883e44b015698b740cd6403f953dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868870"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Reemplazar argumentos repetitivos por una matriz de parámetros

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|Identificador de comprobación|CA1025|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene más de tres parámetros y los últimos tres parámetros son del mismo tipo.

## <a name="rule-description"></a>Descripción de la regla
 Use una matriz de parámetros en lugar de argumentos repetidos cuando se desconoce el número exacto de argumentos y los argumentos de variable son del mismo tipo o pueden pasarse como el mismo tipo. Por ejemplo, el <xref:System.Console.WriteLine%2A> método proporciona una sobrecarga de uso general que usa una matriz de parámetros para aceptar cualquier número de <xref:System.Object> argumentos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace los argumentos repetidos con una matriz de parámetros.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Siempre es seguro suprimir una advertencia de esta regla; Sin embargo, este diseño puede provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]