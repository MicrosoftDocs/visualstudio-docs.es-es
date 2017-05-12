---
title: "escape (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "codificar objetos de cadena"
  - "Escape (método)"
  - "Hexadecimal"
  - "String (objeto), codificación"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# escape (Funci&#243;n de JavaScript)
Codifica cadenas para que se puedan leer en todos los equipos.  Desusado.  
  
## Sintaxis  
  
```  
escape(charString)   
```  
  
## Comentarios  
 El argumento obligatorio `charString` es cualquier objeto o literal `String` que se va a codificar.  
  
 La función **escape** devuelve un valor alfanumérico \(en formato Unicode\) que almacena el contenido de `charstring`.  Todos los espacios, signos de puntuación, caracteres acentuados y caracteres no ASCII se reemplazan con la codificación `%`*xx*, donde *xx* equivale al número hexadecimal que representa el carácter.  Por ejemplo, un espacio se devuelve como "%20".  
  
 Los caracteres con un valor mayor que 255 se almacenan mediante el formato **%u** *xxxx*.  
  
> [!NOTE]
>  No se debe usar la función **escape** para codificar identificadores uniformes de recursos \(URI\).  Usa las funciones `encodeURI` y `encodeURIComponent` en su lugar.  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [encodeURI \(Función\)](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent \(Función\)](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)   
 [unescape \(Función\)](../../javascript/reference/unescape-function-javascript.md)