---
title: Usar la memoria de forma eficaz al compilar proyectos grandes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2cb204fcfb5a96fe9833571895513dfda4449b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577378"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Usar la memoria de forma eficaz al compilar grandes proyectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [utilizando memoria eficazmente cuando puede compilar proyectos grandes](https://docs.microsoft.com/visualstudio/msbuild/using-memory-efficiently-when-you-build-large-projects).  
  
  
Los proyectos grandes suelen contener numerosos subproyectos y otras dependencias, que pueden consumir una gran cantidad de memoria del sistema en tiempo de compilación. Cuando se reduce la memoria disponible del sistema, el rendimiento del sistema se puede ver afectado. Las versiones anteriores de proyectos de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] permanecían en la memoria, mientras que en la versión 3.5 los proyectos se quitaban, aunque los resultados de la compilación se conservaban en una memoria caché para su recuperación posterior.  
  
 La versión 4.0 controla la administración de la memoria automáticamente, ya que hace que los proyectos no tengan que usar propiedades como `UnloadProjectsOnCompletion` y `UseResultsCache`.  
  
## <a name="see-also"></a>Vea también  
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



