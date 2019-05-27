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
ms.openlocfilehash: 6d466dec85a0bdf242120ef5e88a0d5f5d2ac48e
ms.sourcegitcommit: 0ef51e3517436a85cfb85bf492722d566ce602c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934514"
---
# <a name="custombuild-task"></a>Tarea CustomBuild

Contiene la herramienta compiladora de Visual C++, cmd.exe. Esta clase deriva de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), pero no usa seguimiento de archivos para detectar dependencias de archivos. Todas las dependencias se deben especificar de forma explícita como AdditionalDependencies para que la compilación incremental funcione correctamente.


## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea**CustomBuild**.

|Parámetro|Descripción|
|---------------|-----------------|
|**BuildSuffix**|Parámetro **string** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|
|**TrackerLogDirectory**|Parámetro **string** opcional.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)
