---
title: "toLocaleUpperCase (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase (método)"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# toLocaleUpperCase (M&#233;todo, String de JavaScript)
Devuelve una cadena donde todos los caracteres alfabéticos se han convertido a mayúsculas, según la configuración regional actual del entorno host.  
  
## Sintaxis  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## Comentarios  
 La referencia obligatoria `stringVar` es un objeto `String` o un literal de cadena.  
  
 El método `toLocaleUpperCase` convierte los caracteres de una cadena teniendo en cuenta la configuración regional actual del entorno host.  En la mayoría de los casos, el resultado es el mismo que el resultado del método `toUpperCase`.  Los resultados difieren si las reglas de un lenguaje entran en conflicto con las asignaciones normales de minúsculas y mayúsculas de Unicode.  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [toLocaleLowerCase \(Método, String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase \(Método, String\)](../../javascript/reference/touppercase-method-string-javascript.md)