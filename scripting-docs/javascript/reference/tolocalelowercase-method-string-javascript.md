---
title: "toLocaleLowerCase (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase (método)"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# toLocaleLowerCase (M&#233;todo, String de JavaScript)
Convierte todos los caracteres alfabéticos a minúsculas, según la configuración regional actual del entorno host.  
  
## Sintaxis  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## Comentarios  
 La referencia obligatoria `stringVar` es un objeto `String` o un literal de cadena.  
  
 El método `toLocaleLowerCase` convierte los caracteres de una cadena teniendo en cuenta la configuración regional actual del entorno host.  En la mayoría de los casos, el resultado es el mismo que el resultado del método `toLowerCase`.  Los resultados difieren si las reglas de un lenguaje entran en conflicto con las asignaciones normales de minúsculas y mayúsculas de Unicode.  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [toLocaleUpperCase \(Método, String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase \(Método\)](../../javascript/reference/tolowercase-method-javascript.md)