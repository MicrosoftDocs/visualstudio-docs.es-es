---
title: "toString (M&#233;todo, Boolean) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString (M&#233;todo, Boolean)
Devuelve una representación alfanumérica de un objeto.  
  
## Sintaxis  
  
```  
  
boolean.toString()  
```  
  
## Parámetros  
 `boolean`  
 Obligatorio.  Objeto para el que se va a obtener una representación de cadena.  
  
## Valor devuelto  
 Si el valor Boolean es `true`, devuelve "true".  De lo contrario, devuelve "false".  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **toString**.  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]