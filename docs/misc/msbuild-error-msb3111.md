---
title: "Error de MSBuild MSB3111 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ConfigBindingRedirectsWithPartialTrust"
helpviewer_keywords: 
  - "MSB3111"
ms.assetid: f01286a1-ba27-4733-a431-35ffe9a31356
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3111
**MSB3111: El uso de redireccionamientos de enlace al archivo app.config requiere plena confianza.**  
  
 Esta advertencia se genera cuando el proceso de compilación detecta que la aplicación ha intentado redirigir algunos de sus ensamblados a otra versión en el archivo app.config.  Esto no funcionará para las aplicaciones de confianza parcial.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)