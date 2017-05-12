---
title: "Funci&#243;n Object.assign (objeto) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funci&#243;n Object.assign (objeto) (JavaScript)
Copia los valores de uno o varios objetos de origen en un objeto de destino.  
  
## Sintaxis  
  
```  
Object.assign(target, ...sources );  
```  
  
#### Parámetros  
 `target`  
 Obligatorio.  Objeto en el que se copian las propiedades enumerables.  
  
 `...sources`  
 Obligatorio.  Uno o varios objetos de los que se copian las propiedades enumerables.  
  
## Excepciones  
 Esta función genera un `TypeError` si se produce un error de asignación, que finaliza la operación de copia.  Se producirá un `TypeError` si una propiedad de destino no se puede escribir.  
  
## Comentarios  
 Esta función devuelve el objeto de destino.  Solo se copian las propiedades *enumerable own* del objeto de origen al objeto de destino.  Puede usar esta función para combinar o clonar objetos.  
  
 Los orígenes `null` o `undefined` se tratan como objetos vacíos y no aportan nada al objeto de destino.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo combinar un objeto mediante `Object.assign`.  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo clonar un objeto mediante `Object.assign`.  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]