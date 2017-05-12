---
title: "undefined (Constante de JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined (propiedad)"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# undefined (Constante de JavaScript)
Un valor que nunca se ha definido, como por ejemplo una variable que no se ha inicializado.  
  
## Sintaxis  
  
```  
undefined  
```  
  
## Comentarios  
 La constante `undefined` es un miembro del objeto `Global` y está disponible cuando se inicializa el motor de scripting.  Cuando se ha declarado una variable pero no se ha inicializado, su valor es **undefined**.  
  
 Si no se ha declarado una variable, no puedes compararla con `undefined`, pero puedes comparar su tipo con la cadena "undefined".  
  
 La constante `undefined` es útil para probar o establecer explícitamente una variable como no definida \(undefined\).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo utilizar la constante `undefined`.  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## Requisitos  
 La propiedad `undefined` se presentó por primera vez en [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)] y fue de solo lectura en [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vea también  
 [typeof \(Operador\)](../../javascript/reference/typeof-operator-decrementjavascript.md)