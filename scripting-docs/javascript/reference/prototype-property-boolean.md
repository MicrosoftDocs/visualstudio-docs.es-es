---
title: "prototype (Propiedad, Boolean) | Microsoft Docs"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype (Propiedad, Boolean)
Devuelve una referencia al prototipo para un booleano.  
  
## Sintaxis  
  
```  
  
boolean.prototype  
```  
  
## Comentarios  
 El argumento de `boolean` es el nombre de un objeto.  
  
 La propiedad `prototype` proporciona un conjunto básico de funcionalidades a una clase de objetos.  Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  Es posible agregar propiedades y métodos al prototipo, pero los objetos integrados no se pueden asignar a otro prototipo.  
  
 Por ejemplo, para agregar un método al objeto `Boolean` que devuelva el valor del elemento más grande de la matriz, declare la función, agréguela a `Boolean.prototype` y después úsela.  
  
```javascript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]