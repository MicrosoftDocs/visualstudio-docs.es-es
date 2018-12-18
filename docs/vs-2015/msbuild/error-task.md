---
title: Error (tarea) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff957a54c27c4ae4860e31e4fb7001b7f831ab3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212724"
---
# <a name="error-task"></a>Error (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Detiene una compilación y registra un error basándose en una instrucción condicional evaluada.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Error`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Code`|Parámetro `String` opcional.<br /><br /> Código de error que se debe asociar con el error.|  
|`File`|Parámetro `String` opcional.<br /><br /> El nombre del archivo que contiene el error. Si no se proporciona ningún nombre de archivo, se utilizará el archivo que contiene la tarea Error.|  
|`HelpKeyword`|Parámetro `String` opcional.<br /><br /> Palabra clave Ayuda que se debe asociar con el error.|  
|`Text`|Parámetro `String` opcional.<br /><br /> El texto de error que registra [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] si el parámetro `Condition` se evalúa como `true`.|  
  
## <a name="remarks"></a>Comentarios  
 La tarea `Error` permite que los proyectos [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] emitan el texto de error a los registradores y detengan la ejecución de la compilación.  
  
 Si el parámetro `Condition` se evalúa como `true`, la compilación se detiene y se registra un error. Si no existe ningún parámetro `Condition`, el error se registra y se detiene la ejecución de la compilación. Para obtener más información sobre el registro, consulte [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se comprueba que se hayan establecido todas las propiedades necesarias. Si no están establecidas, el proyecto genera un evento de error y registra el valor del parámetro `Text` de la tarea `Error`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)



