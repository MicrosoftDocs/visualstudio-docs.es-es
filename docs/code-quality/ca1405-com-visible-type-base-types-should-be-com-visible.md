---
title: "CA1405: Los tipos base de tipos visibles para COM deben ser visibles para COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405: Los tipos base de tipos visibles para COM deben ser visibles para COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|Identificador de comprobación|CA1405|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Depende de la corrección|  
  
## Motivo  
 Un tipo visible para el Modelo de objetos componentes \(COM\) deriva de un tipo que no es visible para COM.  
  
## Descripción de la regla  
 Cuando un tipo visible a través de COM agrega miembros en una nueva versión, debe cumplir una serie de instrucciones estrictas a fin de evitar la interrupción de los clientes COM enlazados a la versión actual.  Un tipo que es no visible a través de COM da por hecho que no necesita cumplir estas reglas de administración de versiones de COM al agregar nuevos miembros.  Sin embargo, si un tipo visible a través de COM se deriva del tipo no visible a través de COM y expone una interfaz de clases de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> \(valor predeterminado\), todos los miembros públicos del tipo base \(a no ser que estén marcados de manera específica como del tipo no visible a través de COM, lo que sería redundante\) están expuestos a COM.  Si el tipo base agrega nuevos miembros en una versión subsiguiente, todos los clientes COM que se enlacen a la interfaz de clases del tipo derivado podrían interrumpirse.  Los tipos visibles a través de COM se deben derivar únicamente de tipos visibles a través de COM para reducir la posibilidad de interrumpir los clientes COM.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, haga que los tipos base sean visibles a través de COM o que el tipo derivado sea no visible a través de COM.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## Vea también  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/es-es/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)