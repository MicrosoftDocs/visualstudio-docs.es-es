---
title: "instanceof (Operador de JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf (operador)"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# instanceof (Operador de JavaScript)
Devuelve un valor booleano que indica si un objeto es instancia de una clase concreta.  
  
## Sintaxis  
  
```  
  
result = object instanceof class  
```  
  
## Parámetros  
 `result`  
 Requerido.  Cualquier variable.  
  
 `object`  
 Requerido.  Cualquier expresión de objeto.  
  
 `class`  
 Requerido.  Cualquier clase de objeto definida.  
  
## Comentarios  
 El operador `instanceof` devuelve `true` si `object` es una instancia de `class`.  Devuelve `true` si `class` está presente en la cadena del prototipo del objeto.  Devuelve `false` si `object` no es una instancia de `class` o si `object` es `null`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar el operador `instanceof`.  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)