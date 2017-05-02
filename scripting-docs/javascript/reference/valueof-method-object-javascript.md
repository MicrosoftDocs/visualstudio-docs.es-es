---
title: "valueOf (M&#233;todo, Object de JavaScript) | Microsoft Docs"
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
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf (método)"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# valueOf (M&#233;todo, Object de JavaScript)
Devuelve el valor primitivo del objeto especificado.  
  
## Sintaxis  
  
```  
  
object.valueOf( )  
```  
  
## Comentarios  
 La referencia obligatoria `object` es cualquier objeto intrínseco de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 El método `valueOf` se define de forma diferente para cada objeto intrínseco de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
|Objeto|Valor devuelto|  
|------------|--------------------|  
|Array|Devuelve la instancia de la matriz.|  
|Boolean|Valor Boolean.|  
|Date|Valor de hora almacenado en milisegundos desde la medianoche del 1 de enero de 1970 UTC.|  
|Función|La propia función.|  
|Number|Valor numérico.|  
|Objeto|El propio objeto.  Es el valor predeterminado.|  
|Cadena|Valor alfanumérico.|  
  
 Los objetos **Math** y `Error` no tienen un método `valueOf`.  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Se aplica a**: [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)&#124; [Boolean \(Objeto\)](../../javascript/reference/boolean-object-javascript.md)&#124; [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)&#124; [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)&#124; [Number \(Objeto\)](../../javascript/reference/number-object-javascript.md)&#124; [Object \(Objeto\)](../../javascript/reference/object-object-javascript.md)&#124; [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [toString \(Método, Object\)](../../javascript/reference/tostring-method-object-javascript.md)