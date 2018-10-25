---
title: 'CA1716: Los identificadores no deberían coincidir con palabras clave | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 000e28642a10c565e525b2714eed0d7abaca9340
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858880"
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
 Un nombre de un espacio de nombres, un tipo o miembro virtual o de interfaz coincide con una palabra clave reservada en un lenguaje de programación.

## <a name="rule-description"></a>Descripción de la regla
 Los identificadores para los espacios de nombres, tipos y virtual y los miembros de interfaz no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino common language runtime. Según el idioma que se usa y la palabra clave, las ambigüedades y errores del compilador pueden dificultar la biblioteca usar.

 Esta regla comprueba las palabras clave en los idiomas siguientes:

- Visual Basic

- C#

- C++/CLI

  Comparación entre mayúsculas y minúsculas se utiliza para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] comparación distingue mayúsculas de minúsculas y palabras clave se usa para los demás idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre que no aparece en la lista de palabras clave.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si están convencidos de que el identificador no confundirá a los usuarios de la API, y que la biblioteca se puede usar en todos los idiomas disponibles en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].



