---
title: "M&#233;todo repeat (cadena) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo repeat (cadena) (JavaScript)
Devuelve un nuevo objeto de cadena con un valor igual a la cadena original repetido el número de veces especificado.  
  
## Sintaxis  
  
```  
stringObj.repeat(count);  
```  
  
#### Parámetros  
 `stringObj`  
 Obligatorio.  Objeto de cadena.  
  
 `count`  
 Obligatorio.  Número de veces que se repetirá la cadena original en la cadena devuelta.  
  
## Excepciones  
 Este método produce un RangeError solo si el argumento es negativo o \+Infinity.  
  
## Comentarios  
 El método `repeat` concatena la cadena original con la nueva cadena el número de veces especificado por `count`.  
  
 Este método produce un error si `count` no es un número positivo menor que `Infinity`.  
  
## Ejemplo  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]