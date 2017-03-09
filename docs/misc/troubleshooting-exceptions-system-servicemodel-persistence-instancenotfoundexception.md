---
title: "Soluci&#243;n de problemas de excepciones: System.ServiceModel.Persistence.InstanceNotFoundException | Microsoft Docs"
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
  - "InstanceNotFoundException (excepción)"
  - "System.ServiceModel.Persistence.InstanceNotFoundException (excepción)"
ms.assetid: e3905352-dff0-41d4-b970-8e1b26d85a83
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ServiceModel.Persistence.InstanceNotFoundException
Se produce una excepción <xref:System.ServiceModel.Persistence.InstanceNotFoundException> en las circunstancias siguientes:  
  
-   Se realiza una operación en una instancia de servicio duradero marcada para su finalización.  
  
-   Un proveedor de persistencia creado por <xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory> intenta bloquear, desbloquear o procesar de otro modo datos de estado que no se encuentran en la base de datos.  
  
## Vea también  
 <xref:System.ServiceModel.Persistence.InstanceNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)