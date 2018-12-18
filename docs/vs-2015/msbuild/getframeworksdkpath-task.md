---
title: Tarea GetFrameworkSdkPath | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ca047d35ec914833d2044cb2ae9fd4f7cf322a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301787"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Recupera la ruta de acceso a [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
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
 En el ejemplo siguiente se usa la tarea `GetFrameworkSdkPath` para almacenar la ruta de acceso a [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] en la propiedad `SdkPath`.  
  
```  
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



