---
title: "for...in (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "instrucciones de iteración, for...in (instrucción)"
  - "estructuras de bucle, for...in (instrucciones)"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# for...in (Instrucci&#243;n de JavaScript)
Ejecuta una o más instrucciones para cada propiedad de un objeto o cada elemento de una matriz.  
  
## Sintaxis  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## Parámetros  
 `variable`  
 Obligatorio.  Variable que puede ser cualquier nombre de propiedad de `object` o cualquier índice del elemento de un objeto `array`.  
  
 `object`, `array`  
 Opcional.  Objeto o matriz en el que se realiza la iteración.  
  
 `statements`  
 Opcional.  Una o varias instrucciones que se ejecutarán para cada propiedad de `object` o cada elemento de `array`.  Puede ser una instrucción compuesta.  
  
## Comentarios  
 Al principio de cada iteración de un bucle, el valor de `variable` es el nombre de propiedad siguiente de `object` o el índice de elemento siguiente de `array`.  Después, puedes usar `variable` en cualquiera de las instrucciones del bucle para hacer referencia a la propiedad de `object` o al elemento de `array`.  
  
 Las propiedades de un objeto no se asignan de una manera determinada.  No puedes especificar una propiedad determinada por su índice, solamente por su nombre.  
  
 La iteración en una matriz se realiza en el orden de sus elementos, es decir, 0, 1, 2.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la instrucción `for...in` con un objeto que se utiliza como matriz asociativa.  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## Ejemplo  
 En este ejemplo se muestra el uso de la instrucción `for ... in` para recorrer en iteración un objeto `Array` que tiene propiedades expando.  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Usa el objeto `Enumerator` para recorrer en iteración los miembros de una colección.  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [for \(Instrucción\)](../../javascript/reference/for-statement-javascript.md)   
 [while \(Instrucción\)](../../javascript/reference/while-statement-javascript.md)