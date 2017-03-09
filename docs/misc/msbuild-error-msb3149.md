---
title: "Error de MSBuild MSB3149 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3149
**MSB3149: Ningún recurso disponible para compilar un arranque.**  
  
 Este error se produce cuando no se puede encontrar ningún archivo de recursos de arranque \(setup.xml\) que coincida con la referencia cultural.  
  
### Para corregir este error  
  
-   Vaya al **Panel de control**, seleccione **Agregar o quitar programas** y repare el SDK de Visual Studio, o bien, copie los archivos en el directorio apropiado \(\<ruta de instalación del SDK\>\\bootstrapper\\engine\\\<referencia cultural\>\\setup.xml\).  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)