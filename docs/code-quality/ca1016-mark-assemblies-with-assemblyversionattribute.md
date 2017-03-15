---
title: "CA1016: Marcar los ensamblados con AssemblyVersionAttribute | Microsoft Docs"
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
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016: Marcar los ensamblados con AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|Identificador de comprobación|CA1016|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 El ensamblado no tiene un número de versión.  
  
## Descripción de la regla  
 La identidad de un ensamblado está compuesta por la información siguiente:  
  
-   Nombre del ensamblado  
  
-   Número de versión  
  
-   Referencia cultural  
  
-   Clave pública \(para los ensamblados con nombre seguro\).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utiliza el número de versión para identificar de forma única un ensamblado y para enlazarse a los tipos de ensamblados con nombre seguro.  El número de versión se utiliza junto con la versión y la directiva del fabricante.  De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue un número de versión al ensamblado utilizando el atributo <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>.  Vea el ejemplo siguiente.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla si se trata de ensamblados usados por otros fabricantes o en un entorno de producción.  
  
## Ejemplo  
 El ejemplo siguiente muestra un ensamblado al que se le ha aplicado el atributo <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## Vea también  
 [Versiones de los ensamblados](../Topic/Assembly%20Versioning.md)   
 [Cómo: Crear una directiva de publicador](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)