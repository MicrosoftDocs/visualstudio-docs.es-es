---
title: "Function (Objeto de JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function (objeto)"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Function (Objeto de JavaScript)
Crea una nueva función.  
  
## Sintaxis  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## Sintaxis  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## Parámetros  
 `functionName`  
 Obligatorio.  Nombre de la función recién creada.  
  
 `argname1...argnameN`  
 Opcional.  Lista de argumentos que la función acepta.  
  
 `body`  
 Opcional.  Cadena que contiene el bloque de código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que se ejecutará cuando se llame a la función.  
  
## Comentarios  
 La función es un tipo de datos básico de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  La sintaxis 1 crea un valor de función que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convierte en un objeto `Function` cuando es necesario.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convierte los objetos `Function` creados por la sintaxis 2 en valores de función cuando se llama a la función.  
  
 La sintaxis 1 es la manera estándar de crear nuevas funciones en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  La sintaxis 2 es un formato alternativo usado para crear objetos de función explícitamente.  
  
 Por ejemplo, si vas a declarar una función que agrega los dos argumentos que se le pasan, puedes hacerlo de dos maneras:  
  
## Ejemplo 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## Ejemplo 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 En cualquier caso, llama a la función con una línea de código similar a la siguiente:  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  Cuando llames a una función, asegúrate de incluir siempre los paréntesis y los argumentos necesarios.  La llamada a una función sin paréntesis hace que se devuelva la propia función, en lugar del valor devuelto de la misma.  
  
## Propiedades  
 [0...  
          n \(Propiedades\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[arguments \(Propiedad\)](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee \(Propiedad\)](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller \(Propiedad\)](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor \(Propiedad\)](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length \(Propiedad, función\)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype \(Propiedad\)](../../javascript/reference/prototype-property-object-javascript.md)  
  
## Métodos  
 [apply \(Método\)](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind \(Método\)](../../javascript/reference/bind-method-function-javascript.md) &#124; [call \(Método\)](../../javascript/reference/call-method-function-javascript.md) &#124; [toString \(Método\)](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf \(Método\)](../../javascript/reference/valueof-method-object-javascript.md)  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [function \(Instrucción\)](../../javascript/reference/function-statement-javascript.md)   
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var \(Instrucción\)](../../javascript/reference/var-statement-javascript.md)