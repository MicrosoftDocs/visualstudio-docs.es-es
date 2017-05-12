---
title: "trim (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "trim (método)"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# trim (M&#233;todo, String de JavaScript)
Quita los caracteres de espacio en blanco y de terminador de línea iniciales y finales de una cadena.  
  
## Sintaxis  
  
```  
  
stringObj.trim()  
```  
  
## Parámetros  
 `stringObj`  
 Obligatorio.  Objeto `String` o literal de cadena.  El método `trim` no modifica esta cadena.  
  
## Valor devuelto  
 Cadena original a la que se han quitado los caracteres de espacio en blanco y de terminador de línea iniciales y finales.  
  
## Comentarios  
 Entre los caracteres que se quitan se incluyen: espacio, tabulador, avance de página, retorno de carro y salto de línea.  Vea [Caracteres especiales](../../javascript/advanced/special-characters-javascript.md) para obtener una lista completa de caracteres de espacio en blanco y de terminador de línea.  
  
 Para obtener un ejemplo que muestre cómo implementar su propio método Trim, vea [Prototipos y herencia de prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `trim`.  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Caracteres especiales](../../javascript/advanced/special-characters-javascript.md)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)   
 [Aplicación de ejemplo de desplazamiento, movimiento panorámico y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)