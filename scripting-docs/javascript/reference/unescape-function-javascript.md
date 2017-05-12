---
title: "unescape (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape (método)"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# unescape (Funci&#243;n de JavaScript)
Descodifica objetos `String` codificados con la función `escape`.  Desusado.  
  
## Sintaxis  
  
```  
unescape(charString)   
```  
  
## Comentarios  
 El argumento obligatorio `charString` es un objeto o un literal `String` que se va a descodificar.  
  
 La función `unescape` devuelve un valor alfanumérico que almacena el contenido de `charstring`.  Todos los caracteres codificados con el formato hexadecimal %*xx* se reemplazan con sus equivalentes del juego de caracteres ASCII.  
  
 Los caracteres codificados con formato **%u** *xxxx* \(caracteres Unicode\) se reemplazan con caracteres Unicode con codificación hexadecimal *xxxx*.  
  
> [!NOTE]
>  No se debe usar la función `unescape` para descodificar identificadores uniformes de recursos \(URI\).  Usa las funciones `decodeURI` y `decodeURIComponent` en su lugar.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vea también  
 [decodeURI \(Función\)](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent \(Función\)](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape \(Función\)](../../javascript/reference/escape-function-javascript.md)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)