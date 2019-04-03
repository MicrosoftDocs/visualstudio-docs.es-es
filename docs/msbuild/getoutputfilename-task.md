---
title: Tarea GetOutputFileName | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6298a512a1848622bf854d6d9ee9084309a0b4f
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514985"
---
# <a name="getoutputfilename-task"></a>Tarea GetOutputFileName

Tarea asistente para obtener el nombre de archivo de salida para cl y otras herramientas, lo que permite especificar solo el directorio de salida, el nombre de archivo completo o nada.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **GetOutputFileName**.

|Parámetro|Descripción|
|---------------|-----------------|
|**OutputExtension**|Parámetro obligatorio de tipo **String**.|
|**OutputFile**|Parámetro de salida **string** opcional.|
|**OutputPath**|Parámetro **string** opcional.|
|**SourceFile**|Parámetro obligatorio de tipo **String**.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)