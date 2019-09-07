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
ms.openlocfilehash: f616547738c7c58d61289b2be71c8e56a1a427c8
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766071"
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

Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional que implica el seguimiento de la duración de los objetos. El recolector de elementos no utilizados ejecuta el finalizador antes de recopilar el objeto. Esto significa que se necesitan al menos dos colecciones para recopilar el objeto. Un finalizador vacío incurrirá en esta sobrecarga adicional sin ninguna ventaja.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Quite el finalizador vacío. Si se requiere un finalizador para la depuración, incluya el finalizador `#if DEBUG / #endif` completo en las directivas.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima un mensaje de esta regla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un finalizador vacío que se debe quitar, un finalizador que debe incluirse en `#if DEBUG / #endif` las directivas y un finalizador que usa las `#if DEBUG / #endif` directivas correctamente.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
