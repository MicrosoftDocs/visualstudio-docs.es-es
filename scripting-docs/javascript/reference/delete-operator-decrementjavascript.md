---
title: "delete (Operador de JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "elementos de matriz, eliminar"
  - "propiedades, eliminar"
  - "Operador delete"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# delete (Operador de JavaScript)
Elimina una propiedad de un objeto o quita un elemento de una matriz.  
  
## Sintaxis  
  
```  
delete expression  
```  
  
## Comentarios  
 El argumento `expression` es una expresión válida de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que normalmente produce un nombre de propiedad o un elemento de matriz.  
  
 Si el resultado de `expression` es un objeto, la propiedad especificada en `expression` existe y el objeto no permite su eliminación, se devuelve `false`.  
  
 En todos los demás casos, se devuelve `true`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo quitar un elemento de una matriz.  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo eliminar propiedades de un objeto.  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)