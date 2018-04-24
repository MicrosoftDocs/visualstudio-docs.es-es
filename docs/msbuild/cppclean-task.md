---
title: CPPClean (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a871effd2b7560cc34ae8e2a91c0b55f63bcfe44
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="cppclean-task"></a>CPPClean (Tarea)
Elimina los archivos temporales que MSBuild crea cuando se compila un proyecto de Visual C++. El proceso que consiste en eliminar archivos de compilación se conoce como *limpieza*.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **CPPClean**.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|**DeletedFiles**|Parámetro de salida `ITaskItem[]` opcional.<br /><br /> Define una matriz de elementos de archivos de salida de MSBuild que las tareas pueden consumir y emitir.|  
|**DoDelete**|Parámetro **Boolean** opcional.<br /><br /> Si `true`, limpie los archivos de compilación temporales.|  
|**FilePatternsToDeleteOnClean**|Parámetro `String` requerido.<br /><br /> Especifica una lista delimitada por punto y coma de extensiones de archivo de archivos que se van a limpiar.|  
|**FilesExcludedFromClean**|Parámetro `String` opcional.<br /><br /> Especifica una lista delimitada por punto y coma de archivos que no se van a limpiar.|  
|**FoldersToClean**|Parámetro `String` requerido.<br /><br /> Especifica una lista delimitada por punto y coma de directorios que se van a limpiar. Puede especificar una ruta de acceso completa o relativa que puede contener el carácter comodín (**\***).|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)