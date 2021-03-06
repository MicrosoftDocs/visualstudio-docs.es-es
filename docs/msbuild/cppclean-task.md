---
title: CPPClean (Tarea) | Microsoft Docs
description: En este artículo se describe la tarea CPPClean, que se usa para eliminar los archivos temporales que MSBuild crea cuando se compila un proyecto de C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5b3d48c4556cfd05e5ce3f2b893b3f0e9a07226
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901435"
---
# <a name="cppclean-task"></a>CPPClean (Tarea)

Elimina los archivos temporales que MSBuild crea cuando se compila un proyecto de C++. El proceso que consiste en eliminar archivos de compilación se conoce como *limpieza*.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea **CPPClean**.

|Parámetro|Descripción|
|---------------|-----------------|
|**DeletedFiles**|Parámetro de salida `ITaskItem[]` opcional.<br /><br /> Define una matriz de elementos de archivos de salida de MSBuild que las tareas pueden consumir y emitir.|
|**DoDelete**|Parámetro **Boolean** opcional.<br /><br /> Si `true`, limpie los archivos de compilación temporales.|
|**FilePatternsToDeleteOnClean**|Parámetro `String` requerido.<br /><br /> Especifica una lista delimitada por punto y coma de extensiones de archivo de archivos que se van a limpiar.|
|**FilesExcludedFromClean**|Parámetro `String` opcional.<br /><br /> Especifica una lista delimitada por punto y coma de archivos que no se van a limpiar.|
|**FoldersToClean**|Parámetro `String` requerido.<br /><br /> Especifica una lista delimitada por punto y coma de directorios que se van a limpiar. Puede especificar una ruta de acceso completa o relativa que puede contener el carácter comodín (*).|

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
