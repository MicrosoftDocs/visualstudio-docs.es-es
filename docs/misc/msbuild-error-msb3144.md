---
title: "Error de MSBuild MSB3144 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3144
**MSB3144: No se proporcionaron suficientes datos para generar un arranque.  Proporcione un valor para al menos uno de los parámetros: 'ApplicationFile' o 'BootstrapperItems'.**  
  
 Este error se produce cuando no se han proporcionado suficientes datos para generar un arranque.  El proceso de compilación crea un arranque vacío sin instalador de aplicación ni paquetes.  
  
### Para corregir este error  
  
-   Proporcione un valor para al menos uno de los parámetros `ApplicationFile` o `BootstrapperItems`.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)