---
title: "join (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join (método)"
  - "concatenación de cadenas, método join"
  - "matrices [Visual Studio], unión"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# join (M&#233;todo, Array de JavaScript)
Agrega todos los elementos de una matriz separados por la cadena separadora especificada.  
  
## Sintaxis  
  
```  
  
arrayObj.join([separator])   
```  
  
## Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto `Array`.  
  
 `separator`  
 Opcional.  Cadena que se utiliza para separar un elemento de una matriz del siguiente, en el objeto `String` resultante.  Si se omite, los elementos de la matriz se separarán mediante comas.  
  
## Comentarios  
 Si alguno de los elementos de la matriz es **undefined** o `null`, se tratará como una cadena vacía.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso del método **join**.  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)