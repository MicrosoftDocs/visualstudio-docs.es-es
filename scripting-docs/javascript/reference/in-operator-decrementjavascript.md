---
title: "in (Operador de JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in (operador)"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# in (Operador de JavaScript)
Comprueba la existencia de una propiedad en un objeto.  
  
## Sintaxis  
  
```  
  
result = property in object  
```  
  
## Parámetros  
 `result`  
 Obligatorio.  Cualquier variable.  
  
 `property`  
 Obligatorio.  Expresión que se evalúa como una expresión de cadena.  
  
 `object`  
 Obligatorio.  Cualquier objeto.  
  
## Comentarios  
 El operador `in` determina si un objeto tiene una propiedad denominada `property`.  También determina si la propiedad es parte de la cadena de prototipo del objeto.  Para obtener más información sobre los prototipos de objeto, vea [Prototipos y herencia de prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar el operador `in`:  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)