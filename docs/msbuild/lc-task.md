---
title: LC (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa9a210b61a1ba28d2dca2f81184b3d20a91ff7f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638706"
---
# <a name="lc-task"></a>LC (tarea)
Incluye *LC.exe*, que genera un archivo *.license* a partir de un archivo *.licx*. Para obtener más información sobre *LC.exe*, vea [Lc.exe (Compilador de licencias)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parámetros
En la tabla siguiente se describen los parámetros de la tarea `LC`.

|Parámetro|Descripción|
|---------------|-----------------|
|`LicenseTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo ejecutable para el que se generan los archivos *.licenses*.|
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Suprime la presentación de la portada de inicio de Microsoft.|
|`OutputDirectory`|Parámetro `String` opcional.<br /><br /> Especifica el directorio en el que se colocan los archivos *.licenses* de salida.|
|`OutputLicense`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre de los archivos *.licenses*. Si no especifica un nombre, se usa el nombre del archivo *.licx* y el archivo *.licenses* se coloca en el directorio que contiene el archivo *.licx*.|
|`ReferencedAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los componentes a los que se hace referencia que se van a cargar al generar el archivo *.license*.|
|`SdkToolsPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a las herramientas del SDK, tales como *resgen.exe*.|
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los elementos que contienen los componentes con licencia que se van a incluir en el archivo *.licenses*. Para obtener más información, consulte la documentación sobre el modificador `/complist` en [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).|

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Ejemplo
En el siguiente ejemplo se utiliza la tarea `LC` para compilar las licencias.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
