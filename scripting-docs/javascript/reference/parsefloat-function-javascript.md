---
title: "parseFloat (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat (método)"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# parseFloat (Funci&#243;n de JavaScript)
Convierte una cadena en un número de punto flotante.  
  
## Sintaxis  
  
```  
parseFloat(numString)   
```  
  
## Comentarios  
 El argumento obligatorio `numString` es una cadena que contiene un número de punto flotante.  
  
 La función `parseFloat` devuelve un valor numérico igual al número contenido en `numString`.  Si no se puede analizar correctamente ningún prefijo de `numString` en un número de punto flotante, se devuelve `NaN` \(no es un número\).  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Puedes comprobar si es `NaN` mediante la función `isNaN`.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vea también  
 [isNaN \(Función\)](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt \(Función\)](../../javascript/reference/parseint-function-javascript.md)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)