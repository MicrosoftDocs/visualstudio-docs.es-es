---
title: "Error de MSBuild MSB3122 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsApplicationNotFullTrust"
helpviewer_keywords: 
  - "MSB3122"
ms.assetid: 523e4160-f165-437a-9f19-fb2ec77d46f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3122
**MSB3122: El uso de asociaciones de archivo requiere plena confianza.**  
  
 Publicar una aplicación que configura asociaciones de archivo requiere que la aplicación sea de plena confianza.  
  
### Para corregir este error  
  
-   Habilite los valores de seguridad de ClickOnce y establezca la aplicación como aplicación de plena confianza.  Para obtener más información, consulte [Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)