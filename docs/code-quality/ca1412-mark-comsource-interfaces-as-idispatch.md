---
title: 'CA1412: Marcar las Interfaces ComSource como IDispatch | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8a53053588670fef616f4df7633b3a25fb45712
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Marcar las interfaces ComSource como IDispatch
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|Identificador de comprobación|CA1412|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo se marca con la <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributo y al menos una interfaz especificada no está marcado con el <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo establecido en el `InterfaceIsDispatch` valor.  
  
## <a name="rule-description"></a>Descripción de la regla  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>se usa para identificar las interfaces de eventos que una clase expone a los clientes del modelo de objetos componentes (COM). Estas interfaces se deben exponer como `InterfaceIsIDispatch` para permitir que los clientes COM de Visual Basic 6 recibir las notificaciones de eventos. De forma predeterminada, si una interfaz no está marcada con el <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo, se expone como una interfaz dual.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue o modifique la <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo para que su valor se establece en InterfaceIsIDispatch para todas las interfaces que se especifican con el <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una clase donde una de las interfaces infringe la regla.  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Generar eventos controlados por un receptor COM](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)