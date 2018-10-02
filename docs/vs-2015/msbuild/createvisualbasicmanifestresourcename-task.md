---
title: CreateVisualBasicManifestResourceName (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a1588ce170ad9e833f7378a837e4e75853c19ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577736"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CreateVisualBasicManifestResourceName (tarea)](https://docs.microsoft.com/visualstudio/msbuild/createvisualbasicmanifestresourcename-task).  
  
  
Crea el nombre de un manifiesto de estilo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a partir del nombre de un archivo .resx especificado u otro recurso.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de [CreateVisualBasicManifestResourceName (Tarea)](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ManifestResourceNames`|Parámetro de solo lectura de salida <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Los nombres de manifiesto resultantes.|  
|`ResourceFiles`|Parámetro `String` requerido.<br /><br /> Nombre del archivo de recursos a partir del que se va a crear el nombre de manifiesto [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`RootNamespace`|Parámetro `String` opcional.<br /><br /> Espacio de nombres raíz del archivo de recursos, que se toma normalmente del archivo de proyecto. Puede ser `null`.|  
|`PrependCultureAsDirectory`|Parámetro `Boolean` opcional.<br /><br /> Si el valor es `true`, el nombre de la referencia cultural se agrega como nombre de directorio inmediatamente antes del nombre de recurso del manifiesto. El valor predeterminado es `true`.|  
|`ResourceFilesWithManifestResourceNames`|Parámetro de salida de solo lectura `String` opcional.<br /><br /> Devuelve el nombre del archivo de recursos que ahora incluye el nombre de recurso del manifiesto.|  
  
## <a name="remarks"></a>Comentarios  
 [CreateVisualBasicManifestResourceName (Tarea)](../msbuild/createvisualbasicmanifestresourcename-task.md) determina el nombre de recurso del manifiesto apropiado que se va a asignar a un archivo .resx especificado o a otro archivo de recursos. La tarea proporciona un nombre lógico a un archivo de recursos y, a continuación, lo asocia a un parámetro de salida como metadatos.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



