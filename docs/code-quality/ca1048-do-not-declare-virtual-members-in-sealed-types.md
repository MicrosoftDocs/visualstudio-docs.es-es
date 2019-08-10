---
title: 'CA1048: No declarar miembros virtuales en tipos sellados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 430ed0b23d62bd46a9764bfb0a3834e0decd476b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922593"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: No declarar miembros virtuales en tipos sellados

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|Identificador de comprobación|CA1048|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público está sellado y declara un método que es Both `virtual` (`Overridable` en Visual Basic) y no final. Esta regla no notifica las infracciones de los tipos de delegado, que deben seguir este patrón.

## <a name="rule-description"></a>Descripción de la regla
Los tipos declaran los métodos como virtuales para que los tipos heredados puedan reemplazar la implementación del método virtual. Por definición, no se puede heredar de un tipo sellado, lo que hace que un método virtual en un tipo sellado no tenga sentido.

El Visual Basic y C# los compiladores no permiten a los tipos infringir esta regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, haga que el método sea no virtual o haga que el tipo sea heredable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. Si se deja el tipo en su estado actual, se pueden producir problemas de mantenimiento y no se proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]