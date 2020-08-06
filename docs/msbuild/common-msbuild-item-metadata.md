---
title: Metadatos de elementos MSBuild comunes | Microsoft Docs
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c715c16782733a08bb617a464c1aa9510d35b54
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425972"
---
# <a name="common-msbuild-item-metadata"></a>Metadatos de elementos MSBuild comunes

En la tabla siguiente se describen metadatos de elementos opcionales que tienen significado para algunos SDK o destinos de MSBuild, pero que no se establecen de forma predeterminada para todos los elementos. Puede establecerlos para influir en el comportamiento de la compilación, pero solo si el SDK o los archivos de destino que usa lo reconocen.

| Metadatos de elementos | SDK | Descripción |
|---------------| ------- | -------------|
|%(Link)| Todas |El sistema de proyectos de Visual Studio usa metadatos `Link` (si están presentes) para modificar lo que se muestra en el árbol del proyecto. Puede colocar un archivo en una estructura de carpetas lógicas diferente del **Explorador de soluciones**.<br />Además, la tarea `AssignTargetPath` examina `Link` para determinar en qué lugar del directorio de salida se debe copiar un archivo, si es uno de los elementos que se copian.|
|%(LinkBase)| SDK de .NET Core | Se usa para establecer la carpeta que se va a utilizar para los metadatos `Link` de grupos de elementos. |

## <a name="see-also"></a>Vea también

- [Propiedades comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)
- [Metadatos de los elementos conocidos de MSBuild](msbuild-well-known-item-metadata.md)