---
title: "constructor (Propiedad, Object de JavaScript) | Microsoft Docs"
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
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor (propiedad)"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# constructor (Propiedad, Object de JavaScript)
Especifica la función que crea un objeto.  
  
## Sintaxis  
  
```  
  
object.constructor  
```  
  
## Comentarios  
 El parámetro obligatorio `object` es el nombre de un objeto o una función.  
  
 La propiedad `constructor` es un miembro del prototipo de todo objeto que tiene un prototipo.  Esto incluye todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] excepto los objetos `Global` y `Math`.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [prototype \(Propiedad, Object\)](../../javascript/reference/prototype-property-object-javascript.md)