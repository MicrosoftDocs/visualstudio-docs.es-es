---
title: "UidManager (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "comprobar UID al localizar elementos XAML [WPF MSBuild]"
  - "localizar elementos XAML [WPF MSBuild], administrar UID"
  - "administrar UID al localizar elementos XAML [WPF MSBuild]"
  - "UidManager (tarea) [WPF MSBuild]"
  - "UidManager (tarea) [WPF MSBuild], parámetros"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UidManager (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> comprueba, actualiza o quita identificadores únicos \(UID\) para buscar todos los elementos de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] incluidos en los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de código fuente.  
  
## Parámetros de la tarea  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`IntermediateDirectory`|Parámetro opcional de tipo **String**.<br /><br /> Especifica el directorio que se utiliza para hacer un copia de seguridad de los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de código fuente que especifica el parámetro **MarkupFiles**.|  
|`MarkupFiles`|Parámetro obligatorio de tipo **ITaskItem\[\]**.<br /><br /> Especifica los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de código fuente que se van a incluir para los procesos de comprobación, actualización o eliminación del UID.|  
|`Task`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la tarea de administración del UID que desee realizar.  Las opciones válidas son **Activar**, **Actualizar** o **Quitar**.|  
  
## Ejemplo  
 En el siguiente ejemplo, se usa la tarea <xref:Microsoft.Build.Tasks.Windows.UidManager> para comprobar que los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de código fuente especificados contienen elementos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] que tienen los UID apropiados.  
  
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
  
## Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Cómo: Localizar una aplicación](../Topic/How%20to:%20Localize%20an%20Application.md)