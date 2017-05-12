---
title: "La longitud de la matriz debe ser un entero positivo finito | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# La longitud de la matriz debe ser un entero positivo finito
Has llamado al constructor **Array** con un argumento que no es un número entero \(los números enteros constan de cero más el conjunto de enteros positivos\).  
  
### Para corregir este error  
  
-   Usa enteros positivos solo cuando crees un nuevo objeto `Array`.  Si quieres crear una matriz con un solo elemento que no es un entero, hazlo con un proceso de dos pasos.  Primero, crea una matriz con un elemento. Después, coloca el valor en el primer elemento \(array\[0\]\).  A continuación se muestra un ejemplo que genera este error.  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     En el ejemplo siguiente se muestra la forma correcta de especificar una matriz con un solo elemento numérico.  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     No hay límite superior para el tamaño de una matriz, salvo el valor entero máximo \(aproximadamente cuatro mil millones\).  
  
## Vea también  
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)