---
title: "La funci&#243;n no tiene un objeto prototipo v&#225;lido | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# La funci&#243;n no tiene un objeto prototipo v&#225;lido
Has intentado usar **instanceof** para determinar si un objeto provenía de una clase de función determinada, pero has redefinido la propiedad `prototype` del objeto como `null` o como un tipo de objeto externo \(ninguno de ellos es un objeto válido de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\).  Un objeto externo puede ser un objeto del modelo de objetos host \(por ejemplo, un documento de Internet Explorer o un objeto de ventana\) o un objeto COM externo.  
  
### Para corregir este error  
  
-   Comprueba que la propiedad `prototype` de la función hace referencia a un objeto de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] válido.  
  
## Vea también  
 [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)   
 [prototype \(Propiedad, Object\)](../../javascript/reference/prototype-property-object-javascript.md)