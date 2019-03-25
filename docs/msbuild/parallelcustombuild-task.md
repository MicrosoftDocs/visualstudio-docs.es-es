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
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 506ead6680bd9a0aaaf38d6959da02a14dfee337
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070469"
---
# <a name="parallelcustombuild-task"></a>Tarea ParallelCustomBuild

Ejecute instancias en paralelo de la [tarea CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **ParallelCustomBuild**.

|Parámetro|Descripción|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parámetro **bool** opcional.|
|**MaxItemsInBatch**|Parámetro **int** opcional.|
|**MaxProcesses**|Parámetro **int** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]**.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)