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
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593296"
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
