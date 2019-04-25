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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: e3393dd7e81fa98c49dd09a32457171286f88f18
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514981"
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