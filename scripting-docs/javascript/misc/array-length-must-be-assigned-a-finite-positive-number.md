---
title: "A la longitud de la matriz se le debe asignar un n&#250;mero positivo finito | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# A la longitud de la matriz se le debe asignar un n&#250;mero positivo finito
Al definir la propiedad **length** de un objeto **Array** existente, especificaste una longitud de matriz que no era un número positivo ni cero.  Este error se produce al asignar un valor a la propiedad **length** de un objeto `Array` que es negativo o no es un número \(`NaN`\).  Ten en cuenta que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convierte automáticamente los números fraccionarios a enteros.  
  
### Para corregir este error  
  
-   Asigna un número entero positivo a la propiedad length.  No hay límite superior para el tamaño de una matriz, salvo el valor entero máximo \(aproximadamente cuatro mil millones\).  En el ejemplo siguiente se muestra la forma correcta de definir la propiedad **length** de un objeto **Array**.  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## Vea también  
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)