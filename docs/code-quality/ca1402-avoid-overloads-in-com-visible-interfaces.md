---
title: 'CA1402: Evite sobrecargas en interfaces visibles para COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e4360ff6c6355827a77d165c9a4975ffa8bdc89a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549016"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Evite sobrecargas en interfaces visibles para COM

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|Identificador de comprobación|CA1402|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un modelo de objetos componentes (COM) visible interfaz declara los métodos sobrecargados.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre. Las sobrecargas subsiguientes reciben un nombre único al anexar al nombre de un carácter de subrayado "_" y un entero que corresponde al orden de declaración de la sobrecarga. Por ejemplo, considere los siguientes métodos:

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

Estos métodos se exponen a los clientes COM de la forma siguiente.

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Los clientes COM de Visual Basic 6 no pueden implementar métodos de interfaz mediante el uso de un carácter de subrayado en el nombre.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre de los métodos sobrecargados para que los nombres sean únicos. Como alternativa, hacer que la interfaz sea invisible para COM cambiando la accesibilidad a `internal` (`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o aplicando el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo establecido en `false`.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una interfaz que infringe la regla y una interfaz que cumple la regla.

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)
- [Long (tipo de datos)](/dotnet/visual-basic/language-reference/data-types/long-data-type)