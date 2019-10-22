---
title: 'CA1412: marcar las interfaces comSource como IDispatch | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652728"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Marcar las interfaces ComSource como IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|Identificador de comprobación|CA1412|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo se marca con el atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> y al menos una interfaz especificada no está marcada con el atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> establecido en el valor `InterfaceIsDispatch`.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> se utiliza para identificar las interfaces de eventos que una clase expone a los clientes del modelo de objetos componentes (COM). Estas interfaces deben exponerse como `InterfaceIsIDispatch` para permitir que los clientes de Visual Basic 6 COM reciban notificaciones de eventos. De forma predeterminada, si una interfaz no está marcada con el atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, se expone como una interfaz dual.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue o modifique el atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> de modo que su valor se establezca en InterfaceIsIDispatch para todas las interfaces que se especifican con el atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase en la que una de las interfaces infringe la regla.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vea también
 [Cómo: generar eventos controlados por un receptor com](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [interoperando con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
