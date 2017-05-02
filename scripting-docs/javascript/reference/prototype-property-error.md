---
title: "prototype (Propiedad, Error) | Microsoft Docs"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype (Propiedad, Error)
Devuelve una referencia al prototipo para un error.  
  
## Sintaxis  
  
```  
  
error.prototype  
```  
  
## Comentarios  
 El argumento `error` es el nombre de un error.  
  
 Usa la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a un error.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Error` que devuelve el valor del elemento mayor de la matriz, declara la función, agrégala a `Error.prototype` y después úsala.  
  
```javascript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tienen una propiedad `prototype` que es de solo lectura.  Se pueden agregar propiedades y métodos al prototipo, pero no se puede asignar al objeto otro prototipo diferente.  No obstante, se puede asignar un nuevo prototipo a los objetos definidos por el usuario.  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]