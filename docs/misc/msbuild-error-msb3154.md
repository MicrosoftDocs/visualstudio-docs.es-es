---
title: "Error de MSBuild MSB3154 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
helpviewer_keywords: 
  - "MSB3154"
ms.assetid: 513b70fa-15f5-4137-bdbc-5974607fb75a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3154
**MSB3154: No se pudieron encontrar los recursos de cadenas para '\<elemento\>'.**  
  
 Este error se genera cuando el paquete especificado no contiene información específica de la referencia cultural.  No existe un archivo package.xml o no contiene un atributo `Culture`.  
  
### Para corregir este error  
  
-   Proporcione un archivo package.xml válido que contenga una etiqueta `Culture` correcta.