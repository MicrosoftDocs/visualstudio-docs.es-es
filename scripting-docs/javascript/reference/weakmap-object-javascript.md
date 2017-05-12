---
title: "WeakMap (Objeto, JavaScript) | Microsoft Docs"
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
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WeakMap (Objeto, JavaScript)
Una colección de pares clave\-valor donde cada clave es una referencia de objeto.  
  
## Sintaxis  
  
```  
weakmapObj = new WeakMap()  
```  
  
## Comentarios  
 No se puede enumerar un objeto `WeakMap`.  
  
 Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
 En un objeto de `WeakMap`, las referencias a los objetos de clave se retienen “débilmente”.  Esto significa que `WeakMap` no evitará que una recolección de elementos no utilizados se produzca en los objetos clave.  Cuando no hay referencias \(distintas de `WeakMap`\) a los objetos clave, el recolector de elementos no utilizados puede obtener los objetos clave.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `WeakMap`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[Constructor](../../javascript/reference/constructor-property-weakmap.md)|Especifica la función que crea un `WeakMap`.|  
|[prototipo](../../javascript/reference/prototype-property-weakmap.md)|Devuelve una referencia al prototipo para un `WeakMap`.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `WeakMap`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Quita todos los elementos de una colección `WeakMap`.|  
|[eliminar](../../javascript/reference/delete-method-weakmap-javascript.md)|Quita un elemento especificado de un `WeakMap`.|  
|[obtener](../../javascript/reference/get-method-weakmap-javascript.md)|Devuelve un elemento especificado de un `WeakMap`.|  
|[tiene](../../javascript/reference/has-method-weakmap-javascript.md)|Devuelve el objeto `true` si el `WeakMap` contiene un elemento especificado.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Agrega un nuevo elemento `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Devuelve una representación de cadena de un `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un objeto `WeakMap` y después recuperarlos.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]