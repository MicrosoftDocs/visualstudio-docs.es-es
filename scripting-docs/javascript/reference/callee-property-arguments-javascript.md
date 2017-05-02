---
title: "callee (Propiedad, arguments de JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee (propiedad)"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# callee (Propiedad, arguments de JavaScript)
Devuelve el objeto `Function` que se está ejecutando; es decir, el texto del cuerpo del objeto `Function` especificado.  
  
## Sintaxis  
  
```  
[function.]arguments.callee  
```  
  
## Comentarios  
 El argumento opcional *function* es el nombre del objeto `Function` que se está ejecutando actualmente.  
  
 La propiedad `callee` es miembro del objeto **arguments** que solo está disponible durante la ejecución de la función asociada.  
  
 El valor inicial de la propiedad `callee` es el objeto `Function` que se está ejecutando.  Esto permite que las funciones anónimas sean recursivas.  
  
## Ejemplo  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [arguments \(Objeto\)](../../javascript/reference/arguments-object-javascript.md)&#124; [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)  
  
## Vea también  
 [caller \(Propiedad, Function\)](../../javascript/reference/caller-property-function-javascript.md)