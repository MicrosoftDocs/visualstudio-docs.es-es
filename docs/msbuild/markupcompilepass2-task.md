---
title: MarkupCompilePass2 (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 360a6c4d3e389583eece1adcc915f26091283653
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942392"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 (tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> realiza una compilación de marcado de segundo paso en archivos de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] que hacen referencia a los tipos del mismo proyecto.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Descripción |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parámetro **Boolean** opcional.<br /><br /> Especifica si la tarea se va a ejecutar en un <xref:System.AppDomain> independiente. Si este parámetro devuelve el valor **false**, la tarea se ejecuta en el mismo <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] y su ejecución es más rápida. Si el parámetro devuelve el valor **true**, la tarea se ejecuta en otro <xref:System.AppDomain> que está aislado de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] y su ejecución es más lenta. |
| `AssembliesGeneratedDuringBuild` | Parámetro **String[]** opcional.<br /><br /> Especifica referencias a los ensamblados que cambian durante el proceso de compilación. Por ejemplo, una solución de Visual Studio puede contener un proyecto que haga referencia al resultado compilado de otro proyecto. En este caso, el resultado compilado del segundo proyecto se puede agregar a **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: **AssembliesGeneratedDuringBuild** debe contener referencias al conjunto completo de ensamblados que genera una solución de compilación. |
| `AssemblyName` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el nombre corto del ensamblado que se genera para un proyecto. Por ejemplo, si un proyecto genera un archivo ejecutable de [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] con el nombre *WinExeAssembly.exe*, el parámetro **AssemblyName** tiene el valor **WinExeAssembly**. |
| `GeneratedBaml` | Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Contiene la lista de archivos generados en formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `KnownReferencePaths` | Parámetro **String[]** opcional.<br /><br /> Especifica referencias a los ensamblados que no cambian nunca durante el proceso de compilación. Incluye los ensamblados que se encuentran en [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], en un directorio de instalación de [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)], etc. |
| `Language` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el lenguaje administrado que el compilador admite. Las opciones válidas son **C#**, **VB**, **JScript** y **C++**. |
| `LocalizationDirectivesToLocFile` | Parámetro **String** opcional.<br /><br /> Especifica cómo generar la información de localización para cada archivo de origen de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Las opciones válidas son **None**, **CommentsOnly** y **All**. |
| `OutputPath` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el directorio en el que se generan los archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputType` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el tipo de ensamblado que genera un proyecto. Las opciones válidas son **winexe**, **exe**, **library** y **netmodule**. |
| `References` | Parámetro opcional de tipo **ITaskItem[]**.<br /><br /> Especifica la lista de referencias de los archivos a los ensamblados que contienen los tipos que se usan en los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Una referencia es para el ensamblado que se ha generado mediante la tarea <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, que debe ejecutarse antes de la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Parámetro **String** opcional.<br /><br /> Especifica el espacio de nombres de la raíz de las clases que están dentro del proyecto. **RootNamespace** también se usa como espacio de nombres predeterminado de un archivo de código administrado generado cuando el archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] correspondiente no incluye el atributo `x:Class`. |
| `XAMLDebuggingInformation` | Parámetro **Boolean** opcional.<br /><br /> Si el valor es **true**, se genera información de diagnóstico y se incluye en el archivo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilado como ayuda para la depuración. |

## <a name="remarks"></a>Comentarios

Antes de ejecutar **MarkupCompilePass2**, debe generar un ensamblado temporal con los tipos que usan los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] cuyo paso de compilación de marcado se aplazó. Para generar el ensamblado temporal, ejecute la tarea **GenerateTemporaryTargetAssembly**.

Cuando se ejecuta <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>, se le proporciona una referencia al ensamblado temporal generado. De esta manera, se pueden compilar en formato binario los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] cuya compilación se ha aplazado en el primer paso de compilación de marcado.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> para realizar una compilación de segundo paso.

```xml
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

## <a name="see-also"></a>Vea también

[Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)  
[Referencia de tareas de MSBuild para WPF](../msbuild/wpf-msbuild-task-reference.md)  
[Referencia de MSBuild](../msbuild/msbuild-reference.md)  
[Referencia de tareas de MSBuild](../msbuild/msbuild-task-reference.md)  
[Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[Información general sobre las aplicaciones de explorador XAML de WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)