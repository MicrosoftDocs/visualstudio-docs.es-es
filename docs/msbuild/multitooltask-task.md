---
title: Tarea MultiToolTask | Microsoft Docs
description: Acceda a una tabla que describe los parámetros obligatorios y opcionales de la tarea MultiToolTask de MSBuild.
ms.custom: SEO-VS-2020
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
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d76aa3762b254ee35ada1e4e81fe857f509a4e5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048975"
---
# <a name="multitooltask-task"></a>Tarea MultiToolTask

Sin descripción.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **MultiToolTask**.

|Parámetro|Description|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Parámetro **string[]** opcional.|
|**SemaphoreProcCount**|Parámetro **string** opcional.|
|**SchedulerFunction**|Parámetro **string** opcional.|
|**SchedulerVerbose**|Parámetro **bool** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|
|**TaskAssemblyName**|Parámetro **string** opcional.|
|**TaskName**|Parámetro obligatorio de tipo **String**.|
|**TrackerLogDirectory**|Parámetro obligatorio de tipo **String**.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)
