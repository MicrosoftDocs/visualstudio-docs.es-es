---
title: "M&#233;todo startsWith (cadena) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# M&#233;todo startsWith (cadena) (JavaScript)
Devuelve un valor que indica si una cadena o subcadena empieza con otra cadena especificada.  
  
## Sintaxis  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### Parámetros  
 `stringObj`  
 Obligatorio.  Objeto de cadena con el que se va a buscar.  
  
 `str`  
 Obligatorio.  La cadena de búsqueda.  
  
 `position`  
 Opcional.  La posición del primer carácter con el que se va a buscar en el objeto de cadena, empezando por 0.  
  
## Valor devuelto  
 Si la cadena que empieza en `position` comienza con la cadena de búsqueda, el método `startsWith` devuelve `true`; en caso contrario, devuelve `false`.  
  
## Excepciones  
 Si `str` es `RegExp`, se produce `TypeError`.  
  
## Comentarios  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]