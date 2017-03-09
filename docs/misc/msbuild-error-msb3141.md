---
title: "Error de MSBuild MSB3141 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3141
**MSB3141: No se especificó ningún atributo 'PublicKey' o 'Hash' para el archivo '\<archivo\>' del elemento '\<paquete\>'."**  
  
 Este error se produce cuando se intenta utilizar HomeSite para los paquetes de arranque.  Sin embargo, el manifiesto de arranque no contiene la información correcta para la comprobación del archivo \(clave pública o código hash\) en tiempo de ejecución.  
  
### Para corregir este error  
  
-   Descargue el archivo del paquete para el que falte la información y cópielo en la caché de arranque.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)