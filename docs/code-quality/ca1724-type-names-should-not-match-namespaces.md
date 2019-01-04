---
title: 'CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c28bf4af55e1c12045357a76e3488ff4083fcee5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848946"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Los nombres de tipo no deberían coincidir con los espacios de nombres

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|Identificador de comprobación|CA1724|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un nombre de tipo coincide con un nombre de espacio de nombres que se hace referencia que tenga uno o varios de los tipos visibles externamente. La comparación de nombre distingue mayúsculas de minúsculas.

## <a name="rule-description"></a>Descripción de la regla

Los nombres de tipo creados por el usuario no deberían coincidir con los nombres de espacios de nombres que se hace referencia que tienen tipos visibles externamente. Si infringe esta regla puede reducir la utilización de la biblioteca.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el tipo de modo que no coincide con el nombre de un espacio de nombres que se hace referencia con tipos visibles externamente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Para el desarrollo nuevo, no conocidos se producen escenarios donde se debe suprimir una advertencia de esta regla. Antes de suprimir la advertencia, considere cuidadosamente cómo se podrían confundir a los usuarios de la biblioteca por el nombre coincidente. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.