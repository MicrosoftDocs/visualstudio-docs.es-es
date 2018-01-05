---
title: 'CA2107: Revisar denegar y permitir el uso | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3d6f514546c298a134785740fe7bbf948031bc74
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Revisar el uso de Deny y PermitOnly
|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|Identificador de comprobación|CA2107|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método contiene una comprobación de seguridad que especifica la acción de seguridad PermitOnly o Deny.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> acción de seguridad debe usarse únicamente por aquellos que tienen conocimientos avanzados de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] seguridad. Debería realizarse una revisión de la seguridad del código que utiliza estas acciones de seguridad.  
  
 Denegar modifica el comportamiento predeterminado del recorrido de pila que se produce en respuesta a una petición de seguridad. Permite especificar los permisos que no deben concederse para la duración del método denegar, sin tener en cuenta los permisos reales de los llamadores de la pila de llamadas. Si el recorrido de pila detecta un método que está protegido por Deny, y si el permiso solicitado está incluido en los permisos denegados, se produce un error en el recorrido de pila. PermitOnly también modifica el comportamiento predeterminado del recorrido de pila. Permite al código para especificar únicamente aquellos permisos que se pueden conceder, independientemente de los permisos de los llamadores. Si el recorrido de pila detecta un método que está protegido por PermitOnly y, si el permiso solicitado no se incluye en los permisos especificados por PermitOnly, se produce un error en el recorrido de pila.  
  
 Código que se basa en estas acciones se debería evaluar cuidadosamente las vulnerabilidades de seguridad debido a su utilidad limitada y comportamiento. Considere el siguiente caso:  
  
-   [Las peticiones de vínculo](/dotnet/framework/misc/link-demands) no se ven afectados por Deny y PermitOnly.  
  
-   Si se produce la Deny o PermitOnly en el mismo marco de pila como petición que provoca el recorrido de pila, las acciones de seguridad no tienen ningún efecto.  
  
-   Normalmente pueden especificarse valores que se usan para crear permisos basados en la ruta de acceso de varias maneras. Denegar el acceso a un formulario de la ruta de acceso no deniega el acceso a todas las formas. Por ejemplo, si un recurso compartido de archivos \\\Server\Share se asigna a una unidad de red X:, para denegar el acceso a un archivo en el recurso compartido, debe denegar \\\Server\Share\File, X:\File y todas las rutas que tiene acceso al archivo.  
  
-   Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> puede finalizar un recorrido de pila antes de alcanza Deny o PermitOnly.  
  
-   Si una instrucción Deny tenga cualquier efecto, es decir, cuando el llamador tiene un permiso que está bloqueado por Deny, el llamador puede acceder al recurso protegido directamente, omitiendo el Deny. De forma similar, si el llamador no dispone del permiso denegado, el recorrido de pila produciría un error sin Deny.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cualquier uso de estas acciones de seguridad provocará una infracción. Para corregir una infracción, no utilice estas acciones de seguridad.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima las advertencias de esta regla solo después de completar una revisión de seguridad.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra algunas limitaciones de Deny.  
  
 La biblioteca siguiente contiene una clase que tiene dos métodos que son idénticos salvo por las peticiones de seguridad que protegen.  
  
 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 La aplicación siguiente muestra los efectos de Deny en los métodos protegidos de la biblioteca.  
  
 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
 **Petición: Deny del autor de llamada no tiene ningún efecto a petición con el permiso validado.**  
**LinkDemand: Deny del autor de llamada no tiene ningún efecto en LinkDemand con el permiso validado.**  
**LinkDemand: Deny del autor de llamada no tiene ningún efecto con el código protegido por LinkDemand.**  
**LinkDemand: Este Deny no tiene ningún efecto con el código protegido por LinkDemand.**   
## <a name="see-also"></a>Vea también  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)   

