---
title: MarkupCompilePass1 (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea MarkupCompilePass1 para convertir archivos de proyectos XAML no localizables en formato binario compilado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89d67c083c9e40710e79568c12684ab54653a5be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966206"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> convierte archivos de proyecto de XAML no localizables en un formato binario compilado.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Description |
| - | - |
| `AllGeneratedFiles` | Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Contiene una lista completa de archivos que se generan mediante la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parámetro **Boolean** opcional.<br /><br /> Especifica si la tarea se va a ejecutar en un <xref:System.AppDomain> independiente. Si este parámetro devuelve el valor **false**, la tarea se ejecuta en el mismo <xref:System.AppDomain> que MSBuild y su ejecución es más rápida. Si el parámetro devuelve el valor **true**, la tarea se ejecuta en otro <xref:System.AppDomain> que está aislado de MSBuild y su ejecución es más lenta. |
| `ApplicationMarkup` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica el nombre del archivo XAML de la definición de aplicación. |
| `AssembliesGeneratedDuringBuild` | Parámetro **String[]** opcional.<br /><br /> Especifica referencias a los ensamblados que cambian durante el proceso de compilación. Por ejemplo, una solución de Visual Studio puede contener un proyecto que haga referencia al resultado compilado de otro proyecto. En este caso, el resultado compilado del segundo proyecto se puede agregar al parámetro **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: El parámetro **AssembliesGeneratedDuringBuild** debe contener referencias al conjunto completo de ensamblados que genera una solución de compilación. |
| `AssemblyName` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el nombre corto del ensamblado que se genera para un proyecto. Por ejemplo, si un proyecto genera un archivo ejecutable de Windows con el nombre *WinExeAssembly.exe*, el parámetro **AssemblyName** tiene el valor **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Parámetro **String** opcional.<br /><br /> Especifica el token de la clave pública del ensamblado. |
| `AssemblyVersion` | Parámetro **String** opcional.<br /><br /> Especifica el número de versión del ensamblado. |
| `ContentFiles` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica la lista de archivos de contenido separados. |
| `DefineConstants` | Parámetro **String** opcional.<br /><br /> Especifica que se mantiene el valor actual de **DefineConstants**, lo que afecta a la generación del ensamblado de destino. Si se cambia este parámetro, puede que cambie la API pública del ensamblado de destino y se vea afectada la compilación de los archivos XAML que hacen referencia a tipos locales. |
| `ExtraBuildControlFiles` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica una lista de los archivos que controlan si se va a desencadenar una recompilación cuando se vuelva a ejecutar la tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>; se desencadena una recompilación si cambia alguno de estos archivos. |
| `GeneratedBamlFiles` | Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Contiene la lista de archivos generados en formato binario XAML. |
| `GeneratedCodeFiles` | Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Contiene la lista de los archivos de código administrado generados. |
| `GeneratedLocalizationFiles` | Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Contiene la lista de los archivos de localización que se generaron por cada archivo XAML localizable. |
| `HostInBrowser` | Parámetro **String** opcional.<br /><br /> Especifica si el ensamblado generado es XAML  Browser Application (XBAP). Las opciones válidas son **true** y **false**. Si es **true**, se genera código para admitir el hospedaje en el explorador. |
| `KnownReferencePaths` | Parámetro **String[]** opcional.<br /><br /> Especifica referencias a los ensamblados que no cambian durante el proceso de compilación. Incluye los ensamblados que se encuentran en la caché global de ensamblados, en un directorio de instalación de .NET, etc. |
| `Language` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el lenguaje administrado que el compilador admite. Las opciones válidas son **C#**, **VB**, **JScript** y **C++**. |
| `LanguageSourceExtension` | Parámetro **String** opcional.<br /><br /> Especifica la extensión que se anexa a la extensión del archivo de código administrado generado:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Si el valor del parámetro **LanguageSourceExtension** no se establece en un valor concreto, se utiliza la extensión de nombre de archivo de origen predeterminada de un lenguaje: *.vb* para Visual Basic, *.csharp* para C#. |
| `LocalizationDirectivesToLocFile` | Parámetro **String** opcional.<br /><br /> Especifica cómo generar la información de localización para cada archivo de origen de XAML. Las opciones válidas son **None**, **CommentsOnly** y **All**. |
| `OutputPath` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el directorio en el que se generan los archivos de código administrado y los archivos de formato binario XAML. |
| `OutputType` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el tipo de ensamblado que genera un proyecto. Las opciones válidas son **winexe**, **exe**, **library** y **netmodule**. |
| `PageMarkup` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica una lista de los archivos XAML que se van a procesar. |
| `References` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica la lista de referencias de los archivos a los ensamblados que contienen los tipos que se usan en los archivos XAML. |
| `RequirePass2ForMainAssembly` | Parámetro de salida opcional de tipo **Boolean**.<br /><br /> Indica si el proyecto contiene archivos XAML no localizables que hagan referencia a tipos locales insertados en el ensamblado principal. |
| `RequirePass2ForSatelliteAssembly` | Parámetro de salida opcional de tipo **Boolean**.<br /><br /> Indica si el proyecto contiene archivos XAML localizables que hagan referencia a tipos locales insertados en el ensamblado principal. |
| `RootNamespace` | Parámetro **String** opcional.<br /><br /> Especifica el espacio de nombres de la raíz de las clases que están dentro del proyecto. **RootNamespace** también se usa como espacio de nombres predeterminado de un archivo de código administrado generado cuando el archivo XAML correspondiente no incluye el atributo `x:Class`. |
| `SourceCodeFiles` | Parámetro opcional de tipo **ITaskItem[]** .<br /><br /> Especifica la lista de archivos de código del proyecto actual. La lista no incluye los archivos de código administrado específicos del lenguaje que se hayan generado. |
| `UICulture` | Parámetro **String** opcional.<br /><br /> Especifica el ensamblado satélite de la referencia cultural de la interfaz de usuario en la que se insertan los archivos de formato binario XAML generados. Si no se establece el valor de **UICulture**, los archivos de formato binario XAML generados se insertan en el ensamblado principal. |
| `XAMLDebuggingInformation` | Parámetro **Boolean** opcional.<br /><br /> Si el valor es **true**, se genera información de diagnóstico y se incluye en el archivo XAML compilado como ayuda para la depuración. |

## <a name="remarks"></a>Comentarios

La tarea <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> compila normalmente XAML en formato binario y genera archivos de código. Si un archivo XAML contiene referencias a tipos definidos en el mismo proyecto, **MarkupCompilePass1** aplaza su compilación en formato binario a un segundo paso de compilación de marcado (**MarkupCompilePass2**). Estos archivos se deben compilar de forma aplazada porque deben esperar hasta que se compilen los tipos definidos localmente a los que se hace referencia. En cambio, si un archivo XAML tiene un atributo `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> genera el archivo de código específico del lenguaje para él.

Un archivo XAML es adaptable si contiene elementos que usan el atributo `x:Uid`:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Un archivo XAML hace referencia a un tipo definido localmente cuando declara un espacio de nombres XML que use el valor `clr-namespace` para hacer referencia a un espacio de nombres del proyecto actual:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Si un archivo XAML es localizable o hace referencia a un tipo definido localmente, se necesita un segundo paso de compilación de marcado, el cual requiere la ejecución de [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) y, a continuación, de [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo convertir tres archivos *Page* de XAML en archivos de formato binarios. *Page1* contiene una referencia a un tipo, `Class1`, que está en el espacio de nombres raíz del proyecto y, por tanto, no se convierte en archivos de formato binarios en este paso de compilación de marcado. En su lugar, se ejecuta [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) y, después, [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)
- [Referencia de tareas de MSBuild para WPF](../msbuild/wpf-msbuild-task-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de tareas de MSBuild](../msbuild/msbuild-task-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Información general sobre las aplicaciones de explorador XAML de WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)