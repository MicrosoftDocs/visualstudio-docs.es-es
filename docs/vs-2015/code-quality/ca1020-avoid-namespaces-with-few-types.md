---
title: 'CA1020: Evitar espacios de nombres con pocos tipos | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c94cf09b43eb09482be4a30d9f0b9206678c4dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435829"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitar los espacios de nombres con pocos tipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|Identificador de comprobación|CA1020|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un espacio de nombres distinto del espacio de nombres global contiene menos de cinco tipos.

## <a name="rule-description"></a>Descripción de la regla
 Asegúrese de que cada uno de los espacios de nombres tiene una organización lógica y que existe un motivo válido para los tipos en un espacio de nombres apenas lleno. Los espacios de nombres deben contener tipos que se utilizan conjuntamente en la mayoría de los escenarios. Cuando sus aplicaciones son mutuamente excluyentes, tipos deben estar en espacios de nombres independientes. Por ejemplo, el <xref:System.Web.UI> espacio de nombres contiene tipos que se usan en aplicaciones Web, y el <xref:System.Windows.Forms> espacio de nombres contiene tipos que se usan en [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]-aplicaciones basadas en. Aunque ambos espacios de nombres tienen tipos que controlan aspectos de la interfaz de usuario, estos tipos no están diseñados para su uso en la misma aplicación. Por lo tanto, se encuentran en espacios de nombres independientes. Organización del espacio de nombres especial también puede resultar útil porque aumenta la detectabilidad de una característica. Mediante el examen de la jerarquía del espacio de nombres, los consumidores de la biblioteca deben ser capaz de encontrar los tipos que implementan una característica.

> [!NOTE]
> No se deben combinar los permisos y los tipos de tiempo de diseño en otros espacios de nombres para cumplir con esta directriz. Estos tipos pertenecen a sus propios espacios de nombres por debajo de su espacio de nombres principal y los espacios de nombres deben terminar en `.Design` y `.Permissions`, respectivamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, intente combinar los espacios de nombres que contienen solo unos pocos tipos en un único espacio de nombres.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando el espacio de nombres no contiene tipos que se usan con los tipos en otros espacios de nombres.
