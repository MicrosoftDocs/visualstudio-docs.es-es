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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515131"
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