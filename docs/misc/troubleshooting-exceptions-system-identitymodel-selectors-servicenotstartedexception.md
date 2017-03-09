---
title: "Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.ServiceNotStartedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.ServiceNotStartedException (excepción)"
  - "ServiceNotStartedException (excepción)"
ms.assetid: 6d34bab2-994a-4b0c-893d-19b5d7acf92d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.ServiceNotStartedException
Se produce una excepción <xref:System.IdentityModel.Selectors.ServiceNotStartedException> cuando no se ha iniciado CardSpace en el equipo del usuario. Si CardSpace ha intentado iniciarse pero no ha podido por cualquier razón, se produce esta excepción.  
  
 Compruebe que el servicio CardSpace está instalado y habilitado en el equipo. Intente iniciar el servicio CardSpace manualmente utilizando Microsoft Management Console \(MMC\).  
  
 La versión 1 de CardSpace no admite los sistemas de archivos FAT. En los sistemas FAT, CardSpace no se iniciará y se producirá esta excepción.  
  
## Vea también  
 <xref:System.IdentityModel.Selectors.ServiceNotStartedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)