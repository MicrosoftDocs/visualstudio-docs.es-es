---
title: 'CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 027ec9b19bcf8a4a10e8b973b86e57be2dbc6be7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838327"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros

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