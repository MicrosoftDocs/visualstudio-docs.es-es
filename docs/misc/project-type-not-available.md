---
title: "Tipo de proyecto no disponible | Microsoft Docs"
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
  - "vs.projecttypenotavailable"
helpviewer_keywords: 
  - "Tipo de proyecto no disponible (error)"
ms.assetid: a579fe75-efa2-4dd0-b5d7-ae106d3aedbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Tipo de proyecto no disponible
Este cuadro de diálogo muestra el error "No se puede abrir \<proyecto\>. Su tipo de proyecto \<tipo\_proyecto\> no es compatible con esta versión de la aplicación".  
  
## Solución  
  
-   Este cuadro de diálogo aparece porque no se encuentra el producto o la versión de producto necesaria para abrir el archivo especificado.  Es normal que este error ocurra al intentar abrir un archivo de proyecto que no se puede abrir con la versión instalada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Por ejemplo, al intentar abrir un archivo de proyecto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] con [!INCLUDE[vbprvbxprlong](../misc/includes/vbprvbxprlong_md.md)], aparece este cuadro de diálogo.  
  
#### Para solucionar este error  
  
-   Instale la versión correcta de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Referencia de propiedades del proyecto](../ide/reference/project-properties-reference.md)