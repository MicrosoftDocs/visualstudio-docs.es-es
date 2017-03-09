---
title: "CA1403: Los tipos de dise&#241;o autom&#225;tico no deben ser visibles para COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403: Los tipos de dise&#241;o autom&#225;tico no deben ser visibles para COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|Identificador de comprobación|CA1403|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo de valor visible para el Modelo de objetos componentes \(COM\) está marcado con el atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> establecido en <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## Descripción de la regla  
 Common Language Runtime administra los tipos de diseño <xref:System.Runtime.InteropServices.LayoutKind>.  El diseño de estos tipos puede cambiar de una versión a otra de .NET Framework, lo que interrumpirá a los clientes COM que esperan un diseño concreto.  Tenga en cuenta que si no se especifica el atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute>, los compiladores de C\#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y C\+\+ especifican el diseño <xref:System.Runtime.InteropServices.LayoutKind> para los tipos de valor.  
  
 A menos que se marque lo contrario, todos los tipos públicos no genéricos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM.  Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad del tipo para COM se establezca explícitamente; el ensamblado que contiene se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se tiene que marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el valor del atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> a <xref:System.Runtime.InteropServices.LayoutKind> o <xref:System.Runtime.InteropServices.LayoutKind>, o bien haga el tipo invisible para COM.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo que infringe la regla y otro que la cumple.  
  
 [!code-cs[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## Reglas relacionadas  
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Vea también  
 [Introducing the Class Interface](http://msdn.microsoft.com/es-es/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)