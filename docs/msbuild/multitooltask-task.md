---
title: Tarea MultiToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), MultiToolTask task
- MultiToolTask task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: a16a61c06bf80bef3fbb78f155cd8b41905a8d72
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515195"
---
# <a name="multitooltask-task"></a>Tarea MultiToolTask

Sin descripción.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **MultiToolTask**.

|Parámetro|Descripción|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Parámetro **string[]** opcional.|
|**SemaphoreProcCount**|Parámetro **string** opcional.|
|**SchedulerFunction**|Parámetro **string** opcional.|
|**SchedulerVerbose**|Parámetro **bool** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]**.|
|**TaskAssemblyName**|Parámetro **string** opcional.|
|**TaskName**|Parámetro obligatorio de tipo **String**.|
|**TrackerLogDirectory**|Parámetro obligatorio de tipo **String**.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)