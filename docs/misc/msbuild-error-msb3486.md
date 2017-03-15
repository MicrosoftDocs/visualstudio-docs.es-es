---
title: "Error de MSBuild MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3486
**MSB3486: No se puede obtener el certificado del almacén '\<almacén de certificados\>'.**  
  
 La tarea `ResolveKeySource` de MSBuild genera este error cuando en el almacén de certificados personal no se encuentra un certificado que coincida con la huella digital del archivo .pfx del proyecto.  
  
### Para corregir este error  
  
-   Asegúrese de que la huella digital del archivo .pfx del proyecto coincida con la del certificado en el almacén de certificados personal.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)