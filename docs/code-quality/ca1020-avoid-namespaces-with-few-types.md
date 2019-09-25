---
title: 'CA1020: Evitar los espacios de nombres con pocos tipos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236227"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitar los espacios de nombres con pocos tipos

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|Identificador de comprobación|CA1020|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un espacio de nombres distinto del espacio de nombres global contiene menos de cinco tipos.

## <a name="rule-description"></a>Descripción de la regla

Asegúrese de que cada uno de los espacios de nombres tiene una organización lógica y que existe un motivo válido para colocar los tipos en un espacio de nombres rellenado de forma dispersa. Los espacios de nombres deben contener tipos que se usan juntos en la mayoría de los escenarios. Cuando las aplicaciones son mutuamente excluyentes, los tipos se deben encontrar en espacios de nombres independientes. Por ejemplo, el <xref:System.Web.UI> espacio de nombres contiene tipos que se usan en aplicaciones web y <xref:System.Windows.Forms> el espacio de nombres contiene tipos que [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]se usan en aplicaciones basadas en. Aunque ambos espacios de nombres tienen tipos que controlan aspectos de la interfaz de usuario, estos tipos no están diseñados para su uso en la misma aplicación. Por lo tanto, se encuentran en espacios de nombres independientes. La organización del espacio de nombres meticuloso también puede ser útil porque aumenta la capacidad de detección de una característica. Al examinar la jerarquía de espacios de nombres, los consumidores de la biblioteca deben poder localizar los tipos que implementan una característica.

> [!NOTE]
> Los tipos y permisos en tiempo de diseño no se deben combinar en otros espacios de nombres para cumplir esta directriz. Estos tipos pertenecen a sus propios espacios de nombres debajo del espacio de nombres principal y los espacios de nombres `.Design` deben `.Permissions`terminar en y, respectivamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, intente combinar los espacios de nombres que contienen solo unos pocos tipos en un espacio de nombres único.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando el espacio de nombres no contiene tipos que se utilizan con los tipos en los otros espacios de nombres.