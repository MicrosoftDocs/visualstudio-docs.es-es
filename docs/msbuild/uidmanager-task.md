---
title: UidManager (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo la tarea UidManager de MSBuild comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos XAML en los archivos XAML de origen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6287abee811d406ef7aafa5ce3cc3dc62624b0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902621"
---
# <a name="uidmanager-task"></a>UidManager (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos XAML incluidos en los archivos XAML de origen.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Description |
|-------------------------| - |
| `IntermediateDirectory` | Parámetro **String** opcional.<br /><br /> Especifica el directorio que se utiliza para hacer una copia de seguridad de los archivos XAML de origen que especifica el parámetro **MarkupFiles**. |
| `MarkupFiles` | Parámetro obligatorio de tipo **ITaskItem[]** .<br /><br /> Especifica los archivos XAML de origen que se van a incluir para los procesos de comprobación, actualización o eliminación del UID. |
| `Task` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la tarea de administración del UID que desea realizar. Las opciones válidas son **Activar**, **Actualizar** o **Quitar**. |

## <a name="example"></a>Ejemplo

 En el siguiente ejemplo, se usa la tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> para comprobar que los archivos XAML de origen especificados contienen elementos XAML que tienen los UID apropiados.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)
- [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Procedimiento: Localizar una aplicación](/dotnet/framework/wpf/advanced/how-to-localize-an-application)