---
title: "CA1014: Marcar los ensamblados con CLSCompliantAttribute | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014: Marcar los ensamblados con CLSCompliantAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|Identificador de comprobación|CA1014|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 No se ha aplicado el atributo <xref:System.CLSCompliantAttribute?displayProperty=fullName> a un ensamblado.  
  
## Descripción de la regla  
 La Common Language Specification \(CLS\) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación.  Los procedimientos de diseño dictan que todos los ensamblados indican explícitamente la conformidad con CLS con <xref:System.CLSCompliantAttribute>.  Si el atributo no está presente en un ensamblado, éste no es conforme.  
  
 Es posible que un ensamblado conforme a CLS contenga tipos o miembros de tipo que no sean conformes.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado.  En lugar de marcar todo el ensamblado como no conforme, debe determinar qué tipo o miembros de tipo no son conformes y marcar estos elementos como tales.  Si es posible, debe proporcionar una alternativa conforme a CLS para los miembros no conformes de forma que el mayor número de público posible pueda obtener acceso a toda la funcionalidad del ensamblado.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Si no desea que el ensamblado sea conforme, aplique el atributo y establezca su valor en `false`.  
  
## Ejemplo  
 El ejemplo siguiente muestra un ensamblado al que se le ha aplicado el atributo <xref:System.CLSCompliantAttribute?displayProperty=fullName> que lo declara como conforme a CLS.  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## Vea también  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)