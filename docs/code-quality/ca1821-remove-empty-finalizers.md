---
title: 'CA1821: Quitar los finalizadores vacíos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75c77a35fc09ea4b45bdbef756341b330bdd11df
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Quitar los finalizadores vacíos
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|Identificador de comprobación|CA1821|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo implementa un finalizador que está vacío, llama sólo al finalizador del tipo base o llama sólo a los métodos emitidos condicionalmente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto. El recolector de elementos no utilizados se ejecutará el finalizador antes de recopilar el objeto. Esto significa que dos colecciones serán necesarias para recopilar el objeto. Un finalizador vacío produce esta sobrecarga adicional sin ningún beneficio.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Quite el finalizador vacío. Si un finalizador se requiere para la depuración, incluya el finalizador todo en `#if DEBUG / #endif` directivas.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima un mensaje de esta regla. Error al suprimir la finalización disminuye el rendimiento y no proporciona ninguna ventaja.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un finalizador vacío que se debe quitar, un finalizador que debe incluirse en `#if DEBUG / #endif` directivas y un finalizador que usa el `#if DEBUG / #endif` directivas correctamente.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]