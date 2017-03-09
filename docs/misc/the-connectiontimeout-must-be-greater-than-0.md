---
title: "El valor de ConnectionTimeout debe ser mayor que 0 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrNetwork_BadConnectionTimeout"
ms.assetid: 15ac09a7-47f0-44f3-9e84-5bd10bd07450
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El valor de ConnectionTimeout debe ser mayor que 0
Al cargar y descargar archivos con el [My.Computer.Network \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-computer-network-object), debe especificar un `connectionTimeout` mayor que `0`.  
  
### Para corregir este error  
  
-   Proporcione un valor de `connectionTimeout` que sea mayor que `0`.  
  
## Vea también  
 [Método My.Computer.Network.UploadFile](http://msdn.microsoft.com/es-es/5505ea3e-3dbd-460b-9f8f-62c84c0a4de6)   
 [Método My.Computer.Network.DownloadFile](http://msdn.microsoft.com/es-es/aeb7ed8f-1ac9-4242-ae57-9f35914eb329)   
 [Cómo: Cargar un archivo](../Topic/How%20to:%20Upload%20a%20File%20in%20Visual%20Basic.md)   
 [Cómo: Descargar un archivo](../Topic/How%20to:%20Download%20a%20File%20in%20Visual%20Basic.md)   
 [Operaciones de red en .NET Framework con Visual Basic](http://msdn.microsoft.com/es-es/c5379021-44ef-4d6a-acf5-e951fdcab6b2)