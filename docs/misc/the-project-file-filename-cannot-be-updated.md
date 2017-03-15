---
title: "The project file &#39;&lt;filename&gt;&#39; cannot be updated | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file &#39;&lt;filename&gt;&#39; cannot be updated
Está intentando abrir un proyecto creado con una versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  El proyecto debe actualizarse al formato actual, pero no se puede actualizar porque el archivo de proyecto especificado \(.vbproj\) está marcado como de sólo lectura o el archivo está bajo control de código fuente y está actualmente bloqueado por otro usuario.  
  
### Para corregir este error  
  
1.  En el Explorador de archivos, busque el archivo de proyecto especificado.  
  
2.  En el menú **Archivo**, elija **Propiedades**.  
  
3.  En el cuadro de diálogo **Propiedades**, desactive el atributo **Sólo lectura**.  
  
 Si el archivo está bajo control de código fuente y está bloqueado por otro usuario, espere hasta que esté disponible y desprotéjalo localmente.  
  
## Vea también  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)