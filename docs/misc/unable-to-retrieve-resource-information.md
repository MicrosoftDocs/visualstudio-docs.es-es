---
title: "Unable to retrieve resource information | Microsoft Docs"
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
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to retrieve resource information
La exploración de la jerarquía de archivos .resx produjo un error.  
  
 Como parte del paso de compilación `Preparing resources`, visible en la **Ventana de salida**, el sistema de proyectos explorará la jerarquía del proyecto para buscar todos los archivos con una extensión .resx.  Esto producirá una lista de archivos XML .resx que se deben transformar en archivos binarios .resources antes de incluirlos como recursos en los resultados del proyecto.  
  
 **Para corregir este error**  
  
-   Reinicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si esto no funciona, llame a los servicios de soporte técnico de Microsoft para informar del problema.  
  
     Este error puede impedir que la compilación se lleve a cabo.  
  
## Vea también  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/es-es/f793852c-da06-4d52-a826-65f635844772)