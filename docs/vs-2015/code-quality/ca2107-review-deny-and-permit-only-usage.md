---
title: 'CA2107: Revisión de deny y PermitOnly sólo uso | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7de14898c5fb2bb6f8e95a2af5fd6b39a54cdb1d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082157"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Revisar el uso de Deny y PermitOnly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|Identificador de comprobación|CA2107|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método contiene una comprobación de seguridad que especifica la acción de seguridad PermitOnly o Deny.

## <a name="rule-description"></a>Descripción de la regla
 El [con el método PermitOnly](http://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) y <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> acciones de seguridad deben usarse únicamente por los usuarios que tengan conocimientos avanzados de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] seguridad. Debería realizarse una revisión de la seguridad del código que utiliza estas acciones de seguridad.

 Denegar modifica el comportamiento predeterminado del recorrido de pila que se produce en respuesta a una petición de seguridad. Permite especificar los permisos que no se deben conceder para la duración del método denegar, sin tener en cuenta los permisos reales de los llamadores de la pila de llamadas. Si el recorrido de pila detecta un método que está protegido por Deny, y si se incluye el permiso exigido en los permisos denegados, se produce un error en el recorrido de pila. PermitOnly también modifica el comportamiento predeterminado del recorrido de pila. Permite al código especificar sólo aquellos permisos que se pueden conceder, independientemente de los permisos de los llamadores. Si el recorrido de pila detecta un método que está protegido por PermitOnly y, si el permiso solicitado no se incluye en los permisos que se especifican por PermitOnly, se produce un error en el recorrido de pila.

 Código que se basa en estas acciones se debería evaluar cuidadosamente las vulnerabilidades de seguridad debido a su utilidad limitada y el comportamiento. Considere el siguiente caso:

- [Las peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) no se ven afectados por Deny o PermitOnly.

- Si Deny o PermitOnly se produce en el mismo marco de pila como la demanda que hace que el recorrido de pila, las acciones de seguridad tienen ningún efecto.

- Normalmente, los valores que se usan para construir los permisos basados en la ruta de acceso pueden especificarse de varias maneras. Denegar el acceso a un formulario de la ruta de acceso no deniega el acceso a todas las formas. Por ejemplo, si un recurso compartido de archivos \\\Server\Share se asigna a una unidad de red X:, para denegar el acceso a un archivo en el recurso compartido, debe denegar \\\Server\Share\File, X:\File y cualquier otra ruta que se obtiene acceso al archivo.

- Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> puede finalizar un recorrido de pila antes de alcanza Deny o PermitOnly.

- Si una instrucción Deny tiene ningún efecto, es decir, cuando el llamador tiene un permiso que está bloqueado por Deny, el llamador puede acceder al recurso protegido directamente, omitiendo la denegación. De forma similar, si el llamador no tiene el permiso denegado, el recorrido de pila produciría un error sin Deny.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cualquier uso de estas acciones de seguridad provocará una infracción. Para corregir una infracción, no utilice estas acciones de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de completar una revisión de seguridad.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra algunas limitaciones de Deny.

 La siguiente biblioteca contiene una clase que tiene dos métodos que son idénticos salvo por las peticiones de seguridad que protegen.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra los efectos de Deny en los métodos protegidos de la biblioteca.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **A petición: Denegar la persona que llama no tiene ningún efecto a petición con el permiso validado. ** 
 **LinkDemand: Denegar la persona que llama no tiene ningún efecto en LinkDemand con el permiso validado. ** 
 **LinkDemand: Denegar la persona que llama no tiene ningún efecto con el código protegido por LinkDemand. ** 
 **LinkDemand: Este denegar no tiene ningún efecto con el código protegido por LinkDemand.**
## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [reemplazar comprobaciones de seguridad](http://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [con el método PermitOnly](http://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
