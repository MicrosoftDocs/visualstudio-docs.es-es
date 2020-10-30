---
title: Tarea GetOutputFileName | Microsoft Docs
description: Use la tarea asistente GetOutputFileName de MSBuild para especificar las opciones del nombre de archivo de salida para cl.exe y otras herramientas.
ms.custom: SEO-VS-2020
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
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436791"
---
# <a name="getoutputfilename-task"></a>Tarea GetOutputFileName

Tarea asistente para obtener el nombre de archivo de salida para cl y otras herramientas, lo que permite especificar solo el directorio de salida, el nombre de archivo completo o nada.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **GetOutputFileName** .

|Parámetro|Descripción|
|---------------|-----------------|
|**OutputExtension**|Parámetro obligatorio de tipo **String** .|
|**OutputFile**|Parámetro de salida **string** opcional.|
|**OutputPath**|Parámetro **string** opcional.|
|**SourceFile**|Parámetro obligatorio de tipo **String** .|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)
