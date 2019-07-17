---
title: 'CA1900: Campos de tipo de valor deberían ser portátiles | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97a83bf4ba71d0adc71fdb96d4e1c865358c08e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203098"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Los campos de tipo de valor deben ser portátiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1900: Campos de tipo de valor deberían ser portátiles](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).  
  
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|Identificador de comprobación|CA1900|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Importante: si el campo puede verse fuera del ensamblado.<br /><br /> No-importante: si el campo no está visible fuera del ensamblado.|  
  
## <a name="cause"></a>Causa  
 Esta regla comprueba que las estructuras declaradas con un diseño explícito se alinearán correctamente cuando se calculan las referencias a código no administrado en sistemas operativos de 64 bits. IA-64 no permitir accesos memoria no alineada y el proceso se bloqueará si no se soluciona esta infracción.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Estructuras que tienen un diseño explícito que contiene campos desalineados provocan bloqueos en sistemas operativos de 64 bits.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Deben tener todos los campos que tengan menos de 8 bytes desplazamientos que son un múltiplo de su tamaño y los campos que son 8 bytes o más deben tener los desplazamientos que son un múltiplo de 8. Otra solución consiste en usar `LayoutKind.Sequential` en lugar de `LayoutKind.Explicit`, si es razonable.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Esta advertencia se debe suprimir solo si se produce en error.
