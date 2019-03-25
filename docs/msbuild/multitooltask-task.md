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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: bd0c5510c754043a0a55b305c671ce9487cabb49
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070494"
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