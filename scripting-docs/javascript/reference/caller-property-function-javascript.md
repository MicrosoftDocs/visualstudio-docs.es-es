---
title: "caller (Propiedad, Function de JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller (propiedad)"
  - "llamadas de función, funciones en ejecución"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# caller (Propiedad, Function de JavaScript)
Obtiene la función invocada por la función actual.  
  
## Sintaxis  
  
```  
  
functionName.caller  
```  
  
## Comentarios  
 El objeto `functionName` es el nombre de cualquier función que se está ejecutando.  
  
 La propiedad `caller` se define para una función solo mientras esa función se está ejecutando.  Si se llama a la función desde el nivel superior de un programa de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], `caller` contiene `null`.  
  
 Si la propiedad `caller` se usa en un contexto de cadena, el resultado es el mismo que `functionName`.`toString`; es decir, se muestra el texto descompilado de la función.  
  
 En el ejemplo siguiente se muestra el uso de la propiedad `caller`:  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [function \(Instrucción\)](../../javascript/reference/function-statement-javascript.md)