---
title: CreateCSharpManifestResourceName (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1feb8610a7a4d94cc51ef81e2261ff6191fba01c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920955"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName (tarea)
Crea el nombre de un manifiesto de estilo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] a partir del nombre de un archivo *.resx* determinado u otro recurso.  

## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea [CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).  


| Parámetro | Descripción |
| - | - |
| `ManifestResourceNames` | Parámetro de solo lectura de salida <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Los nombres de manifiesto resultantes. |
| `ResourceFiles` | Parámetro `String` requerido.<br /><br /> Nombre del archivo de recursos a partir del que se va a crear el nombre de manifiesto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. |
| `RootNamespace` | Parámetro `String` opcional.<br /><br /> Espacio de nombres raíz del archivo de recursos, que se toma normalmente del archivo de proyecto. Puede ser `null`. |
| `PrependCultureAsDirectory` | Parámetro `Boolean` opcional.<br /><br /> Si el valor es `true`, el nombre de la referencia cultural se agrega como nombre de directorio inmediatamente antes del nombre de recurso del manifiesto. El valor predeterminado es `true`. |
| `ResourceFilesWithManifestResourceNames` | Parámetro de salida de solo lectura `String` opcional.<br /><br /> Devuelve el nombre del archivo de recursos que ahora incluye el nombre de recurso del manifiesto. |

## <a name="remarks"></a>Comentarios  
 [CreateVisualBasicManifestResourceName (Tarea)](../msbuild/createvisualbasicmanifestresourcename-task.md) determina el nombre de recurso del manifiesto apropiado que se va a asignar a un archivo *.resx* especificado o a otro archivo de recursos. La tarea proporciona un nombre lógico a un archivo de recursos y, a continuación, lo asocia a un parámetro de salida como metadatos.  

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  

## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)