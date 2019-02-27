---
title: Tarea GetFrameworkPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b836a0fef26f34e83f7238ebe4f6c64731b84257
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610364"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath (tarea)
Recupera la ruta de acceso a los ensamblados de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

## <a name="task-parameters"></a>Parámetros de tareas
En la siguiente tabla se describen los parámetros de la tarea `GetFrameworkPath` .

|Parámetro|Descripción|
|---------------|-----------------|
|`FrameworkVersion11Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 1.1 de Framework, si está presente. De lo contrario, devuelve `null`.|
|`FrameworkVersion20Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 2.0 de Framework, si está presente. De lo contrario, devuelve `null`.|
|`FrameworkVersion30Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 3.0 de Framework, si está presente. De lo contrario, devuelve `null`.|
|`FrameworkVersion35Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 3.5 de Framework, si está presente. De lo contrario, devuelve `null`.|
|`FrameworkVersion40Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 4.0 de Framework, si está presente. De lo contrario, devuelve `null`.|
|`Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de Framework más recientes, si alguno está disponible. De lo contrario, devuelve `null`.|

## <a name="remarks"></a>Comentarios
Si están instaladas varias versiones de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], esta tarea devuelve la versión en la que puede ejecutarse [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se usa la tarea `GetFrameworkPath` para almacenar la ruta de acceso a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en la propiedad `FrameworkPath`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
