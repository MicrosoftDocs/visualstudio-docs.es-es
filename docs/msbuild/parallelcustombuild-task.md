---
title: Tarea ParallelCustomBuild | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea ParallelCustomBuild para ejecutar instancias paralelas de la tarea CustomBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048899"
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