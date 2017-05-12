---
title: "input (Propiedad) ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_ (propiedad)"
  - "input (propiedad)"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# input (Propiedad) ($_) (RegExp) (JavaScript)
Devuelve la cadena con la que se realizó la búsqueda de una expresión regular.  Es de solo lectura.  
  
## Sintaxis  
  
```  
  
RegExp.input  
```  
  
## Comentarios  
 El objeto asociado con esta propiedad siempre es el objeto `RegExp` global.  
  
 El valor de la propiedad **input** se modifica cada vez que se cambia la cadena buscada.  
  
 En el ejemplo siguiente se muestra el uso de la propiedad **input**:  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)  
  
## Vea también  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)