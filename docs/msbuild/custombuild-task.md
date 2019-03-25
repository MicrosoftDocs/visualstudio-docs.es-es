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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 183cdefbca29db486b84cb61f90501507e298838
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070475"
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