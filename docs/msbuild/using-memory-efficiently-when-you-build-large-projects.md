---
title: "Usar la memoria de forma eficaz al compilar grandes proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "almacenamiento en caché (MSBuild)"
  - "uso de memoria (MSBuild)"
  - "msbuild, uso eficaz de la memoria al compilar árboles grandes"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Usar la memoria de forma eficaz al compilar grandes proyectos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con frecuencia, los proyectos grandes contienen muchos subproyectos y otras dependencias, y éstos pueden consumir mucha memoria del sistema en tiempo de compilación.  Cuando se disminuye la memoria del sistema disponible, puede disminuir también el rendimiento del sistema.  Las versiones anteriores de los proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] permanecían en memoria o, en la versión 3.5, los proyectos se quitaban, pero los resultados de la compilación se mantenían en una memoria caché para su posterior recuperación.  
  
 La versión 4.0 controla automáticamente esta administración de memoria, lo que evita que los proyectos tengan que usar propiedades como `UnloadProjectsOnCompletion` y `UseResultsCache`.  
  
## Vea también  
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)