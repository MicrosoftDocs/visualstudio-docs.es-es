---
title: "El proyecto &#39;&lt;nombreProyecto&gt;&#39; necesita una referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n1&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39;, pero hace referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n2&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39; (error de Visual Basic). | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32209"
  - "bc32209"
helpviewer_keywords: 
  - "BC32209"
ms.assetid: fe50736b-444f-4e40-8f80-9760ff13a153
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El proyecto &#39;&lt;nombreProyecto&gt;&#39; necesita una referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n1&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39;, pero hace referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n2&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39; (error de Visual Basic).
Un proyecto hace una referencia indirecta a un ensamblado que se define en otra parte, pero el proyecto también tiene una referencia directa a una versión posterior de ese ensamblado.  
  
 Si el compilador permite que el código use la referencia indirecta, puede que no tenga acceso a tipos y elementos de programación definidos en la versión más reciente, pero no en la versión anterior.  
  
 **Identificador de error:** BC32209  
  
### Para corregir este error  
  
-   Elimine la referencia indirecta a la versión anterior del ensamblado y use la referencia directa a la versión más reciente.  
  
## Vea también  
 [Ensamblados en Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NIB: Administrar referencias](http://msdn.microsoft.com/es-es/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB Cómo: Agregar o quitar referencias con el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)