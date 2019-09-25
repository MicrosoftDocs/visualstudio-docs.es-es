---
title: 'CA1003: Utilizar instancias genéricas de controlador de eventos'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c654da177e4a9cf820887cf74977a4c3da5a57b6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236653"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Utilizar instancias genéricas de controlador de eventos

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|Identificador de comprobación|CA1003|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo contiene un delegado que devuelve void y cuya firma contiene dos parámetros (el primero es un objeto y el segundo un tipo que se puede asignar a EventArgs) y el ensamblado contenedor tiene como destino .NET.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Antes de .net, para pasar información personalizada al controlador de eventos, se tenía que declarar un nuevo delegado que especifica una clase que se deriva de la <xref:System.EventArgs?displayProperty=fullName> clase. En .net, el delegado <xref:System.EventHandler%601?displayProperty=fullName> genérico permite que cualquier clase derivada de <xref:System.EventArgs> se use junto con el controlador de eventos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el delegado y reemplace su uso con el <xref:System.EventHandler%601?displayProperty=fullName> delegado.

Si el delegado se genera automáticamente mediante el compilador Visual Basic, cambie la sintaxis de la declaración de evento para <xref:System.EventHandler%601?displayProperty=fullName> usar el delegado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un delegado que infringe la regla. En el Visual Basic ejemplo, los comentarios describen cómo modificar el ejemplo para satisfacer la regla. En el C# ejemplo siguiente, se muestra el código modificado.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

En el fragmento de código siguiente se quita la declaración de delegado del ejemplo anterior, que cumple la regla. Reemplaza su uso en los `ClassThatRaisesEvent` métodos y `ClassThatHandlesEvent` mediante el <xref:System.EventHandler%601?displayProperty=fullName> delegado.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: No anide tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Usar genéricos cuando sea necesario](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)