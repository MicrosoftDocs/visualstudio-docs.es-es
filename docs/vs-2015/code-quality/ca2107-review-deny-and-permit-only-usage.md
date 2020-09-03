---
title: 'CA2107: revisar el uso de deny y solo permitir | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547776"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Revisar el uso de Deny y PermitOnly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|Identificador de comprobación|CA2107|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método contiene una comprobación de seguridad que especifica las acciones de seguridad PermitOnly o deny.

## <a name="rule-description"></a>Descripción de la regla
 El [uso del método PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) y <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> las acciones de seguridad solo deben utilizarlos los que tengan conocimientos avanzados de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] seguridad. Debería realizarse una revisión de la seguridad del código que utiliza estas acciones de seguridad.

 Deny modifica el comportamiento predeterminado del recorrido de la pila que se produce como respuesta a una demanda de seguridad. Permite especificar permisos que no se deben conceder mientras dure el método de denegación, independientemente de los permisos reales de los llamadores de la pila de llamadas. Si el recorrido de la pila detecta un método protegido por deny y si el permiso solicitado está incluido en los permisos denegados, se produce un error en el recorrido de la pila. PermitOnly también modifica el comportamiento predeterminado del recorrido de la pila. Permite que el código especifique solo los permisos que se pueden conceder, independientemente de los permisos de los llamadores. Si el recorrido de la pila detecta un método protegido por PermitOnly y si el permiso solicitado no se incluye en los permisos especificados por PermitOnly, se produce un error en el recorrido de la pila.

 El código que se basa en estas acciones se debe evaluar detenidamente para detectar vulnerabilidades de seguridad debido a su utilidad limitada y a un comportamiento sutil. Tenga en cuenta lo siguiente.

- Las [peticiones de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) no se ven afectadas por deny o PermitOnly.

- Si deny o PermitOnly se producen en el mismo marco de pila que la demanda que provoca el recorrido de la pila, las acciones de seguridad no tienen ningún efecto.

- Normalmente, los valores que se usan para construir permisos basados en ruta de acceso se pueden especificar de varias maneras. Denegar el acceso a un formulario de la ruta de acceso no deniega el acceso a todos los formularios. Por ejemplo, si se asigna un recurso compartido de archivos \\ \Server\Share a una unidad de red X:, para denegar el acceso a un archivo en el recurso compartido, debe denegar \\ Compartido\archivo, X:\file y todas las demás rutas que tengan acceso al archivo.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>Puede finalizar un recorrido de pila antes de que se alcance deny o PermitOnly.

- Si una denegación tiene algún efecto, es decir, cuando un llamador tiene un permiso que está bloqueado por deny, el llamador puede tener acceso al recurso protegido directamente, omitiendo la denegación. Del mismo modo, si el autor de la llamada no tiene el Permiso denegado, se produciría un error en el recorrido de pila sin denegar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cualquier uso de estas acciones de seguridad producirá una infracción. Para corregir una infracción, no utilice estas acciones de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de completar una revisión de seguridad.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran algunas limitaciones de deny.

 La siguiente biblioteca contiene una clase que tiene dos métodos que son idénticos salvo por las demandas de seguridad que los protegen.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Ejemplo
 En la siguiente aplicación se muestran los efectos de deny en los métodos protegidos de la biblioteca.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Demand: deny del autor de la llamada no tiene ningún efecto a petición con el permiso declarado.** 
 **LinkDemand: el llamador deny no tiene ningún efecto en LinkDemand con el permiso imserted.** 
 **LinkDemand: el autor de la llamada no tiene ningún efecto con código protegido por LinkDemand.** 
 **LinkDemand: esta denegación no tiene ningún efecto con código protegido por LinkDemand.**
## <a name="see-also"></a>Consulte también
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [invalidar las comprobaciones de seguridad](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [mediante el método PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
