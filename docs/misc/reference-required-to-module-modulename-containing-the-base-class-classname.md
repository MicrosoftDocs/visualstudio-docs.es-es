---
title: "Referencia necesaria para el m&#243;dulo &#39;&lt;nombreDeM&#243;dulo&gt;&#39; que contiene la clase base &#39;&lt;nombreDeClase&gt;&#39; | Microsoft Docs"
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
  - "vbc30008"
  - "bc30008"
helpviewer_keywords: 
  - "BC30008"
ms.assetid: ec8de475-8a8b-4aa5-86c9-6fcc44dcec06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Referencia necesaria para el m&#243;dulo &#39;&lt;nombreDeM&#243;dulo&gt;&#39; que contiene la clase base &#39;&lt;nombreDeClase&gt;&#39;
Referencia necesaria para el módulo '\<nombreDeMódulo\>' que contiene la clase base '\<nombreDeClase\>'. Agregue una al proyecto.  
  
 La clase se define en un módulo al que no se hace referencia directamente en el proyecto. El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requiere una referencia para evitar la ambigüedad en caso de que la clase esté definida en más de un módulo.  
  
 **Identificador de error:** BC30008  
  
### Para corregir este error  
  
-   Incluya el nombre del módulo no referenciado en las referencias del proyecto.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)