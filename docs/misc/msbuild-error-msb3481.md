---
title: "Error de MSBuild MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3481
**MSB3481: No se encontró el certificado de firma.  Asegúrese de que se encuentra en el almacén personal del usuario actual.**  
  
 Este error se genera cuando no se encuentra el certificado de firma en el almacén de certificados personal.  Este error es similar a [Error de MSBuild MSB3486](../misc/msbuild-error-msb3486.md), que significa que se ha encontrado el certificado pero que no coincide.  
  
### Para corregir este error  
  
-   Asegúrese de que en el almacén de certificados personal haya un certificado válido que coincida con el archivo .pfx del proyecto.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)