---
title: "Map (Objeto, JavaScript) | Microsoft Docs"
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
  - "Map"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Map (Objeto, JavaScript)
Colección de pares clave\-valor.  
  
## Sintaxis  
  
```javascript  
mapObj = new Map()  
```  
  
## Comentarios  
 Los valores y claves de la colección pueden ser de cualquier tipo.  Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Map`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[Constructor](../../javascript/reference/constructor-property-map.md)|Especifica la función que crea un mapa.|  
|[prototipo](../../javascript/reference/prototype-property-map.md)|Devuelve una referencia al prototipo para un mapa.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Devuelve el número de elementos de un mapa.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Map`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Quita todos los elementos de un mapa.|  
|[eliminar](../../javascript/reference/delete-method-map-javascript.md)|Quita un elemento especificado de un mapa.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Realiza la acción especificada para cada elemento de un mapa.|  
|[obtener](../../javascript/reference/get-method-map-javascript.md)|Devuelve un elemento especificado de un mapa.|  
|[tiene](../../javascript/reference/has-method-map-javascript.md)|Devuelve el objeto `true` si el mapa contiene un elemento especificado.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Agrega un nuevo elemento a una asignación.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Devuelve una representación de cadena de un mapa.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Map` y después recuperarlos.  
  
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