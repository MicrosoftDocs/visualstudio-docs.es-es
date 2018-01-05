---
title: "CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9e6142ff6670edd6eb1f4cad009b68005b27a86f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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