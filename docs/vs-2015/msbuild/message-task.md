---
title: Message (Tarea) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7993fe70c52cfd0694bd50d873425eda82c0a7c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566009"
---
# <a name="message-task"></a>Message (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [tarea Message](https://docs.microsoft.com/visualstudio/msbuild/message-task).  
  
  
Registra un mensaje durante una compilación.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Message`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Importance`|Parámetro `String` opcional.<br /><br /> Especifica la importancia del mensaje. Este parámetro puede tener un valor de `high`, `normal` o `low`. El valor predeterminado es `normal`.|  
|`Text`|Parámetro `String` opcional.<br /><br /> El texto del error que se va a registrar.|  
  
## <a name="remarks"></a>Comentarios  
 La tarea `Message` permite a los proyectos de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] enviar mensajes a los registradores en etapas diferentes del proceso de compilación.  
  
 Si el parámetro `Condition` se evalúa como `true`, se registrará el valor del parámetro `Text` y la compilación seguirá ejecutándose. Si no existe un parámetro `Condition`, se registra el texto del mensaje. Para obtener más información sobre el registro, consulte [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 De forma predeterminada, el mensaje se envía al registrador de la consola de MSBuild. Esto se puede cambiar si se modifica el parámetro <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. El registrador interpreta el parámetro `Importance`.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código registra mensajes para todos los registradores registrados.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)



