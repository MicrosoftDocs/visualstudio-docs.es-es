---
title: "decodeURIComponent (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent (método)"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# decodeURIComponent (Funci&#243;n de JavaScript)
Obtiene la versión sin codificar de un componente codificado de un identificador uniforme de recursos \(URI\).  
  
## Sintaxis  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## Comentarios  
 El argumento obligatorio `encodedURIString` es un valor que representa un componente de URI codificado.  
  
 Un componente de URI forma parte de un URI completo.  
  
 Si `encodedURIString` no es válido, se produce un URIError.  
  
## Ejemplo  
 El código siguiente codifica y descodifica un URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [decodeURI \(Función\)](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI \(Función\)](../../javascript/reference/encodeuri-function-javascript.md)