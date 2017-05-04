---
title: "Directiva use strict | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "modo strict"
  - "directiva use strict"
  - "uso de strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Directiva use strict
Restringe el uso de algunas características en JavaScript.  Se admite en aplicaciones de Internet Explorer 10 y [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] solamente.  
  
## Sintaxis  
  
```javascript  
use strict  
```  
  
## Comentarios  
  
## Ejemplo  
 El código siguiente provoca un error de sintaxis porque en el modo strict todas las variables se deben declarar con `var`.  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## Vea también  
 [Modo strict](../../javascript/advanced/strict-mode-javascript.md)