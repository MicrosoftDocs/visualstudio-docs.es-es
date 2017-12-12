---
title: Usar la memoria de forma eficaz al compilar proyectos grandes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e9484e0b8771ad665f1891298ff2f6a8a1d0005e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Usar la memoria de forma eficaz al compilar grandes proyectos
Los proyectos grandes suelen contener numerosos subproyectos y otras dependencias, que pueden consumir una gran cantidad de memoria del sistema en tiempo de compilación. Cuando se reduce la memoria disponible del sistema, el rendimiento del sistema se puede ver afectado. Las versiones anteriores de proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] permanecían en la memoria, mientras que en la versión 3.5 los proyectos se quitaban, aunque los resultados de la compilación se conservaban en una memoria caché para su recuperación posterior.  
  
 La versión 4.0 controla la administración de la memoria automáticamente, ya que hace que los proyectos no tengan que usar propiedades como `UnloadProjectsOnCompletion` y `UseResultsCache`.  
  
## <a name="see-also"></a>Vea también  
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)