---
title: "encodeURI (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI (método)"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURI (Funci&#243;n de JavaScript)
Codifica una cadena de texto como identificador de recursos uniforme \(URI\) válido.  
  
## Sintaxis  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## Comentarios  
 El argumento obligatorio `URIString` es un valor que representa un URI codificado.  
  
 La función `encodeURI` devuelve un URI codificado.  Si pasas el resultado a `decodeURI`, se devuelve la cadena original.  La función `encodeURI` no codifica los siguientes caracteres: ":", "\/", ";" y "?".  Usa el método `encodeURIComponent` para codificar estos caracteres.  
  
## Ejemplo  
 El código siguiente codifica y descodifica un URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [decodeURI \(Función\)](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent \(Función\)](../../javascript/reference/decodeuricomponent-function-javascript.md)