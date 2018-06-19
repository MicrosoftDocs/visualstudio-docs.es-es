---
title: 'CA1020: Evitar espacios de nombres con pocos tipos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c7aae7f5db19a8f72a0d4670727dbf787cf228e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31896496"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitar espacios de nombres con pocos tipos
|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|Identificador de comprobación|CA1020|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un espacio de nombres distinto del espacio de nombres global contiene menos de cinco tipos.

## <a name="rule-description"></a>Descripción de la regla
 Asegúrese de que cada uno de los espacios de nombres tiene una organización lógica y que existe una razón para colocar los tipos en un espacio de nombres apenas lleno. Espacios de nombres deben contener tipos que se utilizan conjuntamente en la mayoría de los escenarios. Cuando sus aplicaciones son mutuamente excluyentes, tipos deben estar en espacios de nombres independientes. Por ejemplo, el <xref:System.Web.UI> espacio de nombres contiene tipos que se usan en aplicaciones Web, y el <xref:System.Windows.Forms> espacio de nombres contiene tipos que se usan en [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-aplicaciones basadas en. Aunque ambos espacios de nombres tienen tipos que controlan aspectos de la interfaz de usuario, estos tipos no están diseñados para su uso en la misma aplicación. Por lo tanto, se encuentran en espacios de nombres independientes. Organización de espacio de nombres especial también puede resultar útil porque aumenta la detectabilidad de una característica. Mediante el examen de la jerarquía de espacio de nombres, los consumidores de biblioteca deben ser capaces de encontrar los tipos que implementan una característica.

> [!NOTE]
>  No se deberían combinar permisos y los tipos de tiempo de diseño en otros espacios de nombres para cumplir con esta directriz. Estos tipos pertenecen a sus propios espacios de nombres por debajo de su espacio de nombres principal, y los espacios de nombres deben finalizar en `.Design` y `.Permissions`, respectivamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, intente combinar los espacios de nombres que contienen tan solo unos tipos en un único espacio de nombres.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando el espacio de nombres no contiene tipos que se usan con los tipos en otros espacios de nombres.