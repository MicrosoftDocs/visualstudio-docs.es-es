---
title: Tarea GetFrameworkSdkPath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 5e17a9753f0855befd3c791cf191b191b1c4662d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (Tarea)
Recupera la ruta de acceso a [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `GetFrameworkSdkPath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Parámetro de salida de solo lectura `String` opcional.<br /><br /> Devuelve la ruta de acceso al SDK de .NET versión 2.0, si está presente. De lo contrario, devuelve `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Parámetro de salida de solo lectura `String` opcional.<br /><br /> Devuelve la ruta de acceso al SDK de .NET versión 3.5, si está presente. De lo contrario, devuelve `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Parámetro de salida de solo lectura `String` opcional.<br /><br /> Devuelve la ruta de acceso al SDK de .NET versión 4.0, si está presente. De lo contrario, devuelve `String.Empty`.|  
|`Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso al SDK de .NET más reciente, si hay alguna versión. De lo contrario, devuelve `String.Empty`.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa la tarea `GetFrameworkSdkPath` para almacenar la ruta de acceso a [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] en la propiedad `SdkPath`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)