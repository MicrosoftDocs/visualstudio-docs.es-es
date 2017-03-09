---
title: "La instrucci&#243;n no puede aparecer dentro del cuerpo de un evento. | Microsoft Docs"
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
  - "bc31112"
  - "vbc31112"
helpviewer_keywords: 
  - "BC31112"
ms.assetid: fd51fc53-a008-4b79-85fb-2d9fa1fb5a79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n no puede aparecer dentro del cuerpo de un evento.
La instrucción no puede aparecer dentro del cuerpo de un evento. Se supone el final del evento.  
  
 Una instrucción que no es válida dentro de un cuerpo de evento aparece dentro de uno.  
  
 **Identificador de error:** BC31112  
  
### Para corregir este error  
  
-   Agregue `End Event` antes de la instrucción.  
  
## Vea también  
 [Application Events Sample](http://msdn.microsoft.com/es-es/289a787f-b97e-43c8-a304-fe95e45f4a0d)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)