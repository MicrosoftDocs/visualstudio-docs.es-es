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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 197128fadb660ab06686d13ec304a5d9d1698070
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515433"
---
# <a name="custombuild-task"></a>Tarea CustomBuild

Contiene la herramienta compiladora de Visual C++, cmd.exe.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea**CustomBuild**.

|Parámetro|Descripción|
|---------------|-----------------|
|**BuildSuffix**|Parámetro **string** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]**.|
|**TrackerLogDirectory**|Parámetro **string** opcional.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)