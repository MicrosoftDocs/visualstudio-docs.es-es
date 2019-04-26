---
title: Uso de AspNetCompiler (Tarea) para precompilar aplicaciones de ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 90b9111d8d8ae78e5b937942df32fb84c97355fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945432"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler (tarea)
La tarea `AspNetCompiler` contiene *aspnet_compiler.exe*, una utilidad que sirve para precompilar aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

## <a name="task-parameters"></a>Parámetros de tareas
En la siguiente tabla se describen los parámetros de la tarea `AspNetCompiler` .

|Parámetro|Descripción|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, el ensamblado de nombre seguro permitirá llamadores de confianza parcial.|
|`Clean`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, se compilará la aplicación precompilada limpia. Cualquier componente previamente compilado se volverá a compilar. El valor predeterminado es `false`. Este parámetro corresponde al modificador **-c** en *aspnet_compiler.exe*.|
|`Debug`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, se enviará información de depuración (archivo .PDB) durante la compilación. El valor predeterminado es `false`. Este parámetro corresponde al modificador **-d** en *aspnet_compiler.exe*.|
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, el ensamblado no se firma totalmente cuando se crea.|
|`FixedNames`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, a los ensamblados compilados se les darán nombres fijos.|
|`Force`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, la tarea sobrescribirá el directorio de destino si ya existe. El contenido existente se perderá. El valor predeterminado es `false`. Este parámetro corresponde al modificador **-f** en *aspnet_compiler.exe*.|
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica un contenedor de claves de nombre seguro.|
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso física del archivo de clave con nombre seguro.|
|`MetabasePath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta completa de la metabase de IIS de la aplicación. Este parámetro no se puede combinar con los parámetros `VirtualPath` o `PhysicalPath`. Este parámetro corresponde al modificador **-m** en *aspnet_compiler.exe*.|
|`PhysicalPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso física de la aplicación que se va a compilar. Si este parámetro falta, se utiliza la metabase de IIS se utiliza para buscar la aplicación. Este parámetro corresponde al modificador **-p** en *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Parámetro `String` opcional.<br /><br /> Especifica el elemento TargetFrameworkMoniker que indica la versión de .NET Framework de *aspnet_compiler.exe* que se debe usar. Solo acepta los monikers de .NET Framework.|
|`TargetPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso física a la aplicación que se va a compilar. Si no se especifica, la aplicación se vuelve a compilar in situ.|
|`Updateable`|Parámetro `Boolean` opcional.<br /><br /> Si este parámetro es `true`, la aplicación precompilada se podrá actualizar.  El valor predeterminado es `false`. Este parámetro corresponde al modificador **-u** en *aspnet_compiler.exe*.|
|`VirtualPath`|Parámetro `String` opcional.<br /><br /> Ruta de acceso virtual de la aplicación que se va a compilar. Si se especifica `PhysicalPath`, la ruta de acceso física se utiliza para buscar la aplicación. En caso contrario, se utiliza la metabase de IIS y se supone que la aplicación se encuentra en el lugar predeterminado. Este parámetro corresponde al modificador **-v** en *aspnet_compiler.exe*.|

## <a name="remarks"></a>Comentarios
Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Ejemplo
En el siguiente ejemplo de código se utiliza la tarea `AspNetCompiler` para precompilar una aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
* [Tareas](../msbuild/msbuild-tasks.md)
* [Referencia de tareas](../msbuild/msbuild-task-reference.md)
