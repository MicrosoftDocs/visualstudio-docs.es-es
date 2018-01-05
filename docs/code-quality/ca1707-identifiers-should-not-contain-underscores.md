---
title: "CA1707: Los identificadores no deberían contener subrayado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 582b7c95663633a4aada6a479a17306354c16b7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deberían contener subrayado
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|Identificador de comprobación|CA1707|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en los ensamblados<br /><br /> Poco problemático: cuando se desencadena en parámetros de tipo|  
  
## <a name="cause"></a>Motivo  
 El nombre de un identificador contiene el carácter de subrayado (_).  
  
## <a name="rule-description"></a>Descripción de la regla  
 Por convención, los nombres del identificador no contienen el carácter de subrayado (_). La regla comprueba espacios de nombres, tipos, miembros y parámetros.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Quite todos los caracteres de subrayado del nombre.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)