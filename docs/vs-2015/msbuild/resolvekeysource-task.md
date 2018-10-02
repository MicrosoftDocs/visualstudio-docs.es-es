---
title: Tarea ResolveKeySource | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a51b9b07be214a6713da4d9d6f9ccf99814b270f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580694"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ResolveKeySource (tarea)](https://docs.microsoft.com/visualstudio/msbuild/resolvekeysource-task).  
  
  
Determina el origen de la clave de nombre seguro.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveKeySource`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Parámetro `Int32` opcional.<br /><br /> Obtiene o establece la cantidad de tiempo, en segundos, que se mostrará el mensaje de cuenta atrás.|  
|`AutoClosePasswordPromptTimeout`|Parámetro `Int32` opcional.<br /><br /> Obtiene o establece la cantidad de tiempo, en segundos, que se esperará antes de cerrar el cuadro de diálogo de solicitud de contraseña.|  
|`CertificateFile`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la ruta de acceso del archivo de certificado.|  
|`CertificateThumbprint`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la huella digital del certificado.|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la ruta de acceso del archivo de claves.|  
|`ResolvedKeyContainer`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece el contenedor de clave resuelta.|  
|`ResolvedKeyFile`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece el archivo de clave resuelta.|  
|`ResolvedThumbprint`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece la huella digital resuelta del certificado.|  
|`ShowImportDialogDespitePreviousFailures`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se muestra el cuadro de diálogo de importación a pesar de los errores anteriores.|  
|`SuppressAutoClosePasswordPrompt`|Parámetro `Boolean` opcional.<br /><br /> Obtiene o establece un valor booleano que especifica si el cuadro de diálogo de contraseña no se debe cerrar automáticamente.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



