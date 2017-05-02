---
title: "isFinite (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "isFinite"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "números finitos"
  - "isFinite (método)"
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# isFinite (Funci&#243;n de JavaScript)
Determina si un número proporcionado es finito.  
  
## Sintaxis  
  
```  
isFinite(number)   
```  
  
## Comentarios  
 El argumento obligatorio `number` es cualquier valor numérico.  
  
 La función `isFinite` devuelve `true` si `number` es cualquier valor distinto de `NaN`, infinito negativo o infinito positivo.  En estos tres casos, devuelve **false**.  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vea también  
 [isNaN \(Función\)](../../javascript/reference/isnan-function-javascript.md)