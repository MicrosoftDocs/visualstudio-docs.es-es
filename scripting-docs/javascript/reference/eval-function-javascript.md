---
title: "eval (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval (función)"
  - "análisis, código"
  - "analizador"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# eval (Funci&#243;n de JavaScript)
Evalúa código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y lo ejecuta.  
  
## Sintaxis  
  
```  
eval(codeString)   
```  
  
## Parámetros  
 `codeString`  
 Obligatorio.  Valor `String` que contiene código válido de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Comentarios  
 La función `eval` habilita la ejecución dinámica de código fuente de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Cadena `codeString` analizada por el analizador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y ejecutada.  
  
 El código pasado a la función `eval` se ejecuta en el mismo contexto que la llamada a la función `eval`.  
  
 Siempre que sea posible, usa [JSON.parse \(Función\)](../../javascript/reference/json-parse-function-javascript.md) para deserializar el texto de la notación de objetos JavaScript \(JSON\).  La función `JSON.parse` es más segura y se ejecuta más rápidamente que la función `eval`.  
  
## Ejemplo  
 En el código siguiente se inicializa la variable `myDate` en una fecha de prueba.  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vea también  
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)