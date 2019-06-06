---
title: 'CA2107: Revisar el uso de Deny y PermitOnly'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7f3bdc6351f30d5cad60a7ed9663824fa3d434
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714705"
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

El <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> acción de seguridad debe usarse únicamente por los usuarios que tengan conocimientos avanzados de seguridad de. NET. Debería realizarse una revisión de la seguridad del código que utiliza estas acciones de seguridad.

Denegar modifica el comportamiento predeterminado del recorrido de pila que se produce en respuesta a una petición de seguridad. Permite especificar los permisos que no se deben conceder para la duración del método denegar, sin tener en cuenta los permisos reales de los llamadores de la pila de llamadas. Si el recorrido de pila detecta un método que está protegido por Deny, y si se incluye el permiso exigido en los permisos denegados, se produce un error en el recorrido de pila. PermitOnly también modifica el comportamiento predeterminado del recorrido de pila. Permite al código especificar sólo aquellos permisos que se pueden conceder, independientemente de los permisos de los llamadores. Si el recorrido de pila detecta un método que está protegido por PermitOnly y, si el permiso solicitado no se incluye en los permisos que se especifican por PermitOnly, se produce un error en el recorrido de pila.

Código que se basa en estas acciones se debería evaluar cuidadosamente las vulnerabilidades de seguridad debido a su utilidad limitada y el comportamiento. Considere el siguiente caso:

- [Las peticiones de vínculo](/dotnet/framework/misc/link-demands) no se ven afectados por Deny o PermitOnly.

- Si Deny o PermitOnly se produce en el mismo marco de pila como la demanda que hace que el recorrido de pila, las acciones de seguridad tienen ningún efecto.

- Normalmente, los valores que se usan para construir los permisos basados en la ruta de acceso pueden especificarse de varias maneras. Denegar el acceso a un formulario de la ruta de acceso no deniega el acceso a todas las formas. Por ejemplo, si un recurso compartido de archivos \\\Server\Share se asigna a una unidad de red X:, para denegar el acceso a un archivo en el recurso compartido, debe denegar \\\Server\Share\File X:\File y cualquier otra ruta que se obtiene acceso al archivo.

- Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> puede finalizar un recorrido de pila antes de alcanza Deny o PermitOnly.

- Si una instrucción Deny tiene ningún efecto, es decir, cuando el llamador tiene un permiso que está bloqueado por Deny, el llamador puede acceder al recurso protegido directamente, omitiendo la denegación. De forma similar, si el llamador no tiene el permiso denegado, el recorrido de pila produciría un error sin Deny.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cualquier uso de estas acciones de seguridad provocará una infracción. Para corregir una infracción, no utilice estas acciones de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Suprima una advertencia de esta regla solo después de completar una revisión de seguridad.

## <a name="example-1"></a>Ejemplo 1

El ejemplo siguiente muestra algunas limitaciones de Deny. La biblioteca contiene una clase que tiene dos métodos que son idénticos salvo por las peticiones de seguridad que protegen.

[!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Ejemplo 2

La aplicación siguiente muestra los efectos de Deny en los métodos protegidos de la biblioteca.

[!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Vea también

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)