---
title: "CA1017: Marcar los ensamblados con ComVisibleAttribute | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017: Marcar los ensamblados con ComVisibleAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|Identificador de comprobación|CA1017|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 No se ha aplicado el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> a un ensamblado.  
  
## Descripción de la regla  
 El atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> determina cómo obtienen acceso los clientes COM al código administrado.  Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM.  La visibilidad COM se puede establecer para un ensamblado completo y, a continuación, se puede invalidar para los tipos individuales y los miembros de tipo.  Si el atributo no está presente, el contenido del ensamblado es visible para los clientes COM.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado.  Si no desea que el ensamblado sea visible a los clientes COM, aplique el atributo y establezca su valor en `false`.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Si desea que el ensamblado sea visible, aplique el atributo y establezca su valor en `true`.  
  
## Ejemplo  
 El ejemplo siguiente muestra un ensamblado al que se le ha aplicado el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> para evitar que los clientes COM sean visibles.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## Vea también  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)