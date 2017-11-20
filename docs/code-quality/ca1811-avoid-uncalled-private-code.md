---
title: "CA1811: Evitar código privado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fc7bac9804c42cb7910df6b6d89ad766b09ee0d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitar código privado al que no se llama
|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|Identificador de comprobación|CA1811|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Miembro privado o interno (nivel de ensamblado) no tiene llamadores en el ensamblado, no es invocado por common language runtime y no es invocado por un delegado. Esta regla no comprueba los miembros siguientes:  
  
-   Miembros de interfaz explícita.  
  
-   Constructores estáticos.  
  
-   Constructores de serialización.  
  
-   Los métodos marcados con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Miembros que son reemplazos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla puede notificar los falsos positivos si producen puntos de entrada que no estén identificados por la lógica de la regla. Además, un compilador puede emitir código noncallable en un ensamblado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el código noncallable o agregue código que lo llama.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)