---
title: "reverse (M&#233;todo de JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "matrices [Visual Studio], invertir elementos"
  - "reverse (método)"
  - "transponer elementos"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# reverse (M&#233;todo de JavaScript)
Invierte los elementos en un objeto `Array`.  
  
## Sintaxis  
  
```  
  
arrayObj.reverse()   
```  
  
## Parámetros  
 `arrayObj`  
 Requerido.  Cualquier objeto `Array`.  
  
## Valor devuelto  
 Matriz invertida.  
  
## Comentarios  
 La referencia `arrayObj` obligatoria es un objeto `Array`.  
  
 El método `reverse` invierte los elementos de un objeto `Array` en contexto.  No se crea un nuevo objeto `Array` durante la ejecución.  
  
 Si la matriz no es contigua, el método `reverse` crea elementos en la matriz que rellenan los espacios vacíos que hay en ella.  Cada uno de estos elementos creados tiene el valor `undefined`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `reverse`.  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [concat \(Método, Array\)](../../javascript/reference/concat-method-array-javascript.md)