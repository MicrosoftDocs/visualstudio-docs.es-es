---
title: 'CA1716: Los identificadores no deberían coincidir con palabras clave'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 514a062429168592fe46112ad008d0d1f4e60a28
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914789"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Los identificadores no deberían coincidir con palabras clave
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|Identificador de comprobación|CA1716|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un nombre de un espacio de nombres, un tipo o un miembro virtual o de interfaz coincide con una palabra clave reservada en un lenguaje de programación.

## <a name="rule-description"></a>Descripción de la regla
 Identificadores de espacios de nombres, tipos y virtual y los miembros de interfaz no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino common language runtime. Según el idioma que se usa y la palabra clave, ambigüedades y errores del compilador pueden dificultar la biblioteca a la utilice.

 Esta regla comprueba las palabras clave en los idiomas siguientes:

-   Visual Basic

-   C#

-   C++/CLI

 Comparación entre mayúsculas y minúsculas se utiliza para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] comparación entre mayúsculas y minúsculas y palabras clave se usa para los demás idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre que no aparece en la lista de palabras clave.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si convencido de que el identificador no confundirá a los usuarios de la API, y que la biblioteca se pueden utilizar en todos los idiomas disponibles en la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].