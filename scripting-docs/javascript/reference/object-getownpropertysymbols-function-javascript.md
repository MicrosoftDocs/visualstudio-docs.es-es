---
title: "Funci&#243;n Object.getOwnPropertySymbols (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funci&#243;n Object.getOwnPropertySymbols (JavaScript)
Devuelve las propiedades de símbolos propios de un objeto.  Las propiedades de símbolos propios de un objeto son aquellas que se definen directamente en ese objeto y que no se heredan del prototipo del objeto.  
  
## Sintaxis  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto que contiene los símbolos propios.  
  
## Valor devuelto  
 Matriz que contiene los símbolos propios del objeto.  
  
## Comentarios  
 Deberá usar `Object.getOwnPropertySymbols` para obtener las propiedades de símbolo de un objeto.  `Object.getOwnPropertyNames` no devolverá las propiedades de símbolo.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo obtener las propiedades de símbolo de un objeto.  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]