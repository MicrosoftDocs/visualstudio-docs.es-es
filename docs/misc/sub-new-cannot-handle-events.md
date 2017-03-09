---
title: "&#39;Sub New&#39; no puede administrar eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; no puede administrar eventos
Intentó combinar `Sub New` con `Handles`, que no es válido. Utilice la palabra clave `Handles` al final de una declaración de procedimiento para que controle los eventos generados por una variable de objeto declarada mediante el uso de la palabra clave `WithEvents`.  
  
 **Identificador de error:** BC30497  
  
### Para corregir este error  
  
1.  No use `New` en este contexto.  
  
## Vea también  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)