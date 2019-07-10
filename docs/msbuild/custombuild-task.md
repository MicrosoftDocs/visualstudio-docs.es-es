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
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587018"
---
# <a name="custombuild-task"></a>Tarea CustomBuild

Contiene la herramienta compiladora de Visual C++, cmd.exe. Esta clase deriva de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), pero no usa seguimiento de archivos para detectar dependencias de archivos. Todas las dependencias se deben especificar de forma explícita como AdditionalDependencies para que la compilación incremental funcione correctamente.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea**CustomBuild**.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**BuildSuffix**|Parámetro **string** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|
|**TrackerLogDirectory**|Parámetro **string** opcional.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)
