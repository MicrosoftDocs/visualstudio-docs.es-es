---
title: "M&#233;todo fill (matriz) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# M&#233;todo fill (matriz) (JavaScript)
Rellena una matriz con un valor especificado.  
  
## Sintaxis  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto de matriz.  
  
 `value`  
 Obligatorio.  Valor usado para rellenar la matriz.  
  
 `start`  
 Opcional.  Índice inicial usado para rellenar los valores de la matriz.  El valor predeterminado es 0.  
  
 `end`  
 Opcional.  Índice final usado para rellenar los valores de la matriz.  El valor predeterminado es la propiedad length del objeto `this`.  
  
## Comentarios  
 Si `start` es negativo, `start` se trata como `length`\+`start`, donde `length` es la longitud de la matriz.  Si `end` es negativo, `end` se trata como `length`\+`end`.  
  
## Ejemplo  
 Los ejemplos de código siguientes rellenan una matriz con valores.  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]