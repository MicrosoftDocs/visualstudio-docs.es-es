---
title: "toGMTString (M&#233;todo, Date de JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString (método)"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toGMTString (M&#233;todo, Date de JavaScript)
Devuelve una fecha convertida en cadena usando la hora del meridiano de Greenwich \(GMT\).  
  
## Sintaxis  
  
```  
  
dateObj.toGMTString()   
```  
  
## Comentarios  
 La referencia obligatoria `dateObj` es cualquier objeto `Date`.  
  
 El método `toGMTString` está obsoleto y solo se proporciona por compatibilidad con versiones anteriores.  Se recomienda que uses el método `toUTCString` en su lugar.  
  
 El método `toGMTString` devuelve un objeto `String` que contiene la fecha con el formato propio de la convención GMT.  El formato del valor devuelto es el siguiente: "5 de enero de 1996 00:00:00 GMT".  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [toUTCString \(Método, Date\)](../../javascript/reference/toutcstring-method-date-javascript.md)