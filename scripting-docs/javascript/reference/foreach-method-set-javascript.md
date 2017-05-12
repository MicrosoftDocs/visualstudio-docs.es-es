---
title: "forEach (M&#233;todo, Set de JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# forEach (M&#233;todo, Set de JavaScript)
Realiza la acción especificada para cada elemento de un conjunto.  
  
## Sintaxis  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### Parámetros  
 `setObj`  
 Requerido.  Un objeto `Set`.  
  
 `callbackfn`  
 Requerido.  `callbackfn` acepta hasta tres argumentos.  La función a la que llama `forEach` una vez por cada elemento del conjunto.  
  
 `thisArg`  
 Opcional.  Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`.  Si se omite `thisArg`, se usa `undefined` como valor de `this`.  
  
## Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## Comentarios  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, key, setObj)`  
  
 Puede declarar la función de devolución de llamada usando hasta tres parámetros, como se muestra en la tabla siguiente.  
  
|Argumento de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`value`|Un valor contenido en el conjunto.|  
|`key`|Un valor contenido en el conjunto.  Un conjunto no tiene claves, por tanto, este valor es igual que `value`.|  
|`setObj`|El objeto `Set` para atravesar.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar `forEach`.  El argumento `callbackfn` incluye el código de la función de devolución de llamada.  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra que también puede recuperar miembros de un conjunto pasando solo un único parámetro a la función de devolución de llamada.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]