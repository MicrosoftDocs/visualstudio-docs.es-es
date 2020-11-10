---
title: LC (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea LC para encapsular LC.exe, que genera un archivo .license a partir de un archivo .licx.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c996d5a8d1d4bf296a395bfb64ead6eba1bb01
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903577"
---
# <a name="lc-task"></a>LC (tarea)

Incluye *LC.exe* , que genera un archivo *.license* a partir de un archivo *.licx*. Para obtener más información sobre *LC.exe* , vea [Lc.exe (Compilador de licencias)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea `LC`.

|Parámetro|Descripción|
|---------------|-----------------|
|`LicenseTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo ejecutable para el que se generan los archivos *.licenses*.|
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Suprime la presentación de la portada de inicio de Microsoft.|
|`OutputDirectory`|Parámetro `String` opcional.<br /><br /> Especifica el directorio en el que se colocan los archivos *.licenses* de salida.|
|`OutputLicense`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre de los archivos *.licenses*. Si no especifica un nombre, se usa el nombre del archivo *.licx* y el archivo *.licenses* se coloca en el directorio que contiene el archivo *.licx*.|
|`ReferencedAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los componentes a los que se hace referencia que se van a cargar al generar el archivo *.license*.|
|`SdkToolsPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a las herramientas del SDK, como *resgen.exe*.|
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los elementos que contienen los componentes con licencia que se van a incluir en el archivo *.licenses*. Para obtener más información, consulte la documentación sobre el modificador `/complist` en [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

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
