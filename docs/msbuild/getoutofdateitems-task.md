---
title: Tarea GetOutOfDateItems | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747319"
---
# <a name="getoutofdateitems-task"></a>Tarea GetOutOfDateItems

Tarea asistente que lee TLog antiguos, escribe TLog nuevos y devuelve un conjunto de elementos no actualizados.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **GetOutOfDateItems**.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**CheckForInterdependencies**|Parámetro **bool** opcional.|
|**CommandMetadataName**|Parámetro **string** opcional.|
|**DependenciesMetadataName**|Parámetro **string** opcional.|
|**HasInterdependencies**|Parámetro de salida **bool** opcional.|
|**OutOfDateSources**|Parámetro de salida opcional de tipo **ITaskItem[]** .|
|**OutputsMetadataName**|Parámetro obligatorio de tipo **String**.|
|**Sources**|Parámetro opcional de tipo **ITaskItem[]** .|
|**TLogDirectory**|Parámetro obligatorio de tipo **String**.|
|**TLogNamePrefix**|Parámetro obligatorio de tipo **String**.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)