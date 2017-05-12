---
title: "prototype (Propiedad, String) | Microsoft Docs"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype (Propiedad, String)
Devuelve una referencia al prototipo correspondiente a una clase de cadena.  
  
## Sintaxis  
  
```  
  
string.prototype  
```  
  
## Comentarios  
 El argumento `string` es el nombre de una cadena.  
  
 Usa la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `String` que devuelve el valor del último elemento de la cadena, declara la función, agrégala a `String.prototype` y después úsala.  
  
```javascript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tienen una propiedad `prototype` que es de solo lectura.  Se pueden agregar propiedades y métodos al prototipo, pero no se puede asignar al objeto otro prototipo diferente.  No obstante, se puede asignar un nuevo prototipo a los objetos definidos por el usuario.  
  
 Las listas de métodos y propiedades de cada objeto intrínseco en esta referencia de lenguaje indican cuáles son parte del prototipo del objeto y cuáles no.  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]