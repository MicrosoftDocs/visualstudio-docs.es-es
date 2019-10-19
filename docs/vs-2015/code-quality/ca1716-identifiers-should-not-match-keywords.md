---
title: 'CA1716: los identificadores no deben coincidir con palabras clave | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f81aec5973d1915ba646c20c3b84186443678754
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669102"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Los identificadores no deberían coincidir con palabras clave
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|Identificador de comprobación|CA1716|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un nombre de un espacio de nombres, un tipo o un viritual o un miembro de interfaz coincide con una palabra clave reservada en un lenguaje de programación.

## <a name="rule-description"></a>Descripción de la regla
 Los identificadores de los espacios de nombres, los tipos y los miembros virtuales y de interfaz no deben coincidir con las palabras clave definidas por los lenguajes que tienen como destino el Common Language Runtime. Dependiendo del lenguaje que se use y de la palabra clave, los errores del compilador y las ambigüedades pueden dificultar el uso de la biblioteca.

 Esta regla comprueba las palabras clave en los idiomas siguientes:

- Visual Basic

- C#

- C++/CLI

  La comparación sin distinción entre mayúsculas y minúsculas se usa para palabras clave de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y la comparación con distinción entre mayúsculas y minúsculas se usa para los demás idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre que no aparezca en la lista de palabras clave.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si está convencido de que el identificador no confundirá a los usuarios de la API y que la biblioteca se puede usar en todos los idiomas disponibles en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
