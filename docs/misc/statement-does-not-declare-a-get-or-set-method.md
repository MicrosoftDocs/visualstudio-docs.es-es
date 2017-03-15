---
title: "La instrucci&#243;n no declara un m&#233;todo &#39;Get&#39; o &#39;Set&#39;. | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n no declara un m&#233;todo &#39;Get&#39; o &#39;Set&#39;.
La instrucción no proporciona correctamente una instrucción de declaración `Get` o `Set` alrededor de un procedimiento `Property`. Una propiedad se define como un bloque de código delimitado por las instrucciones `Property` y `End Property`. Dentro de este bloque, cada procedimiento `Property` aparece como un bloque interno encerrado entre una instrucción de declaración y una instrucción de finalización.  
  
 **Identificador de error:** BC30576  
  
### Para corregir este error  
  
-   Proporcione una instrucción de declaración `Get` o `Set`.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)