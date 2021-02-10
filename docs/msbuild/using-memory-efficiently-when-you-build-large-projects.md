---
title: Usar la memoria de forma eficaz al compilar proyectos grandes | Microsoft Docs
description: Obtenga información sobre cómo MSBuild administra automáticamente la memoria, como descargar versiones anteriores y recuperar memorias caché, al compilar proyectos de gran tamaño.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99cee9cfbf779bbee97c00fb76f9670e1d609b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965907"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Usar la memoria de forma eficaz al compilar proyectos grandes

Los proyectos grandes suelen contener numerosos subproyectos y otras dependencias, que pueden consumir una gran cantidad de memoria del sistema en tiempo de compilación. Cuando se reduce la memoria disponible del sistema, el rendimiento del sistema se puede ver afectado. Las versiones anteriores de proyectos de MSBuild permanecían en memoria. La versión 3.5 quitaba las versiones anteriores de los proyectos, pero conservaba los resultados de compilación en una caché para su posterior recuperación.

 La versión 4.0 controla la administración de la memoria automáticamente, ya que hace que los proyectos no tengan que usar propiedades como `UnloadProjectsOnCompletion` y `UseResultsCache`.

### <a name="see-also"></a>Consulte también

- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
