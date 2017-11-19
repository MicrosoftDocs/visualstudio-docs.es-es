---
title: 'CA1408: No utilizar AutoDual ClassInterfaceType | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ffdbbfb8f28a6150888f3f127aa66ae82d31b4b8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 [Presentar la interfaz de clase](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)