---
title: "No se puede enviar el informe de errores autom&#225;ticamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede enviar el informe de errores autom&#225;ticamente
No se puede enviar el informe de errores automáticamente. Visite 'http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039' para establecer la configuración de envío de informes de errores.  
  
 Especificó la opción del compilador `/errorreport:send`, pero el equipo no está configurado para enviar informes de errores automáticamente. No se enviará ninguna información sobre los errores internos del compilador de Visual Basic.  
  
 **Identificador de error:** BC2027  
  
### Para corregir este error  
  
-   Quite la opción del compilador `/errorreport:send` o reemplácela por `/errorreport:queue`, `/errorreport:prompt` o `/errorreport:none`.  
  
     O bien  
  
-   Habilite la elaboración automática de informes de errores siguiendo las instrucciones de [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039).  
  
## Vea también  
 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)   
 [http:\/\/go.Microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)