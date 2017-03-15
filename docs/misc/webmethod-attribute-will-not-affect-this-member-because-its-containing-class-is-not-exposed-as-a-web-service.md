---
title: "El atributo &#39;WebMethod&#39; no tendr&#225; ning&#250;n efecto en este miembro porque su clase contenedora no est&#225; expuesta como un servicio web | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30771"
  - "bc30771"
helpviewer_keywords: 
  - "BC30771"
ms.assetid: 20b09f6a-b61a-4d89-9ca5-4632b5e68e65
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo &#39;WebMethod&#39; no tendr&#225; ning&#250;n efecto en este miembro porque su clase contenedora no est&#225; expuesta como un servicio web
El atributo <xref:System.Web.Services.WebMethodAttribute> hace que un método se pueda llamar desde clientes web remotos, pero solo cuando la clase del método deriva de <xref:System.Web.Services.WebService>.  
  
 **Identificador de error:** BC30771  
  
### Para corregir este error  
  
-   Cambie la clase para que se derive de <xref:System.Web.Services.WebService>.  
  
     O bien  
  
-   Quite el atributo <xref:System.Web.Services.WebMethodAttribute> del método.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Tutorial: Crear un servicio web usando Visual Basic o Visual C\#](http://msdn.microsoft.com/es-es/295f4c3f-9540-4bd1-b1cc-3e9cb9675cc7)