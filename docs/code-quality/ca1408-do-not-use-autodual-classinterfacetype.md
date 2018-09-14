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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a4baa4f12a3d4cb113dd99f1cd3e158742c1ed1a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545611"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: No utilizar AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|Identificador de comprobación|CA1408|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible del modelo de objetos componentes (COM) se marca con el <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo establecido en el `AutoDual` valor <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto. Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz. De forma predeterminada, si la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo no se especifica, se usa una interfaz solo de envío.

 A menos que marque en caso contrario, todos los tipos genéricos públicos son visibles para COM; todos los tipos genéricos y no públicos no están visibles para COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el valor de la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo a la `None` valor de <xref:System.Runtime.InteropServices.ClassInterfaceType> y definir explícitamente la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima una advertencia de esta regla a menos que se tiene la certeza de que el diseño del tipo y sus tipos base no cambiará en una versión futura.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una clase que infringe la regla y una nueva declaración de la clase para usar una interfaz explícita.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1403: Los tipos de diseño automático no deben ser visibles para COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Vea también

- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)