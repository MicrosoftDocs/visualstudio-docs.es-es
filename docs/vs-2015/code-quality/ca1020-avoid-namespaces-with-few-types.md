---
title: 'CA1020: Evite los espacios de nombres con pocos tipos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 81eaf2735869668b86ca8879478e3d76d77a2811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662309"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitar espacios de nombres con pocos tipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|Identificador de comprobación|CA1020|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un espacio de nombres distinto del espacio de nombres global contiene menos de cinco tipos.

## <a name="rule-description"></a>Descripción de la regla
 Asegúrese de que cada uno de los espacios de nombres tiene una organización lógica y que existe un motivo válido para colocar los tipos en un espacio de nombres rellenado de forma dispersa. Los espacios de nombres deben contener tipos que se usan juntos en la mayoría de los escenarios. Cuando las aplicaciones son mutuamente excluyentes, los tipos se deben encontrar en espacios de nombres independientes. Por ejemplo, el espacio de nombres <xref:System.Web.UI> contiene tipos que se usan en aplicaciones web y el espacio de nombres <xref:System.Windows.Forms> contiene tipos que se usan en aplicaciones basadas en [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]. Aunque ambos espacios de nombres tienen tipos que controlan aspectos de la interfaz de usuario, estos tipos no están diseñados para su uso en la misma aplicación. Por lo tanto, se encuentran en espacios de nombres independientes. La organización del espacio de nombres meticuloso también puede ser útil porque aumenta la capacidad de detección de una característica. Al examinar la jerarquía de espacios de nombres, los consumidores de la biblioteca deben poder localizar los tipos que implementan una característica.

> [!NOTE]
> Los tipos y permisos en tiempo de diseño no se deben combinar en otros espacios de nombres para cumplir esta directriz. Estos tipos pertenecen a sus propios espacios de nombres debajo del espacio de nombres principal y los espacios de nombres deben terminar en `.Design` y `.Permissions`, respectivamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, intente combinar los espacios de nombres que contienen solo unos pocos tipos en un espacio de nombres único.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando el espacio de nombres no contiene tipos que se utilizan con los tipos en los otros espacios de nombres.
