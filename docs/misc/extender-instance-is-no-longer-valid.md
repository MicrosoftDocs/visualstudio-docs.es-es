---
title: "Extender instance is no longer valid. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTINVALID"
ms.assetid: 6361ba35-f2c5-4024-9362-46d7d9daf651
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender instance is no longer valid.
No se ha podido crear satisfactoriamente la instancia del extensor, o se ha destruido.  
  
### Para corregir este error  
  
1.  Vuelva a obtener la instancia del extensor del objeto Extendee  
  
     \-O bien\-  
  
     Vuelva a obtener la instancia del extensor llamando a DTE.ObjectExtenders.GetExtender\(\).  
  
## Vea también  
 <xref:EnvDTE.ObjectExtenders>   
 <xref:EnvDTE.ObjectExtenders.GetExtender%2A>