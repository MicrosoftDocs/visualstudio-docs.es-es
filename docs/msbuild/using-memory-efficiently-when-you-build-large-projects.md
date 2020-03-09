---
title: Usar la memoria de forma eficaz al compilar proyectos grandes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631320"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Usar la memoria de forma eficaz al compilar proyectos grandes

Los proyectos grandes suelen contener numerosos subproyectos y otras dependencias, que pueden consumir una gran cantidad de memoria del sistema en tiempo de compilación. Cuando se reduce la memoria disponible del sistema, el rendimiento del sistema se puede ver afectado. Las versiones anteriores de proyectos de MSBuild permanecían en memoria. La versión 3.5 quitaba las versiones anteriores de los proyectos, pero conservaba los resultados de compilación en una caché para su posterior recuperación.

 La versión 4.0 controla la administración de la memoria automáticamente, ya que hace que los proyectos no tengan que usar propiedades como `UnloadProjectsOnCompletion` y `UseResultsCache`.

### <a name="see-also"></a>Vea también

- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
