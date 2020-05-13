---
title: UidManager (Tarea) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631528"
---
# <a name="uidmanager-task"></a>UidManager (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos XAML incluidos en los archivos XAML de origen.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Descripción |
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
- [Cómo: Localizar una aplicación](/dotnet/framework/wpf/advanced/how-to-localize-an-application)