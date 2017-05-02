---
title: "this (Instrucci&#243;n de JavaScript) | Microsoft Docs"
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
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructores, hacer referencia al objeto actual"
  - "this (instrucción)"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# this (Instrucci&#243;n de JavaScript)
Hace referencia al objeto actual.  
  
## Sintaxis  
  
```  
this.property  
```  
  
## Comentarios  
 El argumento `property` obligatorio es una de las propiedades del objeto actual.  
  
 La palabra clave `this` se puede utilizar generalmente en constructores de objetos para hacer referencia al objeto actual.  
  
## Ejemplo  
 En el ejemplo siguiente, la palabra **this** hace referencia al objeto Car recién creado y asigna valores a tres de sus propiedades:  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 La palabra clave **this** suele hacer referencia al objeto **window** si se usa fuera del ámbito de cualquier otro objeto.  Sin embargo, dentro de los controladores de eventos `this` hace referencia al elemento DOM que provocó el evento.  
  
 En el código siguiente \(para Internet Explorer 9 o posterior\), el controlador de eventos imprime la versión de cadena de un botón que tiene un identificador de "clicker".  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Utilizar el método bind](../../javascript/advanced/using-the-bind-method-javascript.md)