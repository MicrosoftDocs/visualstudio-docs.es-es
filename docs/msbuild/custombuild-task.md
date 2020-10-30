---
title: Tarea CustomBuild | Microsoft Docs
description: En este artículo se describe la tarea CustomBuild de MSBuild, que MSBuild usa para admitir la personalización del proceso de compilación de C++.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796555"
---
# <a name="custombuild-task"></a>Tarea CustomBuild

Incluye la herramienta del compilador de Microsoft C++, cmd.exe. Esta clase deriva de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), pero no usa seguimiento de archivos para detectar dependencias de archivos. Todas las dependencias se deben especificar de forma explícita como AdditionalDependencies para que la compilación incremental funcione correctamente.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **CustomBuild** .

|Parámetro|Descripción|
|---------------|-----------------|
|**BuildSuffix**|Parámetro **string** opcional.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|
|**TrackerLogDirectory**|Parámetro **string** opcional.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)
