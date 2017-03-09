---
title: "Error de MSBuild MSB3121 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationMissingAttribute"
helpviewer_keywords: 
  - "MSB3121"
ms.assetid: c1e83a2a-515f-412d-b8b7-4821e510a923
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3121
**MSB3121: En el elemento de asociación de archivo del manifiesto de aplicación faltan uno o varios de los siguientes atributos necesarios: extension, description, progid o default icon.**  
  
 El [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) debe contener los valores de los cuatro atributos.  
  
### Para corregir este error  
  
-   Establezca cada atributo [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) en un valor válido.  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)