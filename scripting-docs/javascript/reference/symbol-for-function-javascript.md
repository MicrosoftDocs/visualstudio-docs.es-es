---
title: "Funci&#243;n Math.floor (JavaScript) | Microsoft Docs"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funci&#243;n Math.floor (JavaScript)
Devuelve el símbolo de una clave especificada o, si la clave no está presente, crea un nuevo objeto de símbolo con la nueva clave.  
  
## Sintaxis  
  
```vb  
Symbol.for(key);  
```  
  
#### Parámetros  
 `key`  
 Requerido.  La clave del símbolo, que también se utiliza como la descripción.  
  
## Comentarios  
 Este método busca el símbolo en el registro de símbolos globales.  Si serializa símbolos como cadenas, utilice el registro de símbolos globales para asegurarse de que se asigne una cadena concreta al símbolo correcto para todas las búsquedas.  
  
## Ejemplo  
  
```javascript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]