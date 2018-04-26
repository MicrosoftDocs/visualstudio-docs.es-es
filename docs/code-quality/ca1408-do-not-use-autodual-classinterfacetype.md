---
title: 'CA1408: No utilizar AutoDual ClassInterfaceType'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f324eee1ae71f063ddd19d5a7f3d82af6f45c00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: No utilizar AutoDual ClassInterfaceType
|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|Identificador de comprobación|CA1408|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible del modelo de objetos componentes (COM) se marca con la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo establecido en el `AutoDual` valo <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto. Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz. De forma predeterminada, si la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo no se especifica, se utiliza una interfaz solo de envío.

 A menos que marque lo contrario, todos los tipos no genéricos públicos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el valor de la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribuir a la `None` valo <xref:System.Runtime.InteropServices.ClassInterfaceType> y definir explícitamente la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla a menos que se tiene la certeza de que el diseño del tipo y sus tipos base no van a cambiar en una versión futura.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase que infringe la regla y una nueva declaración de la clase se debe utilizar una interfaz explícita.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1403: Los tipos de diseño automático no deben ser visibles para COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Vea también
 [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interoperar con código no administrado](/dotnet/framework/interop/index)