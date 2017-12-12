---
title: Tarea ResolveKeySource | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: cdbbdd476d37d19be63402b970beef84e9802fb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="resolvekeysource-task"></a>ResolveKeySource (Tarea)
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