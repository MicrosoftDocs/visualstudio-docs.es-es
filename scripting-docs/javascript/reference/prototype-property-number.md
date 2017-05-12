---
title: "prototype (Propiedad, Number) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype (Propiedad, Number)
Devuelve una referencia al prototipo correspondiente a una clase de número.  
  
## Sintaxis  
  
```  
  
number.prototype  
```  
  
## Comentarios  
 El argumento `number` es el nombre de un número.  
  
 Usa la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Number` que devuelve el número de dígitos \(enteros\), declara la función, agrégala a `Number.prototype` y después úsala.  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tienen una propiedad `prototype` que es de solo lectura.  Se pueden agregar propiedades y métodos al prototipo, pero no se puede asignar al objeto otro prototipo diferente.  No obstante, se puede asignar un nuevo prototipo a los objetos definidos por el usuario.  
  
 Las listas de métodos y propiedades de cada objeto intrínseco en esta referencia de lenguaje indican cuáles son parte del prototipo del objeto y cuáles no.  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]