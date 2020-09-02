---
title: GenerateTemporaryTargetAssembly (Tarea) | Microsoft Docs
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
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ce412fdeb8d466708f3231cba14718d13720c69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676638"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> genera un ensamblado si al menos una página de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] del proyecto hace referencia a un tipo declarado localmente en ese proyecto. El ensamblado generado se quita una vez completado el proceso de compilación, o si este no se produce.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AssemblyName`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el nombre corto del ensamblado que se genera para un proyecto y que también es el nombre del ensamblado de destino que se genera temporalmente. Por ejemplo, si un proyecto genera un archivo ejecutable de [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] con el nombre **WinExeAssembly.exe**, el parámetro **AssemblyName** tiene un valor de **WinExeAssembly**.|  
|`CompileTargetName`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el nombre del destino de [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] que se usa para generar ensamblados a partir de archivos de código fuente. El valor típico de **CompileTargetName** es **CoreCompile**.|  
|`CompileTypeName`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el tipo de compilación que realiza el destino especificado por el parámetro **CompileTargetName**. Para el destino **CoreCompile**, este valor es **Compile**.|  
|`CurrentProject`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso completa del archivo de proyecto de [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] para el proyecto que requiere un ensamblado de destino temporal.|  
|`GeneratedCodeFiles`|Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica la lista de archivos de código administrado específicos del lenguaje y generados por la tarea [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md).|  
|`IntermediateOutputPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el directorio en el que se genera el ensamblado de destino temporal.|  
|`MSBuildBinPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ubicación de **MSBuild.exe**, necesario para compilar el ensamblado de destino temporal.|  
|`ReferencePath`|Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica una lista de ensamblados, por ruta de acceso y nombre de archivo, a los que hacen referencia los tipos compilados en el ensamblado de destino temporal.|  
|`ReferencePathTypeName`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el parámetro que usa el parámetro de destino de compilación (**CompileTargetName**) que especifica la lista de referencias del ensamblado (**ReferencePath**). El valor correcto es **ReferencePath**.|  
  
## <a name="remarks"></a>Comentarios  
 El primer paso de compilación de marcado, que ejecuta [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compila los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en formato binario. Por consiguiente, el compilador necesita una lista de los ensamblados a los que se hace referencia y que contienen los tipos que usan los archivos de [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]. Sin embargo, si un archivo [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] usa un tipo definido en el mismo proyecto, no se crea ningún ensamblado correspondiente para ese proyecto hasta que se compile el proyecto. Por consiguiente, no se puede proporcionar ninguna referencia del ensamblado durante el primer paso de compilación de marcado.  
  
 En su lugar, **MarkupCompilePass1** aplaza la conversión de los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] que contienen referencias a los tipos del mismo proyecto a un segundo paso de compilación de marcado, que ejecuta [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Antes de que se ejecute **MarkupCompilePass2**, se genera un ensamblado temporal. Este ensamblado contiene los tipos que usan los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] cuyo paso de compilación de marcado se aplazó. Cuando se ejecuta **MarkupCompilePass2** se le proporciona una referencia al ensamblado generado para permitir que los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de la compilación aplazada se conviertan al formato binario.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera un ensamblado temporal porque `Page1.xaml` contiene una referencia a un tipo que está en el mismo proyecto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Información general sobre las aplicaciones de explorador XAML de WPF](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
