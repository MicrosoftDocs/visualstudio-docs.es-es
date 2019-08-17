---
title: 'CA1000: No declarar miembros estáticos en tipos genéricos'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f10433330642ee06dd7f705cdd8e35333cd8a79d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547915"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: No declarar miembros estáticos en tipos genéricos

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|Identificador de comprobación|CA1000|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un tipo genérico contiene un `static` miembro`Shared` (en Visual Basic).

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Cuando se `static` llama a un miembro de un tipo genérico, se debe especificar el argumento de tipo para el tipo. Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro. La sintaxis para especificar el argumento de tipo en estos dos casos es diferente y se confunde fácilmente, como se muestra en las siguientes llamadas:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

Por lo general, se deben evitar las dos declaraciones anteriores para que no sea necesario especificar el argumento de tipo cuando se llama al miembro. Esto da como resultado una sintaxis para llamar a miembros en genéricos que no son diferentes de la sintaxis de los elementos no genéricos. Para obtener más información, [vea CA1004: Los métodos genéricos deben proporcionar](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)un parámetro de tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el miembro estático o cámbielo por un miembro de instancia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Proporcionar genéricos en una sintaxis que sea fácil de entender y usar reduce el tiempo necesario para aprender y aumentar la tasa de adopción de nuevas bibliotecas.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: No anide tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Usar genéricos cuando sea necesario](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)