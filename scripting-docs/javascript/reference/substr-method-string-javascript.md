---
title: "substr (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr (método)"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# substr (M&#233;todo, String de JavaScript)
Obtiene una subcadena que comienza en la ubicación especificada y tiene la longitud especificada.  
  
## Sintaxis  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## Parámetros  
 `stringvar`  
 Obligatorio.  Literal de cadena u objeto `String` del que se extrae la subcadena.  
  
 `start`  
 Obligatorio.  Posición inicial de la subcadena deseada.  El índice del primer carácter de la cadena es cero.  
  
 `length`  
 Opcional.  Número de caracteres que se va a incluir en la subcadena devuelta.  
  
## Comentarios  
 Si `length` es cero o es negativo, se devuelve una cadena vacía.  Si no se especifica, la subcadena continúa hasta el final de `stringvar`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `substr`.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [substring \(Método, String\)](../../javascript/reference/substring-method-string-javascript.md)