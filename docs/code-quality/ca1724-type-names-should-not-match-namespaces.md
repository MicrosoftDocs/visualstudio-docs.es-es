---
title: 'CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3554a352cb1c32879397e91dba3ce53f31a14bd0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233858"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|Identificador de comprobación|CA1724|
|Categoría|Microsoft.Naming|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un nombre de tipo coincide con un nombre de espacio de nombres al que se hace referencia que tiene uno o más tipos visibles externamente. La comparación de nombres no distingue entre mayúsculas y minúsculas.

## <a name="rule-description"></a>Descripción de la regla

Los nombres de tipos creados por el usuario no deben coincidir con los nombres de los espacios de nombres a los que se hace referencia y que tienen tipos visibles externamente. Infringir esta regla puede reducir la facilidad de uso de la biblioteca.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre del tipo para que no coincida con el nombre de un espacio de nombres al que se hace referencia que tenga tipos visibles externamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

En el desarrollo nuevo, no se produce ningún escenario conocido en el que debe suprimir una advertencia de esta regla. Antes de suprimir la advertencia, considere detenidamente cómo puede confundir los usuarios de la biblioteca con el nombre coincidente. En el caso de las bibliotecas de envío, es posible que tenga que suprimir una advertencia de esta regla.