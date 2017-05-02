---
title: "forEach (M&#233;todo, Map de JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# forEach (M&#233;todo, Map de JavaScript)
Realiza la acción especificada para cada elemento de un mapa.  
  
## Sintaxis  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### Parámetros  
 `mapObj`  
 Requerido.  Un objeto `Map`.  
  
 `callbackfn`  
 Requerido.  La función a la que llama `forEach` una vez por cada elemento del mapa.  `callbackfn` acepta hasta tres argumentos.  `forEach` llama a la función `callbackfn` una vez para cada elemento del mapa.  
  
 `thisArg`  
 Opcional.  Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`.  Si se omite `thisArg`, se usa `undefined` como valor de `this`.  
  
## Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## Comentarios  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Puede declarar la función de devolución de llamada usando hasta tres parámetros, como se muestra en la tabla siguiente.  
  
|Argumento de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`value`|Un valor contenido en la asignación.|  
|`key`|Clave contenida en la asignación.|  
|`mapObj`|El objeto `Map` para atravesar.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar miembros de `Map` mediante `forEach`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]