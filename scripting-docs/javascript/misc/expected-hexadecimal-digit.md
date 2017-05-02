---
title: "Se esperaba un d&#237;gito hexadecimal | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Se esperaba un d&#237;gito hexadecimal
Has creado una secuencia de escape incorrecta de Unicode.  Las secuencias de escape Unicode comienzan con \\u, seguido exactamente de cuatro dígitos hexadecimales \(ni más ni menos\).  Los dígitos hexadecimales Unicode solo pueden contener los números de 0 a 9, las letras mayúsculas A\-F y las letras minúsculas a\-f.  En el ejemplo siguiente se muestra una secuencia de escape Unicode con un formato correcto.  
  
```javascript  
z = "\u1A5F";  
```  
  
### Para corregir este error  
  
-   Asegúrate de que los dígitos hexadecimales Unicode comienzan con \\u, contienen solo los números 0\-9, las letras mayúsculas A\-F y las letras minúsculas a\-f, y están agrupados en cuatro dígitos.  
  
    > [!NOTE]
    >  Si deseas usar el texto literal \\u en una cadena, usa dos barras diagonales inversas \(\(\\\\u\): una como secuencia de escape para la primera barra diagonal inversa.  
  
## Vea también  
 [Tipos de datos](../../javascript/data-types-javascript.md)