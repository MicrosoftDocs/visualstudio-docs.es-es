---
title: Tarea CustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748111"
---
# <a name="custombuild-task"></a>Tarea CustomBuild

Incluye la herramienta del compilador de Microsoft C++, cmd.exe. Esta clase deriva de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), pero no usa seguimiento de archivos para detectar dependencias de archivos. Todas las dependencias se deben especificar de forma explícita como AdditionalDependencies para que la compilación incremental funcione correctamente.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea**CustomBuild**.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**BuildSuffix**|Parámetro **string** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|
|**TrackerLogDirectory**|Parámetro **string** opcional.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)
