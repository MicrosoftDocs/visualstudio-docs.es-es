---
title: "Error de MSBuild MSB3115 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidEntryPoint"
helpviewer_keywords: 
  - "MSB3115"
ms.assetid: 7d9d4156-fd6a-455a-8a3d-b191485f1294
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3115
**MSB3115: El archivo '\<archivo\>' no es un punto de entrada válido.**  
  
 Este error se genera cuando un manifiesto especifica un punto de entrada que no es válido.  
  
### Para corregir este error  
  
-   Asegúrese de especificar puntos de entrada válidos en los manifiestos.  En el caso de un manifiesto de aplicación, un punto de entrada válido es un archivo .exe.  En el caso de un manifiesto de implementación, un punto de entrada válido es un manifiesto de aplicación.