---
title: "El proyecto &#39;&lt;projectname1&gt;&#39; hace una referencia indirecta al proyecto &#39;&lt;projectname2&gt;&#39;, que contiene &#39;&lt;typename&gt;&#39; | Microsoft Docs"
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
  - "vbc31532"
  - "bc31532"
helpviewer_keywords: 
  - "BC31532"
ms.assetid: 9ef6574e-b049-4a2e-9b12-fea2dfe06cd1
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El proyecto &#39;&lt;projectname1&gt;&#39; hace una referencia indirecta al proyecto &#39;&lt;projectname2&gt;&#39;, que contiene &#39;&lt;typename&gt;&#39;
El proyecto '\<projectname1\>' hace una referencia indirecta al proyecto '\<projectname2\>', que contiene '\<typename\>'. Agregue una referencia de proyecto a '\<projectname2\>' a su proyecto.  
  
 El código del proyecto accede a un tipo definido en otro proyecto, pero el proyecto no tiene una referencia directa al proyecto que lo define.  
  
 El tipo puede ser una clase, una estructura, una interfaz, un módulo o una enumeración.  
  
 El proyecto que define el tipo mencionado genera un ensamblado que contiene el tipo. Si el proyecto no hace referencia directamente al proyecto que lo define, el compilador no puede garantizar que el ensamblado que contiene el tipo esté en la solución y disponible para el acceso.  
  
 **Id. de error:** BC31532  
  
### Para corregir este error  
  
-   Determine el proyecto que define el tipo mencionado y agréguele una referencia de proyecto.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Administrar referencias](http://msdn.microsoft.com/es-es/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimiento: Agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)