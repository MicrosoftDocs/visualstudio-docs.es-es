---
title: 'CA1408: no usar AutoDual ClassInterfaceType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b953a97d557e28cce50f554acc03797d4be38220
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534880"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: No utilizar AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|Identificador de comprobación|CA1408|
|Category|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo visible del modelo de objetos componentes (COM) se marca con el <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo establecido en el `AutoDual` valor de <xref:System.Runtime.InteropServices.ClassInterfaceType> .

## <a name="rule-description"></a>Descripción de la regla
 Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto. Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz. De forma predeterminada, si <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> no se especifica el atributo, se usa una interfaz de solo envío.

 A menos que se marque lo contrario, todos los tipos públicos no genéricos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el valor del <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo por el `None` valor de <xref:System.Runtime.InteropServices.ClassInterfaceType> y defina explícitamente la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que esté seguro de que el diseño del tipo y sus tipos base no cambiarán en una versión futura.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase que infringe la regla y una nueva declaración de la clase para usar una interfaz explícita.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1403: Los tipos de diseño automático no deben ser visibles a través de COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Consulte también
 [Introducción a la interfaz de clase para la](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [certificación de tipos de .net para](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) la [interoperabilidad con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
