---
title: "encodeURIComponent (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent (método)"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURIComponent (Funci&#243;n de JavaScript)
Codifica una cadena de texto como un componente válido de un identificador uniforme de recursos \(URI\).  
  
## Sintaxis  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## Comentarios  
 El argumento obligatorio `encodedURIString` es un valor que representa un componente de URI codificado.  
  
 La función `encodeURIComponent` devuelve un URI codificado.  Si pasas el resultado a `decodeURIComponent`, se devuelve la cadena original.  Como la función `encodeURIComponent` codifica todos los caracteres, ten cuidado si la cadena representa una ruta de acceso como \/carpeta1\/carpeta2\/predeterminado.html.  Los caracteres de barra diagonal se codificarán y no serán válidos si se envían como solicitud a un servidor web.  Usa la función `encodeURI` si la cadena contiene más de un único componente de URI.  
  
## Ejemplo  
 En el código siguiente primero se codifica un componente URI y después se descodifica.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [decodeURI \(Función\)](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent \(Función\)](../../javascript/reference/decodeuricomponent-function-javascript.md)