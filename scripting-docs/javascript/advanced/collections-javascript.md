---
title: "Colecciones (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Colecciones (JavaScript)
Puede utilizar los objetos de colección [Map](../../javascript/reference/map-object-javascript.md), [Set](../../javascript/reference/set-object-javascript.md) y [WeakMap](../../javascript/reference/weakmap-object-javascript.md) para almacenar valores y objetos.  Estos objetos proporcionan los métodos adecuados para agregar y recuperar miembros mediante una clave o un valor en lugar de un índice.  Para tener acceso a los miembros de una colección mediante un índice, utilice un objeto `Array`.  Para obtener más información, vea [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  `Map`, `Set` y `WeakMap` no se admiten en las versiones del explorador anteriores a Internet Explorer 11.  Para obtener más información acerca de la compatibilidad de versiones, vea [Información de versiones](../../javascript/reference/javascript-version-information.md).  
  
## Usar colecciones  
 Los objetos `Map` y `WeakMap` almacenan pares de clave\-valor y permiten agregar, recuperar y quitar miembros mediante la clave.  La clave y el valor pueden ser de cualquier tipo.  El objeto `Set` almacena valores de cualquier tipo.  
  
 Los objetos `Map` y `Set` permiten enumerar los miembros de la colección utilizando el método `forEach` y comprobar el tamaño de la colección utilizando el método `size`.  El objeto `WeakMap`, en cambio, no es enumerable.  Para esta colección, las referencias de clave se conservan débilmente.  Utilice `WeakMap` si desea que el recolector de elementos no utilizados determine si la aplicación tiene que conservar cada miembro de la colección en memoria.  Por ejemplo, esto puede ser útil para escenarios de memoria caché en los que los objetos almacenados en caché sean muy grandes y no desee conservarlos en memoria innecesariamente.  En algunos escenarios, puede utilizar este objeto para evitar pérdidas de memoria.  
  
 En el ejemplo siguiente se muestra cómo usar el objeto `Map`:  En este ejemplo, se tiene acceso a los miembros mediante `get` y `forEach`.  La función de devolución de llamada de `forEach` puede tomar hasta tres parámetros, que proporcionan el valor del elemento actual de la colección, la clave del elemento actual y el propio objeto de la colección.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 El uso de `WeakMap` es similar al de `Map`, con la salvedad de que puede recuperar miembros usando solamente `get`.  Para obtener un ejemplo, vea el objeto [WeakMap](../../javascript/reference/weakmap-object-javascript.md).  
  
 En el ejemplo siguiente se muestra cómo usar el objeto `Set`:  En este ejemplo, la función de devolución de llamada toma un parámetro, que es el valor del elemento actual de la colección.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Vea también  
 [JavaScript avanzado](../../javascript/advanced/advanced-javascript.md)