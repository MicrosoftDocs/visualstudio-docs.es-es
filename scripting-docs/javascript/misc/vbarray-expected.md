---
title: "Se espera VBArray | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Se espera VBArray
Has proporcionado un objeto que no era safeArray de Visual Basic, cuando se esperaba uno.  
  
```  
new VBArray(safeArray);  
```  
  
 Los valores VBArray son de solo lectura y no se pueden crear directamente.  El argumento safeArray es un valor VBArray y debe haber obtenido un valor VBArray antes de pasarlo al constructor de `VBArray`.  Esto solo se consigue recuperando el valor de un objeto ActiveX u otro objeto existente.  
  
### Para corregir este error  
  
-   Asegúrate de pasar únicamente objetos **VBArray** al constructor de **VBArray**.  
  
## Vea también  
 [VBArray \(Objeto\)](../../javascript/reference/vbarray-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)