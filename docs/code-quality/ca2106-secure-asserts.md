---
title: 'CA2106: Asegurar aserciones | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2b49ab6d6cd99dc2865be21a2ed68579922bbb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asegurar aserciones
|||  
|-|-|  
|TypeName|SecureAsserts|  
|Identificador de comprobación|CA2106|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el llamador, el autor de la llamada podría ejecutar código indirectamente mediante el uso de sus permisos. Las aserciones sin comprobaciones de seguridad están permitidas sólo cuando esté seguro de que la aserción no se puede usar de manera perjudicial. Una aserción es inofensiva si el código que se llama es inocuo o los usuarios no pueden pasar información arbitraria al código que llama.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue una demanda de seguridad para el método o su tipo declarativo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla solo después de una revisión cuidadosa de la seguridad.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)