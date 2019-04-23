---
title: UidManager (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 497c8f2ff8defd0acdf943f4856f0195e50366ce
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656835"
---
# <a name="uidmanager-task"></a>UidManager (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] incluidos en los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de origen.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`IntermediateDirectory`|Parámetro **String** opcional.<br /><br /> Especifica el directorio que se utiliza para hacer una copia de seguridad de los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de origen que especifica el parámetro **MarkupFiles**.|  
|`MarkupFiles`|Parámetro obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de origen que se van a incluir para los procesos de comprobación, actualización o eliminación del UID.|  
|`Task`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la tarea de administración del UID que desea realizar. Las opciones válidas son **Activar**, **Actualizar** o **Quitar**.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se usa la tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> para comprobar que los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de origen especificados contienen elementos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] que tienen los UID apropiados.  
  
```  
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
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Cómo: Localizar una aplicación](http://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)
