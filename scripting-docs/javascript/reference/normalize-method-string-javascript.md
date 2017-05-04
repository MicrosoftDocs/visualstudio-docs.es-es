---
title: "M&#233;todo normalize (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# M&#233;todo normalize (String) (JavaScript)
Devuelve la forma de normalización Unicode de una cadena especificada.  
  
## Sintaxis  
  
```  
stringObj.normalize([form]);  
```  
  
#### Parámetros  
 `stringObj`  
 Requerido.  El objeto de cadena con el que se contrasta.  
  
 `form`  
 Opcional.  El valor de forma de normalización Unicode.  
  
## Valor devuelto  
 La forma de normalización Unicode de una cadena especificada.  
  
## Excepciones  
 Si `form` es un valor no admitido, se produce un `RangeError`.  
  
## Comentarios  
 Si `stringObj` no es una cadena, se convertirá en una cadena antes de que el método intente devolver la forma de normalización Unicode de la cadena.  
  
 `form` debe ser un valor de forma de normalización Unicode, "NFC", "NFD", "NFKC" o "NFKD", correspondiente a los valores especificados para el [Anexo del estándar Unicode \#15](http://www.unicode.org/reports/tr15/).  El valor predeterminado de `form` es “NFC”.  
  
## Ejemplo  
 En los siguientes ejemplos de código se muestra el uso del método `normalize`.  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]