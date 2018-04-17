---
title: 'CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: a9d42e7109d75f14d51e0e7834bc996f6f8864dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|Identificador de comprobación|CA1025|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un método público o protegido en un tipo público tiene más de tres parámetros, y los últimos tres parámetros son del mismo tipo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Use una matriz de parámetros en lugar de argumentos repetidos cuando se desconoce el número exacto de argumentos y los argumentos de variable son del mismo tipo o pueden pasarse como el mismo tipo. Por ejemplo, el <xref:System.Console.WriteLine%2A> método proporciona una sobrecarga de uso general que usa una matriz de parámetros para aceptar cualquier número de <xref:System.Object> argumentos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace los argumentos repetidos con una matriz de parámetros.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Siempre es seguro suprimir una advertencia de esta regla; Sin embargo, este diseño podría provocar problemas de uso.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]