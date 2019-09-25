---
title: 'CA1025: Reemplazar argumentos repetitivos por una matriz de parámetros'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65d64dd4e881c41b17cd7cb9dc072a6fe800766
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236144"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Reemplazar argumentos repetitivos por una matriz de parámetros

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|Identificador de comprobación|CA1025|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un método público o protegido en un tipo público tiene más de tres parámetros y los tres últimos parámetros son del mismo tipo.

## <a name="rule-description"></a>Descripción de la regla
Use una matriz de parámetros en lugar de argumentos repetidos cuando se desconoce el número exacto de argumentos y los argumentos de variable son del mismo tipo, o se pueden pasar como el mismo tipo. Por ejemplo, el <xref:System.Console.WriteLine%2A> método proporciona una sobrecarga de uso general que usa una matriz de parámetros para aceptar cualquier número <xref:System.Object> de argumentos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, reemplace los argumentos repetidos por una matriz de parámetros.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Siempre es seguro suprimir una advertencia de esta regla. sin embargo, este diseño podría provocar problemas de uso.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]