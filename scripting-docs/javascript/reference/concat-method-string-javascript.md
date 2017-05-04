---
title: "concat (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat (método, String)"
  - "Concat (método)"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# concat (M&#233;todo, String de JavaScript)
Devuelve una cadena que contiene la concatenación de dos o más cadenas.  
  
## Sintaxis  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## Parámetros  
 `string1`  
 Obligatorio.  Objeto `String` o literal de cadena con que se concatenan todas las demás cadenas especificadas.  
  
 `string2,. . ., stringN`  
 Opcional.  Las cadenas que se van a anexar al final de `string1`.  
  
## Comentarios  
 El resultado del método `concat` es equivalente a: `result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`.  Un cambio de valor en una cadena de origen o de resultado no afecta al valor de la otra cadena.  Si alguno de los argumentos no es una cadena, se convertirá en cadena antes de concatenarse con `string1`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `concat` cuando se usa con una cadena:  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [Operador de suma \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)