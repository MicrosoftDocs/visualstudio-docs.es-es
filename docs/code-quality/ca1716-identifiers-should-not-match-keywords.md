---
title: "CA1716: Los identificadores no deberían coincidir con palabras clave | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 619fc7867d14a26f2c3b674b4b8ac8b2d8fba114
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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