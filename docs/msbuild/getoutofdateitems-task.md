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
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 668dddcd0854869c9ede7bf96c092d415f41dd17
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070470"
---
# <a name="getoutofdateitems-task"></a>Tarea GetOutOfDateItems

Tarea asistente que lee TLog antiguos, escribe TLog nuevos y devuelve un conjunto de elementos no actualizados.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **GetOutOfDateItems**.

|Parámetro|Descripción|
|---------------|-----------------|
|**CheckForInterdependencies**|Parámetro **bool** opcional.|
|**CommandMetadataName**|Parámetro **string** opcional.|
|**DependenciesMetadataName**|Parámetro **string** opcional.|
|**HasInterdependencies**|Parámetro de salida **bool** opcional.|
|**OutOfDateSources**|Parámetro de salida opcional de tipo **ITaskItem[]**.|
|**OutputsMetadataName**|Parámetro obligatorio de tipo **String**.|
|**Sources**|Parámetro opcional de tipo **ITaskItem[]**.|
|**TLogDirectory**|Parámetro obligatorio de tipo **String**.|
|**TLogNamePrefix**|Parámetro obligatorio de tipo **String**.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)