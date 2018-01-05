---
title: "CA1900: Los campos de tipo de valor deberían ser portátiles | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f023749c16a1c4fed36654036813007a83b21a72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Los campos de tipos de valor deberían ser portátiles
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|Identificador de comprobación|CA1900|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Problemático: si el campo se puede ver desde fuera del ensamblado.<br /><br /> Poco problemático: si el campo no está visible fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Esta regla comprueba que las estructuras declaradas con un diseño explícito se alinearán correctamente cuando se calculan las referencias a código no administrado en sistemas operativos de 64 bits. IA-64 no permite accesos memoria no alineada y el proceso se bloqueará si no se corrige esta infracción.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Estructuras que tienen un diseño explícito que contiene campos no alineados provocan bloqueos en sistemas operativos de 64 bits.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Deben tener todos los campos que son menores que 8 bytes desplazamientos que son un múltiplo del tamaño y los campos que son de 8 bytes o más deben tener los desplazamientos que son un múltiplo de 8. Otra solución consiste en usar `LayoutKind.Sequential` en lugar de `LayoutKind.Explicit`, si es razonable.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Esta advertencia se debe suprimir solo si produce por un error.