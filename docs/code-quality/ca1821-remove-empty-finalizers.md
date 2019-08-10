---
title: 'CA1821: Quitar finalizadores vacíos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921368"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Quitar finalizadores vacíos

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|Identificador de comprobación|CA1821|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo implementa un finalizador que está vacío, llama solo al finalizador de tipo base o llama únicamente a métodos emitidos condicionalmente.

## <a name="rule-description"></a>Descripción de la regla
Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto. El recolector de elementos no utilizados ejecutará el finalizador antes de recopilar el objeto. Esto significa que se requerirán dos colecciones para recopilar el objeto. Un finalizador vacío incurrirá en esta sobrecarga adicional sin ninguna ventaja.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Quite el finalizador vacío. Si se requiere un finalizador para la depuración, incluya el finalizador `#if DEBUG / #endif` completo en las directivas.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima un mensaje de esta regla. Un error al suprimir la finalización disminuye el rendimiento y no proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un finalizador vacío que se debe quitar, un finalizador que debe incluirse en `#if DEBUG / #endif` las directivas y un finalizador que usa las `#if DEBUG / #endif` directivas correctamente.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]