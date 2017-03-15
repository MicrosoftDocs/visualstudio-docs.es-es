---
title: "Error de MSBuild MSB3151 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
helpviewer_keywords: 
  - "MSB3151"
ms.assetid: e4766734-2e90-436e-850b-a8a9da535dee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3151
**MSB3151: El elemento '\<paquete\>' ya incluye '\<paquete\>'.**  
  
 Esta advertencia se produce cuando hay dos paquetes de arranque seleccionados y un paquete ya incluye el otro \(por ejemplo, la selección del paquete incluido es redundante\).  
  
### Para corregir este error  
  
-   Desactive la casilla para el paquete incluido de forma redundante.