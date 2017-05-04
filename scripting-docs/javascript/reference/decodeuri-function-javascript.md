---
title: "decodeURI (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI (método)"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# decodeURI (Funci&#243;n de JavaScript)
Obtiene la versión sin codificar de un identificador uniforme de recursos \(URI\) codificado.  
  
## Sintaxis  
  
```  
decodeURI(URIstring)  
```  
  
## Comentarios  
 El argumento obligatorio `URIstring` es un valor que representa un URI codificado.  
  
 Usa la función `decodeURI` en lugar de la función desusada `unescape`.  
  
 La función `decodeURI` devuelve un valor alfanumérico.  
  
 Si `URIString` no es válido, se produce un URIError.  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Ejemplo  
 En el código siguiente primero se codifica un componente URI y después se descodifica.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [decodeURIComponent \(Función\)](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI \(Función\)](../../javascript/reference/encodeuri-function-javascript.md)   
 [Objeto Global](../../javascript/reference/global-object-javascript.md)