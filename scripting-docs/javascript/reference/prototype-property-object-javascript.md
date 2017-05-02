---
title: "prototype (Propiedad, Object de JavaScript) | Microsoft Docs"
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
  - "Prototype"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "herencia, objetos"
  - "Prototype (propiedad)"
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# prototype (Propiedad, Object de JavaScript)
Devuelve una referencia al prototipo correspondiente a una clase de objetos.  
  
## Sintaxis  
  
```  
  
objectName.prototype  
```  
  
## Comentarios  
 El argumento `objectName` es el nombre de un objeto.  
  
 Usa la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Array` que devuelve el valor del elemento mayor de la matriz, declara la función, agrégala a `Array.prototype` y después úsala.  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 Todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tienen una propiedad `prototype` que es de solo lectura.  Se pueden agregar propiedades y métodos al prototipo, pero no se puede asignar al objeto otro prototipo diferente.  No obstante, se puede asignar un nuevo prototipo a los objetos definidos por el usuario.  
  
 Las listas de métodos y propiedades de cada objeto intrínseco en esta referencia de lenguaje indican cuáles son parte del prototipo del objeto y cuáles no.  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [constructor \(Propiedad, Object\)](../../javascript/reference/constructor-property-object-javascript.md)