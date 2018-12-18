---
title: 'CA1821: Quitar los finalizadores vacíos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0ea2ca64009071538848c71f5bf9a825250cb82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900090"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Quitar los finalizadores vacíos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|Identificador de comprobación|CA1821|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo implementa un finalizador que está vacío, llama sólo al finalizador del tipo base o llama sólo a los métodos emitidos condicionalmente.

## <a name="rule-description"></a>Descripción de la regla
 Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto. El recolector de elementos no utilizados se ejecutará el finalizador antes de que recopila el objeto. Esto significa que dos colecciones serán necesarias para recopilar el objeto. Un finalizador vacío produce esta sobrecarga adicional sin ningún beneficio.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el finalizador vacío. Si un finalizador se requiere para la depuración, incluya el finalizador todo en `#if DEBUG / #endif` directivas.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima un mensaje de esta regla. Error al suprimir la finalización disminuye el rendimiento y no ofrece ninguna ventaja.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un finalizador vacío que se debe quitar, un finalizador que debe incluirse en `#if DEBUG / #endif` directivas y un finalizador que usa el `#if DEBUG / #endif` directivas correctamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]



