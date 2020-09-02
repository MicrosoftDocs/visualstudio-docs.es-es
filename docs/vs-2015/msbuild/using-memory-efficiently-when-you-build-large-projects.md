---
title: Usar la memoria de forma eficaz al compilar proyectos grandes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28d9f3d43faa53731b101dfdf58fe1e68a0920c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178296"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Usar la memoria de forma eficaz al compilar grandes proyectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los proyectos grandes suelen contener numerosos subproyectos y otras dependencias, que pueden consumir una gran cantidad de memoria del sistema en tiempo de compilación. Cuando se reduce la memoria disponible del sistema, el rendimiento del sistema se puede ver afectado. Las versiones anteriores de proyectos de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] permanecían en la memoria, mientras que en la versión 3.5 los proyectos se quitaban, aunque los resultados de la compilación se conservaban en una memoria caché para su recuperación posterior.  
  
 La versión 4.0 controla la administración de la memoria automáticamente, ya que hace que los proyectos no tengan que usar propiedades como `UnloadProjectsOnCompletion` y `UseResultsCache`.  
  
## <a name="see-also"></a>Consulte también  
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
