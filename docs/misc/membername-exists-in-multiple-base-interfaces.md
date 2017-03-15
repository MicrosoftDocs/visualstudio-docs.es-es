---
title: "&#39;&lt;nombreDeMiembro&gt;&#39; existe en varias interfaces base | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeMiembro&gt;&#39; existe en varias interfaces base
'\<nombreDeMiembro\>' existe en varias interfaces base. Use el nombre de la interfaz que declara '\<nombreDeMiembro\>' en la cláusula 'Implements' en lugar del nombre de la interfaz derivada.  
  
 Esta interfaz hereda miembros con el mismo nombre de varias interfaces, lo que da lugar a ambigüedades.  
  
 **Identificador de error:** BC31040  
  
### Para corregir este error  
  
-   Use el nombre de interfaz definitorio en las cláusulas `Implements` en lugar del nombre de la interfaz derivada.  
  
## Vea también  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)