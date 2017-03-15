---
title: "Error: no se puede copiar la dependencia &#39;archivo&#39; del proyecto &#39;proyecto&#39; en el directorio de ejecuci&#243;n porque entrar&#237;a en conflicto con la dependencia &#39;archivo&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error: no se puede copiar la dependencia &#39;archivo&#39; del proyecto &#39;proyecto&#39; en el directorio de ejecuci&#243;n porque entrar&#237;a en conflicto con la dependencia &#39;archivo&#39;
Existe un conflicto entre referencias; se está copiando más de una dependencia distinta con el mismo nombre de archivo en el directorio bin para que la aplicación se ejecute. El directorio de ejecución no puede resolver el conflicto porque ninguna de las dependencias es una referencia principal.  
  
 Este error impedirá que la compilación se lleve a cabo.  
  
 Haga doble clic en este elemento de lista de tareas para ir al nodo de referencias del proyecto en el que se ha producido el conflicto.  
  
 **Para corregir este error**  
  
-   Convierta uno de los ensamblados en una referencia directa del proyecto. Un posible inconveniente de este método es que no está garantizado que el ensamblado que elija funcione con los ensamblados que pueden requerir alguna otra versión del ensamblado al que se hace referencia.  
  
     o bien  
  
-   Procure que ambas copias del ensamblado tengan nombres seguros y estén en la memoria caché global de ensamblados. Así, no será necesario copiar los ensamblados en el directorio bin.  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [Caché global de ensamblados](../Topic/Global%20Assembly%20Cache.md)   
 [Ensamblados con nombre seguro](../Topic/Strong-Named%20Assemblies.md)   
 [Versiones de los ensamblados](../Topic/Assembly%20Versioning.md)   
 [Cómo: Crear y quitar dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md)