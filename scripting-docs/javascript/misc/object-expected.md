---
title: "Se esperaba un objeto | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5007"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Se esperaba un objeto
Se intentó invocar un método o propiedad en un objeto de un tipo distinto de `Object`, o se pasó un argumento de un tipo distinto de `Object` cuando se requería `Object`.  
  
### Para corregir este error  
  
-   Invoque el método o propiedad solo en objetos de tipo `Object`.  
  
-   Si se produce un error para un argumento que no es de objeto, pase un objeto de tipo `Object`.  
  
-   Compruebe si se está invocando una referencia nula o indefinida en lugar de un objeto de tipo `Object`.  
  
     Por ejemplo, si obtiene este error en myVar en el código siguiente:  
  
    ```javascript  
    var str = myVar.toString();  
    ```  
  
     puede usar en su lugar este código:  
  
    ```javascript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## Vea también  
 [Object \(Objeto\)](../../javascript/reference/object-object-javascript.md)   
 [Objetos y matrices](../../javascript/objects-and-arrays-javascript.md)