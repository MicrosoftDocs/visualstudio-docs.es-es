---
title: 'CA1048: No declarar miembros virtuales en tipos sellados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 531590eee7804debfc8ccfb9a8e508107fba71df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006741"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: No declarar miembros virtuales en tipos sellados

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|Identificador de comprobación|CA1048|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público está sellado y declara un método que se encuentra tanto `virtual` (`Overridable` en Visual Basic) y no final. Esta regla no informa de las infracciones para tipos de delegado, que deben seguir este patrón.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos declaran los métodos como virtuales para que los tipos heredados puedan reemplazar la implementación del método virtual. Por definición, no puede heredar de un tipo sealed, pasa a un método virtual en un tipo sealed no tiene sentido.

 Los compiladores de Visual Basic y C# no permiten tipos que infringen esta regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que el método no virtual o convierta el tipo puede heredar.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Lo que deja el tipo en su estado actual puede causar problemas de mantenimiento y no proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]