---
title: CreateVisualBasicManifestResourceName (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 948b27aa9e2b800929d9f507535aee1395d45344
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871231"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName (tarea)
Crea el nombre de un manifiesto de estilo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a partir del nombre de un archivo *.resx* determinado u otro recurso.  

## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de [CreateVisualBasicManifestResourceName (Tarea)](../msbuild/createvisualbasicmanifestresourcename-task.md).  


| Parámetro | Descripción |
| - | - |
| `ManifestResourceNames` | Parámetro de solo lectura de salida <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Los nombres de manifiesto resultantes. |
| `ResourceFiles` | Parámetro `String` requerido.<br /><br /> Nombre del archivo de recursos a partir del que se va a crear el nombre de manifiesto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. |
| `RootNamespace` | Parámetro `String` opcional.<br /><br /> Espacio de nombres raíz del archivo de recursos, que se toma normalmente del archivo de proyecto. Puede ser `null`. |
| `PrependCultureAsDirectory` | Parámetro `Boolean` opcional.<br /><br /> Si el valor es `true`, el nombre de la referencia cultural se agrega como nombre de directorio inmediatamente antes del nombre de recurso del manifiesto. El valor predeterminado es `true`. |
| `ResourceFilesWithManifestResourceNames` | Parámetro de salida de solo lectura `String` opcional.<br /><br /> Devuelve el nombre del archivo de recursos que ahora incluye el nombre de recurso del manifiesto. |

## <a name="remarks"></a>Comentarios  
 [CreateVisualBasicManifestResourceName (Tarea)](../msbuild/createvisualbasicmanifestresourcename-task.md) determina el nombre de recurso del manifiesto apropiado que se va a asignar a un archivo *.resx* especificado o a otro archivo de recursos. La tarea proporciona un nombre lógico a un archivo de recursos y, a continuación, lo asocia a un parámetro de salida como metadatos.  

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  

## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)