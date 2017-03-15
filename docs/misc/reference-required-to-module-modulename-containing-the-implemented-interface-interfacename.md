---
title: "Es necesaria una referencia al m&#243;dulo &#39;&lt;nombreDeM&#243;dulo&gt;&#39; que contiene la interfaz implementada &#39;&lt;nombreDeInterfaz&gt;&#39; | Microsoft Docs"
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
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es necesaria una referencia al m&#243;dulo &#39;&lt;nombreDeM&#243;dulo&gt;&#39; que contiene la interfaz implementada &#39;&lt;nombreDeInterfaz&gt;&#39;
Es necesaria una referencia al módulo '\<nombreDeMódulo\>' que contiene la interfaz implementada '\<nombreDeInterfaz\>'. Agregue una al proyecto.  
  
 La interfaz está definida en un módulo al que no se hace referencia directamente en el proyecto. El compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] necesita una referencia para evitar la ambigüedad en caso de que la interfaz esté definida en más de un módulo.  
  
 **Identificador de error:** BC30010  
  
### Para corregir este error  
  
-   Incluya el nombre del módulo al que no se hace referencia en las referencias del proyecto.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)