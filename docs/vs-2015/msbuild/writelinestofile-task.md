---
title: WriteLinesToFile (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b25318a9b453ee9f9b05b22e7130555b5a14d556
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760146"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Escribe las rutas de acceso de los elementos especificados en el archivo de texto especificado.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `WriteLinestoFile`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`File`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo en el que se escriben los elementos.|  
|`Lines`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los elementos que se van a escribir en el archivo.|  
|`Overwrite`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea sobrescribe cualquier contenido existente en el archivo.|  
|`Encoding`|Parámetro `String` opcional.<br /><br /> Selecciona la codificación de caracteres, por ejemplo, "Unicode".  Vea también <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Comentarios  
 Si `Overwrite` es `true`, crea un archivo, escribe el contenido en el archivo y después lo cierra. Si el archivo de destino ya existe, se sobrescribe. Si `Overwrite` es `false`, anexa el contenido al archivo y crea el archivo de destino si aún no existe.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa la tarea `WriteLinesToFile` para escribir las rutas de acceso de los elementos de la colección de elementos `MyItems` en el archivo especificado por la colección de elementos `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
