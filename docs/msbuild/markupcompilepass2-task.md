---
title: "MarkupCompilePass2 (Tarea) | Microsoft Docs"
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
  - "MarkupCompilePass2 (tarea) [WPF MSBuild]"
  - "MarkupCompilePass2 (tarea) [WPF MSBuild], parámetros"
  - "realizar una compilación de marcado de segundo paso [WPF MSBuild], MarkupCompilePass2 (tarea)"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass2 (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> realiza una compilación de marcado de segundo paso en los archivos [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] que hacen referencia a tipos del mismo proyecto.  
  
## Parámetros de la tarea  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Parámetro opcional de tipo **Boolean**.<br /><br /> Especifica si la tarea debe ejecutarse en un <xref:System.AppDomain> independiente.  Si este parámetro devuelve el valor **false**, la tarea se ejecuta en el mismo <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] y lo hace más rápido.  Si el parámetro devuelve el valor **true**, la tarea se ejecuta en otro <xref:System.AppDomain> que está aislado de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] y su ejecución es más lenta.|  
|`AssembliesGeneratedDuringBuild`|Parámetro opcional de tipo **String\[\]**.<br /><br /> Especifica referencias a los ensamblados que cambian durante el proceso de compilación.  Por ejemplo, una solución de [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] puede contener un proyecto que haga referencia al resultado compilado de otro proyecto.  En este caso, el resultado compilado del segundo proyecto se puede agregar a **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: **AssembliesGeneratedDuringBuild** debe contener referencias al conjunto completo de ensamblados que genere una solución de compilación.|  
|`AssemblyName`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el nombre corto del ensamblado que se genera para un proyecto.  Por ejemplo, si un proyecto genera un archivo ejecutable de [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] con el nombre **WinExeAssembly.exe**, el parámetro **AssemblyName** tiene un valor de **WinExeAssembly**.|  
|`GeneratedBaml`|Parámetro de salida opcional de tipo **ITaskItem\[\]**.<br /><br /> Contiene la lista de archivos generados en formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`KnownReferencePaths`|Parámetro opcional de tipo **String\[\]**.<br /><br /> Especifica las referencias a los ensamblados que no cambian nunca durante el proceso de compilación.  Incluye los ensamblados que se encuentran en la [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], en un directorio de instalación de [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)], etc.|  
|`Language`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el lenguaje administrado que el compilador admite.  las opciones válidas son **C\#**, **VB**, **JScript**, y **C\+\+**.|  
|`LocalizationDirectivesToLocFile`|Parámetro opcional de tipo **String**.<br /><br /> Especifica cómo generar la información de localización para cada archivo de código fuente [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Las opciones válidas son **None**, **CommentsOnly** y **All**.|  
|`OutputPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el directorio en el que se crean los archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] generados.|  
|`OutputType`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el tipo de ensamblado que un proyecto genera.  Las opciones válidas son **winexe**, **exe**, **library** y **netmodule**.|  
|`References`|Parámetro opcional de tipo **ITaskItem\[\]**.<br /><br /> Especifica la lista de referencias de los archivos a los ensamblados que contienen los tipos que se usan en los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Se hace una referencia al ensamblado generado por la tarea <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, que se debe ejecutar antes que la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>.|  
|`RootNamespace`|Parámetro opcional de tipo **String**.<br /><br /> Especifica el espacio de nombres de la raíz de las clases que están dentro del proyecto.  **RootNamespace** también se usa como espacio de nombres predeterminado de un archivo de código administrado generado cuando el archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] correspondiente no incluye el atributo `x:Class`.|  
|`XAMLDebuggingInformation`|Parámetro opcional de tipo **Boolean**.<br /><br /> Si el valor es **true**, se genera información de diagnóstico y se incluye en el archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilado como ayuda para la depuración.|  
  
## Comentarios  
 Antes de ejecutar **MarkupCompilePass2**, debe generar un ensamblado temporal con los tipos que usan los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] cuyo paso de compilación de marcado se aplazó.  Para generar el ensamblado temporal, ejecute la tarea **GenerateTemporaryTargetAssembly**.  
  
 Cuando se ejecuta <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>, se le proporciona una referencia al ensamblado temporal generado. De esta forma, se pueden compilar en formato binario los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] cuya compilación se aplazó en el primer paso de compilación de marcado.  
  
## Ejemplo  
 En el ejemplo siguiente, se muestra cómo usar la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> para realizar una compilación de segundo paso.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Información general sobre las aplicaciones de explorador XAML de WPF](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)