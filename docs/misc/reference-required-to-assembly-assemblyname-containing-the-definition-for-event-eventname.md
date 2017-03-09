---
title: "Es necesaria una referencia al ensamblado &#39;&lt;nombreDeEnsamblado&gt;&#39; que contiene la definici&#243;n del evento &#39;nombreDeEvento&#39; | Microsoft Docs"
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
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es necesaria una referencia al ensamblado &#39;&lt;nombreDeEnsamblado&gt;&#39; que contiene la definici&#243;n del evento &#39;nombreDeEvento&#39;
Es necesaria una referencia al ensamblado '\<`assemblyname`\>' que contiene la definición del evento '\<`eventname`\>'. Agregue una referencia al proyecto.  
  
 El evento está definido en una biblioteca de vínculos dinámicos \(DLL\) o un ensamblado al que no se hace referencia directamente en el proyecto. El compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] necesita una referencia para evitar la ambigüedad en caso de que el evento esté definido en más de una DLL o un ensamblado.  
  
 **Identificador de error:** BC30005  
  
### Para corregir este error  
  
-   Incluya el nombre de la DLL o el ensamblado no referenciados en las referencias del proyecto.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)