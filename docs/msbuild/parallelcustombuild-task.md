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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6ea14e61eb2d62f3fc9ccdac3a17010ccc9194f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747219"
---
# <a name="parallelcustombuild-task"></a>Tarea ParallelCustomBuild

Ejecute instancias en paralelo de la [tarea CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **ParallelCustomBuild**.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parámetro **bool** opcional.|
|**MaxItemsInBatch**|Parámetro **int** opcional.|
|**MaxProcesses**|Parámetro **int** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)