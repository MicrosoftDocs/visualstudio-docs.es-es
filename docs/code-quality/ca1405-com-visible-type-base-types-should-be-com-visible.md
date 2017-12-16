---
title: 'CA1405: Los tipos base de tipos visibles COM deben ser visibles para COM | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cceaee755af5269e266ca57e3644213e939c0ead
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Los tipos base de tipos visibles para COM deben ser visibles para COM
|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|Identificador de comprobación|CA1405|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Depende de la corrección|  
  
## <a name="cause"></a>Motivo  
 Un tipo visible del modelo de objetos componentes (COM) que se deriva de un tipo que no es visible para COM.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando un tipo visible COM agrega miembros en una nueva versión, debe cumplir una serie de instrucciones estrictas para evitar que los clientes COM que se enlazan a la versión actual. Un tipo que no es visible para COM, se da por supuesto que no tiene que seguir estas reglas de control de versiones de COM cuando agrega nuevos miembros. Sin embargo, si un visibles para COM tipo deriva del tipo no visible COM y expone una interfaz de clase de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (valor predeterminado), todos los miembros públicos del tipo base (a menos que se marque específicamente como COM invisibles, lo que sería redundante) se expone a COM. Si el tipo base agrega a nuevos miembros en una versión posterior, pueden provocar errores en los clientes COM que se enlazan a la interfaz de clase del tipo derivado. Tipos visibles para COM deben derivar únicamente de tipos visibles para COM para reducir la posibilidad de que los clientes COM.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, hacer que los tipos base visibles para COM o el tipo derivado COM sea invisible.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)