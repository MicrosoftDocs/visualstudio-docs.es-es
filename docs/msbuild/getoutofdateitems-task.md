---
title: Tarea GetOutOfDateItems | Microsoft Docs
description: Use la tarea asistente GetOutOfDateItems de MSBuild para leer y escribir registros de transacciones (TLOG) y devolver conjuntos de elementos que no están actualizados.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436830"
---
# <a name="getoutofdateitems-task"></a>Tarea GetOutOfDateItems

Tarea asistente que lee TLog antiguos, escribe TLog nuevos y devuelve un conjunto de elementos no actualizados.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **GetOutOfDateItems** .

|Parámetro|Descripción|
|---------------|-----------------|
|**CheckForInterdependencies**|Parámetro **bool** opcional.|
|**CommandMetadataName**|Parámetro **string** opcional.|
|**DependenciesMetadataName**|Parámetro **string** opcional.|
|**HasInterdependencies**|Parámetro de salida **bool** opcional.|
|**OutOfDateSources**|Parámetro de salida opcional de tipo **ITaskItem[]** .|
|**OutputsMetadataName**|Parámetro obligatorio de tipo **String** .|
|**Sources**|Parámetro opcional de tipo **ITaskItem[]** .|
|**TLogDirectory**|Parámetro obligatorio de tipo **String** .|
|**TLogNamePrefix**|Parámetro obligatorio de tipo **String** .|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)