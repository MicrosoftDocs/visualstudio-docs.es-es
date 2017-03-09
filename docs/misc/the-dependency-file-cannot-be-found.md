---
title: "The dependency &#39;file&#39; cannot be found | Microsoft Docs"
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
  - "vs.tasklisterror.supdepnotfound"
ms.assetid: a0e6e658-c723-40da-8275-fa212165bd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The dependency &#39;file&#39; cannot be found
Una de las referencias del proyecto contiene una referencia \(dependencia\) que no se ha podido ubicar.  
  
 Si da de alta un proyecto en control del código fuente, puede que algunas dependencias del equipo estén sin resolver.  Esto se debe a que la propiedad ruta de acceso de referencia es una propiedad específica para equipos y, por tanto, no está sometida al control de código fuente.  
  
### Para corregir este error  
  
1.  Localice la referencia de ensamblado indicada en el disco y modifique la propiedad Ruta de acceso de referencia.  
  
2.  Si no puede localizar el archivo de ensamblado en el disco, puede que tenga que volver a instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o cualquier control personalizado de terceros en caso de que no se puedan encontrar las dependencias en el disco.  Además, si está dando de alta un proyecto bajo control de código fuente, puede que tenga que instalar cualquier control de terceros requerido por ese proyecto.  
  
 Esta situación no impedirá la compilación del proyecto.  No obstante, puede que se produzca una excepción TypeLoadException al ejecutar la aplicación.  La dependencia afectada no se comunicará al proceso de implementación.  
  
 Puede ver las referencias del proyecto en el Explorador de soluciones, en el nodo **Referencias**.  
  
## Vea también  
 [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/es-es/8e549b39-7256-456a-8fd7-089b23facf9c)