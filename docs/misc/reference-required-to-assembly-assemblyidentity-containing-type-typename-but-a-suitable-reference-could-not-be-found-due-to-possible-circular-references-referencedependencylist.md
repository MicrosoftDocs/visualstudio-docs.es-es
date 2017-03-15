---
title: "Es necesaria una referencia al ensamblado &#39;&lt;assemblyidentity&gt;&#39; que contiene el tipo &#39;&lt;typename&gt;&#39;, pero no se pudo encontrar una referencia adecuada debido a posibles problemas de referencias circulares: &lt;referencedependencylist&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30962"
  - "vbc30962"
helpviewer_keywords: 
  - "BC30962"
ms.assetid: 6f338158-bfb4-4cc0-bbf7-1111c708613c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es necesaria una referencia al ensamblado &#39;&lt;assemblyidentity&gt;&#39; que contiene el tipo &#39;&lt;typename&gt;&#39;, pero no se pudo encontrar una referencia adecuada debido a posibles problemas de referencias circulares: &lt;referencedependencylist&gt;
Una expresión usa un tipo como, por ejemplo, una clase, estructura, interfaz, enumeración o delegado, que se define fuera del proyecto. Sin embargo, la referencia de proyecto a dicho ensamblado forma parte de un conjunto de referencias circulares.  
  
 Cuando varios proyectos tienen referencias entre sí, las referencias pueden ser *circulares*. Por ejemplo, dos proyectos pueden tener referencias entre sí. De manera más general, una cadena de referencias de un proyecto al siguiente puede volver, en última instancia, al proyecto inicial. En tales casos, no hay ningún proyecto final al final de la cadena con la que se va a resolver la referencia.  
  
 Para obtener acceso a un tipo definido en otro ensamblado, el compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] debe tener una referencia a dicho ensamblado. Debe ser una referencia única y no ambigua, que no produzca referencias circulares entre proyectos.  
  
 **Identificador de error:** BC30962  
  
### Para corregir este error  
  
-   En las propiedades del proyecto, agregue una referencia directa al proyecto que produce el ensamblado que define el tipo que está usando.  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimiento: agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimiento: modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)