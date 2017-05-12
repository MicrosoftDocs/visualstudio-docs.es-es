---
title: "source (Propiedad, Regular Expression de JavaScript) | Microsoft Docs"
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
  - "source"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Source (propiedad)"
ms.assetid: d58ac57e-fcde-49d1-bbba-e8c4218448c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# source (Propiedad, Regular Expression de JavaScript)
Devuelve una copia del texto del patrón de expresión regular.  Es de solo lectura.  El argumento `rgExp` es un objeto **Regular expression**.  Puede ser un nombre de variable o un literal.  
  
## Sintaxis  
  
```  
  
rgExp.source  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad **source**:  
  
```javascript  
function SourceDemo(re, s){  
   var s1;  
   // Test string for existence of regular expression.  
   if (re.test(s))  
      s1 = " contains ";  
   else  
      s1 = " does not contain ";  
   // Get the text of the regular expression itself.  
   return(s + s1 + re.source);  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)