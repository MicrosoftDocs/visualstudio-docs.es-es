---
title: 'CA1707: Los identificadores no deberían contener subrayado | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7973646aab545484287f5628eb0fa3cf3629db84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189206"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deben contener caracteres de subrayado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1707: Los identificadores no deberían contener subrayado](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|Identificador de comprobación|CA1707|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> No problemático: cuando se produce en parámetros de tipo|  
  
## <a name="cause"></a>Causa  
 El nombre de un identificador contiene el carácter de subrayado (_).  
  
## <a name="rule-description"></a>Descripción de la regla  
 Por convención, los nombres del identificador no contienen el carácter de subrayado (_). La regla comprueba espacios de nombres, tipos, miembros y parámetros.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Quite todos los caracteres de subrayado del nombre.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
