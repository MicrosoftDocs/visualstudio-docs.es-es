---
title: "Objeto WeakSet (JavaScript) | Microsoft Docs"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Objeto WeakSet (JavaScript)
Una colección de objetos únicos de cualquier tipo.  
  
## Sintaxis  
  
```  
setObj = new WeakSet()  
```  
  
## Comentarios  
 Si intenta agregar un objeto que no sea único a un `WeakSet`, el nuevo objeto no se agregará a la colección.  
  
 Al contrario que sucede con un `Set`, solo se pueden agregar objetos a la colección.  No se pueden agregar valores arbitrarios a la colección.  
  
 En un objeto `WeakSet` las referencias a objetos en el conjunto se conservan “débilmente”.  Esto significa que `WeakSet` no impedirá que se produzca una recolección de elementos no utilizados en los objetos.  Cuando no hay referencias \(salvo `WeakSet`\) a los objetos, el recolector de elementos no utilizados puede recopilar los objetos.  
  
 `WeakSet` \(o `WeakMap`\) puede ser útil en algunos escenarios que impliquen el almacenamiento en caché de objetos o metadatos de objetos.  Por ejemplo, los metadatos de los objetos no extensibles pueden almacenarse en un `WeakSet` o puede crear una memoria caché de imágenes de usuario mediante `WeakSet`.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `WeakSet`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|constructor|Especifica la función que crea un conjunto.|  
|prototipo|Devuelve una referencia al prototipo para un conjunto.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `WeakSet`.  
  
|Método|Descripción|  
|------------|-----------------|  
|agregar|Agrega un elemento a un conjunto.|  
|eliminar|Elimina el elemento especificado de un conjunto.|  
|has|Devuelve `true` si el conjunto contiene un elemento especificado.|  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo agregar miembros a un conjunto y, a continuación, verificar que se hayan agregado.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]