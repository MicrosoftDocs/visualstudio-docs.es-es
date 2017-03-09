---
title: "Error de MSBuild MSB3148 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3148
**MSB3148: No se proporcionó ninguna ruta de acceso de resultados en la configuración de compilación.**  
  
 Este error se produce cuando se especifica una ruta de acceso nula o no válida; por ejemplo, si `OutputPath=""` en el archivo de proyecto.  El valor predeterminado de la ruta de acceso de resultados es `CurrentDirectory`.  
  
### Para corregir este error  
  
-   Asegúrese de que `OutputPath` no está en blanco o no está incluido en el archivo de proyecto.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)