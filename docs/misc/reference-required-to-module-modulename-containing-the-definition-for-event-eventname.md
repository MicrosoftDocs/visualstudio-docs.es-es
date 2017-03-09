---
title: "Es necesaria una referencia al m&#243;dulo &#39;&lt;nombreDeM&#243;dulo&gt;&#39; que contiene la definici&#243;n del evento &#39;nombreDeEvento&#39; | Microsoft Docs"
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
  - "vbc30006"
  - "bc30006"
helpviewer_keywords: 
  - "BC30006"
ms.assetid: 7ab80acd-b47b-4920-bb15-6a3206b984e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es necesaria una referencia al m&#243;dulo &#39;&lt;nombreDeM&#243;dulo&gt;&#39; que contiene la definici&#243;n del evento &#39;nombreDeEvento&#39;
Es necesaria una referencia al módulo '\<`modulename`\>' que contiene la definición del evento '`eventname`'. Agregue una al proyecto.  
  
 El evento se define en un módulo al que no se hace referencia directamente en el proyecto. El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requiere una referencia para evitar la ambigüedad en caso de que el evento esté definido en más de un módulo.  
  
 **Identificador de error:** BC30006  
  
### Para corregir este error  
  
-   Incluya el nombre del módulo no referenciado en las referencias del proyecto.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)