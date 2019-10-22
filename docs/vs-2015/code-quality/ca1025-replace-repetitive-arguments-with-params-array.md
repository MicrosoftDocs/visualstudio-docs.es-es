---
title: 'CA1025: reemplazar argumentos repetitivos con una matriz params | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 21d13611a3c4dd11eb691c746f8746347fb9a83b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661966"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|Identificador de comprobación|CA1025|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene más de tres parámetros y los tres últimos parámetros son del mismo tipo.

## <a name="rule-description"></a>Descripción de la regla
 Use una matriz de parámetros en lugar de argumentos repetidos cuando se desconoce el número exacto de argumentos y los argumentos de variable son del mismo tipo, o se pueden pasar como el mismo tipo. Por ejemplo, el método <xref:System.Console.WriteLine%2A> proporciona una sobrecarga de uso general que usa una matriz de parámetros para aceptar cualquier número de argumentos de <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace los argumentos repetidos por una matriz de parámetros.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Siempre es seguro suprimir una advertencia de esta regla. sin embargo, este diseño podría provocar problemas de uso.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
