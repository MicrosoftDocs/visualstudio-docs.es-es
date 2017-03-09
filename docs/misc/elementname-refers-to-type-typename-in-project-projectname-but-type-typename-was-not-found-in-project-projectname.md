---
title: "&#39;&lt;nombreDeElemento&gt;&#39; hace referencia al tipo &#39;&lt;nombreDeTipo&gt;&#39; en el proyecto &#39;&lt;nombreDeProyecto&gt;&#39;, pero el tipo &#39;&lt;nombreDeTipo&gt;&#39; no se encontr&#243; en el proyecto &#39;&lt;nombreDeProyecto&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeElemento&gt;&#39; hace referencia al tipo &#39;&lt;nombreDeTipo&gt;&#39; en el proyecto &#39;&lt;nombreDeProyecto&gt;&#39;, pero el tipo &#39;&lt;nombreDeTipo&gt;&#39; no se encontr&#243; en el proyecto &#39;&lt;nombreDeProyecto&gt;&#39;
Una expresión accede a una clase, estructura o interfaz, o a un módulo contemplados en otro proyecto, pero ese proyecto no contiene el tipo especificado.  
  
 Este error se produce cuando el proyecto hace una referencia indirecta a otro proyecto en la misma solución. Normalmente, el proyecto hace referencia a un ensamblado que hace referencia al otro proyecto. Si el ensamblado accede al tipo especificado en el otro proyecto, se establece la referencia indirecta al tipo. Sin embargo, si el tipo no está presente en el otro proyecto, se genera este error.  
  
 **Identificador de error:** BC30960  
  
### Para corregir este error  
  
-   Si el tipo citado ya no está definido en ninguna parte, quite o reemplace la instrucción que intenta acceder a este. Es posible que también debas realizar el mismo cambio en el ensamblado que proporciona la referencia indirecta al tipo citado.  
  
-   Si el tipo citado está definido en alguna parte, cree una referencia directa al proyecto o al ensamblado que lo define.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NIB: Administrar referencias](http://msdn.microsoft.com/es-es/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)