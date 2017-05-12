---
title: "Number (Objeto de JavaScript) | Microsoft Docs"
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
  - "Number_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number (objeto)"
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Number (Objeto de JavaScript)
Objeto que representa un número de cualquier tipo.  Todos los números de JavaScript son números de punto flotante de 64 bits.  
  
## Sintaxis  
  
```  
  
numObj = new Number(value)  
```  
  
## Parámetros  
 `numObj`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto `Number`.  
  
 `value`  
 Obligatorio.  Valor numérico.  
  
## Comentarios  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] crea objetos `Number` cuando se establece una variable en un valor numérico, por ejemplo `var num = 255.336;`.  Rara vez es necesario crear objetos `Number` explícitamente.  
  
 El objeto `Number` tiene sus propios métodos y propiedades, además de los métodos y propiedades heredados de `Object`.  Los números se convierten en cadenas en determinadas circunstancias, por ejemplo, cuando un número se agrega o se concatena con una cadena, así como por medio del método `toString`.  Para obtener más información, consulte  [Operador de suma \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript tiene varias constantes numéricas.  Para obtener una lista completa, consulte [Constantes de número](../../javascript/reference/number-constants-javascript.md).  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Propiedades  
 En la tabla siguiente se enumeran las propiedades del objeto `Number` .  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[Propiedad constructor](../../javascript/reference/constructor-property-object-javascript.md)|Especifica la función que crea un objeto.|  
|[Propiedad prototype](../../javascript/reference/prototype-property-object-javascript.md)|Devuelve una referencia al prototipo para una clase de objetos.|  
  
## Funciones  
 En la tabla siguiente se enumeran las funciones del objeto `Number` .  
  
|Función|Descripción|  
|-------------|-----------------|  
|[Función Number.isFinite](../../javascript/reference/number-isfinite-function-number-javascript.md)|Devuelve un valor booleano que indica si un valor es finito.|  
|[Función Number.isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|Devuelve un valor booleano que indica si un valor es un entero.|  
|[Función Number.isNaN](../../javascript/reference/number-isnan-function-number-javascript.md)|Devuelve un valor booleano que indica si un valor es el valor reservado `NaN` \(no un número\).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Devuelve un valor booleano que indica si un valor puede representarse de forma segura en JavaScript.|  
  
## Métodos  
 En la tabla siguiente se enumeran los métodos del objeto `Number` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[hasOwnProperty \(Método\)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[isPrototypeOf \(Método\)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la jerarquía de prototipo de otro objeto.|  
|[propertyIsEnumerable \(Método\)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si es enumerable.|  
|[toExponential \(Método\)](../../javascript/reference/toexponential-method-number-javascript.md)|Devuelve una cadena que contiene un número representado en notación exponencial.|  
|[toFixed \(Método\)](../../javascript/reference/tofixed-method-number-javascript.md)|Devuelve una cadena que representa un número en notación de punto fijo.|  
|[toLocaleString \(Método\)](../../javascript/reference/tolocalestring-number.md)|Devuelve un objeto convertido en una cadena según la configuración regional actual.|  
|[Método toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Devuelve una cadena que contiene un número representado en notación exponencial o de punto fijo y que tiene un número de dígitos especificado.|  
|[toString \(Método\)](../../javascript/reference/tostring-method-object-javascript.md)|Devuelve una representación de cadena de un objeto.|  
|[valueOf \(Método\)](../../javascript/reference/valueof-method-object-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## Vea también  
 [Objetos de JavaScript](../../javascript/reference/javascript-objects.md)   
 [Math \(Objeto\)](../../javascript/reference/math-object-javascript.md)   
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)