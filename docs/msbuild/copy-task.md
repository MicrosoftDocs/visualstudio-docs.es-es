---
title: Copy (tarea) | Microsoft Docs
description: Obtenga información sobre cómo usar la tarea Copy de MSBuild para copiar archivos en una ubicación de archivo o carpeta nueva del sistema de archivos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00544b6d1e797a1fd8a7a197197480cae5620f10
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796234"
---
# <a name="copy-task"></a>Copy (tarea)

Copia los archivos en una nueva ubicación del sistema de archivos.

## <a name="parameters"></a>Parámetros

En la siguiente tabla se describen los parámetros de la tarea `Copy` .

|Parámetro|Descripción|
|---------------|-----------------|
|`CopiedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos que se han copiado correctamente, *incluidos* aquellos que no se han copiado realmente, sino que se han omitido porque ya estaban actualizados y `SkipUnchangedFiles` era `true`.|
|`DestinationFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la lista de archivos en la que se copiarán los archivos de código fuente. Se espera que esta lista sea una asignación unívoca con la lista especificada en el parámetro `SourceFiles`. Es decir, el primer archivo especificado en `SourceFiles` se copiará en la primera ubicación especificada en `DestinationFiles`, etc.|
|`DestinationFolder`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el directorio en el que desea copiar los archivos. Este debe ser un directorio, no un archivo. Si el directorio no existe, se crea automáticamente.|
|`OverwriteReadOnlyFiles`|Parámetro `Boolean` opcional.<br /><br /> Sobrescribe los archivos aunque estén marcados como archivos de solo lectura|
|`Retries`|Parámetro `Int32` opcional.<br /><br /> Especifica cuántas veces se intentará copiar, si se produjera un error en todos los intentos anteriores. Se establece en cero de forma predeterminada.<br /><br /> **Advertencia:** El uso de reintentos puede enmascarar un problema de sincronización en el proceso de compilación.<br /><br /> **Nota:** Aunque el valor predeterminado de la *tarea* es de cero reintentos, los usos de la tarea suelen pasar `$(CopyRetryCount)`, que es distinto de cero de forma predeterminada.|
|`RetryDelayMilliseconds`|Parámetro `Int32` opcional.<br /><br /> Especifica el retraso entre los reintentos necesarios. Adopta como valor predeterminado el argumento RetryDelayMillisecondsDefault, que se pasa al constructor CopyTask.|
|`SkipUnchangedFiles`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se omite la copia de los archivos sin modificar entre el origen y destino. La tarea `Copy` considera que los archivos están sin modificar si tienen el mismo tamaño y la misma hora de última modificación. <br /><br /> **Nota:** Si se establece este parámetro como `true`, no debe usar el análisis de dependencias en el destino continente, ya que solo se ejecuta la tarea si las horas de última modificación de los archivos de origen son más recientes que las de los archivos de destino.|
|`SourceFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a copiar.|
|`UseHardlinksIfPossible`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, crea vínculos físicos para los archivos copiados en lugar de copiar los archivos.|

## <a name="warnings"></a>Advertencias

Las advertencias se registran, incluidos:

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>Observaciones

Se debe especificar el parámetro `DestinationFolder` o `DestinationFiles`, pero no ambos. Si se especifican los dos, la tarea produce un error y se registra un error.

Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example-1"></a>Ejemplo 1

En el ejemplo siguiente se copian los elementos de la colección de elementos `MySourceFiles` en la carpeta *c:\MyProject\Destination* .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example-2"></a>Ejemplo 2

En el ejemplo siguiente se muestra cómo hacer una copia recursiva. Este proyecto copia de forma recursiva todos los archivos de *c:\MySourceTree* en *c:\MyDestinationTree* , manteniendo la estructura de directorios.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
