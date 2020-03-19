---
title: Tarea ParallelCustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279268"
---
# <a name="parallelcustombuild-task"></a>Tarea ParallelCustomBuild

Ejecute instancias en paralelo de la [tarea CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **ParallelCustomBuild**.

|Parámetro|Description|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parámetro **bool** opcional.|
|**MaxItemsInBatch**|Parámetro **int** opcional.|
|**MaxProcesses**|Parámetro **int** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)