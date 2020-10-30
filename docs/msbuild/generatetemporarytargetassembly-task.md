---
title: GenerateTemporaryTargetAssembly (Tarea) | Microsoft Docs
description: Use la tarea GenerateTemporaryTargetAssembly de MSBuild para generar un ensamblado si un proyecto hace referencia a un tipo declarado localmente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a100ad8a3be57288e49a858d6f87851269df303
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436756"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> genera un ensamblado si al menos una página de XAML del proyecto hace referencia a un tipo declarado localmente en ese proyecto. El ensamblado generado se quita una vez completado el proceso de compilación, o si este no se produce.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Descripción |
|--------------------------| - |
| `AssemblyName` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica el nombre corto del ensamblado que se genera para un proyecto y que también es el nombre del ensamblado de destino que se genera temporalmente. Por ejemplo, si un proyecto genera un archivo ejecutable de Windows con el nombre *WinExeAssembly.exe* , el parámetro **AssemblyName** tiene un valor de **WinExeAssembly** . |
| `CompileTargetName` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica el nombre del destino de MSBuild que se usa para generar ensamblados a partir de archivos de código fuente. El valor típico de **CompileTargetName** es **CoreCompile** . |
| `CompileTypeName` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica el tipo de compilación que realiza el destino especificado por el parámetro **CompileTargetName** . Para el destino **CoreCompile** , este valor es **Compile** . |
| `CurrentProject` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica la ruta de acceso completa del archivo de proyecto de MSBuild para el proyecto que requiere un ensamblado de destino temporal. |
| `GeneratedCodeFiles` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica la lista de archivos de código administrado específicos del lenguaje y generados por la tarea [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md). |
| `IntermediateOutputPath` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica el directorio en el que se genera el ensamblado de destino temporal. |
| `MSBuildBinPath` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica la ubicación de *MSBuild.exe* , necesario para compilar el ensamblado de destino temporal. |
| `ReferencePath` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica una lista de ensamblados, por ruta de acceso y nombre de archivo, a los que hacen referencia los tipos compilados en el ensamblado de destino temporal. |
| `ReferencePathTypeName` | Parámetro obligatorio de tipo **String** .<br /><br /> Especifica el parámetro que usa el parámetro de destino de compilación ( **CompileTargetName** ) que especifica la lista de referencias del ensamblado ( **ReferencePath** ). El valor correcto es **ReferencePath** . |

## <a name="remarks"></a>Observaciones

El primer paso de compilación de marcado, que ejecuta [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compila los archivos XAML en formato binario. Por consiguiente, el compilador necesita una lista de los ensamblados a los que se hace referencia y que contienen los tipos que usan los archivos XAML. Sin embargo, si un archivo XAML usa un tipo definido en el mismo proyecto, no se crea ningún ensamblado correspondiente para ese proyecto hasta que se compile el proyecto. Por consiguiente, no se puede proporcionar ninguna referencia del ensamblado durante el primer paso de compilación de marcado.

En su lugar, **MarkupCompilePass1** aplaza la conversión de los archivos XAML que contienen referencias a los tipos del mismo proyecto a un segundo paso de compilación de marcado, que ejecuta [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Antes de que se ejecute **MarkupCompilePass2** , se genera un ensamblado temporal. Este ensamblado contiene los tipos que usan los archivos XAML cuyo paso de compilación de marcado se aplazó. Cuando se ejecuta **MarkupCompilePass2** se le proporciona una referencia al ensamblado generado para permitir que los archivos XAML de la compilación aplazada se conviertan al formato binario.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un ensamblado temporal porque *Page1.xaml* contiene una referencia a un tipo que está en el mismo proyecto.

```xml
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

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)
- [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Información general sobre las aplicaciones de explorador XAML de WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
