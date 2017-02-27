---
title: "ResolveKeySource (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveKeySource (tarea)"
  - "ResolveKeySource (tarea) [MSBuild]"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ResolveKeySource (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina el origen de la clave de nombre seguro.  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveKeySource`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Parámetro `Int32` opcional.<br /><br /> Obtiene o establece el período de tiempo, en segundos, durante el cual se muestra el mensaje de la cuenta atrás.|  
|`AutoClosePasswordPromptTimeout`|Parámetro `Int32` opcional.<br /><br /> Obtiene o establece el tiempo de espera, en segundos, hasta que se cierra el cuadro de diálogo en el que se solicita la contraseña.|  
|`CertificateFile`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la ruta de acceso al archivo de certificado.|  
|`CertificateThumbprint`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la huella digital de un certificado.|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la ruta de acceso al archivo de clave.|  
|`ResolvedKeyContainer`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece el contenedor de claves resuelto.|  
|`ResolvedKeyFile`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece el archivo de clave resuelto.|  
|`ResolvedThumbprint`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece la huella digital resuelta de un certificado.|  
|`ShowImportDialogDespitePreviousFailures`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, muestre el cuadro de diálogo de importación a pesar de los fracasos anteriores.|  
|`SuppressAutoClosePasswordPrompt`|Parámetro `Boolean` opcional.<br /><br /> Obtiene o establece un valor booleano que especifica si el cuadro de diálogo de solicitud de contraseña no debe cerrarse automáticamente.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)