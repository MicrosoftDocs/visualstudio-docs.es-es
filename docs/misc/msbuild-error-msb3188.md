---
title: "Error de MSBuild MSB3188 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3188
**MSB3188: El ensamblado '\<ensamblado\>' debe estar firmado de manera segura para que se marque como un requisito previo.**  
  
 Se genera este error cuando un ensamblado de requisito previo no está firmado de manera segura.  Sólo se aplica a los manifiestos de aplicación.  
  
### Para corregir este error  
  
-   Asegúrese de que todos los ensamblados que utiliza el proyecto están firmados de manera segura.