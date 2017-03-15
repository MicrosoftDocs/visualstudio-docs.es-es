---
title: "Soluci&#243;n de problemas de excepciones: System.CannotUnloadAppDomainException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CannotUnloadAppDomainException (clase)"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.CannotUnloadAppDomainException
Si se intenta descargar uno de los elementos siguientes, se produce una excepción <xref:System.CannotUnloadAppDomainException>:  
  
-   El dominio de aplicación predeterminado, que debe permanecer cargado a lo largo del período de duración de la aplicación  
  
-   Un dominio de aplicación con un subproceso en ejecución que no puede detener la ejecución de forma inmediata  
  
-   Un dominio de aplicación que ya ha se ha descargado  
  
## Sugerencias asociadas  
 **Asegúrese de que no intenta descargar el dominio de aplicación predeterminado, que tiene un subproceso en ejecución o que ya se ha descargado.**  
 Cualquiera de estas condiciones producirá esta excepción. Para obtener más información, consulta <xref:System.AppDomain.Unload%2A>.  
  
## Vea también  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)