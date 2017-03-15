---
title: "CA2107: Revisar el uso de Deny y PermitOnly | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107: Revisar el uso de Deny y PermitOnly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|Identificador de comprobación|CA2107|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método contiene una comprobación de seguridad que especifica una acción de seguridad PermitOnly o Deny.  
  
## Descripción de la regla  
 Las acciones de seguridad [Using the PermitOnly Method](http://msdn.microsoft.com/es-es/8c7bdb7f-882f-45b7-908c-6cbaa1767649) y <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> solo deberían utilizarlas personas que tienen un conocimiento avanzado de la seguridad de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Debería realizarse una revisión de la seguridad del código que utiliza estas acciones de seguridad.  
  
 La acción Deny modifica el comportamiento predeterminado del recorrido de pila que se produce en respuesta a una demanda de seguridad.  Permite especificar los permisos que no deben concederse durante la ejecución del método de denegación, sin tener en cuenta los permisos reales de los llamadores de la pila de llamadas.  Si el recorrido de pila detecta un método protegido por Deny y el permiso solicitado está incluido en los permisos denegados, el recorrido de pila provoca un error.  PermitOnly también modifica el comportamiento predeterminado del recorrido de pila.  Permite al código especificar solo aquellos permisos que se pueden conceder sin tener en cuenta los permisos de los llamadores.  Si el recorrido de pila detecta un método protegido por PermitOnly y el permiso solicitado no está incluido en los permisos especificados por PermitOnly, el recorrido de pila provoca un error.  
  
 El código basado en estas acciones se debería evaluar cuidadosamente para detectar vulnerabilidades de seguridad debido a su utilidad limitada y al comportamiento sutil.  Considere el siguiente caso:  
  
-   [Link Demands](../Topic/Link%20Demands.md) no se ven afectados por Deny o PermitOnly.  
  
-   Si se producen Deny o PermitOnly en el mismo marco de pila como petición que provoca el recorrido de pila, las acciones de seguridad no tendrían ningún efecto.  
  
-   Los valores que se utilizan para crear permisos basados en la ruta de acceso normalmente se pueden especificar de varias maneras.  El acceso denegado a uno formulario de la ruta de acceso no deniega el acceso a todos los formularios.  Por ejemplo, si un recurso compartido de archivos \\\\Server\\Share se asigna a una unidad de red X:, para denegar el acceso a un archivo del recurso compartido, deberá denegar el acceso a \\\\Server\\Share\\File, X:\\File o cualquier otra ruta que tenga acceso al archivo.  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> puede finalizar un recorrido de pila antes de alcanzar Deny o PermitOnly.  
  
-   Si Deny provoca un efecto, por ejemplo, cuando el llamador tiene un permiso bloqueado por Deny, el llamador puede obtener acceso directamente al recurso compartido omitiendo el permiso Deny.  De forma similar, si el llamador no tiene el permiso denegado, se produciría un error en el recorrido de pila sin el permiso Deny.  
  
## Cómo corregir infracciones  
 Cualquier uso de estas acciones de seguridad provocará una infracción.  Para corregir una infracción, no utilice estas acciones de seguridad.  
  
## Cuándo suprimir advertencias  
 Sólo suprima una advertencia de esta regla después de completar una revisión de seguridad.  
  
## Ejemplo  
 El ejemplo siguiente muestra algunas limitaciones de Deny.  
  
 La siguiente biblioteca contiene una clase con dos métodos que son idénticos salvo las peticiones de seguridad que los protegen.  
  
 [!code-cs[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente muestra los efectos de Deny en los métodos protegidos de la biblioteca.  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Demand: el permiso Denegar del llamador no tiene ningún efecto sobre Demand con el permiso validado.**  
**LinkDemand: el permiso Denegar del llamador no tiene ningún efecto sobre LinkDemand con el permiso validado.**  
**LinkDemand: el permiso Denegar del llamador no tiene ningún efecto sobre el código protegido por LinkDemand.**  
**LinkDemand: este permiso Denegar no tiene ningún efecto sobre el código protegido por LinkDemand.**   
## Vea también  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/es-es/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/es-es/8c7bdb7f-882f-45b7-908c-6cbaa1767649)