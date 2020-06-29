---
title: Delete (Tarea) | Microsoft Docs
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eddb9804378a4c32de9d1b68f952bc715f32ffd6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288915"
---
# <a name="delete-task"></a>Delete (tarea)

Elimina los archivos especificados.

## <a name="parameters"></a>Parámetros

En la siguiente tabla se describen los parámetros de la tarea `Delete` .

|Parámetro|Descripción|
|---------------|-----------------|
|`DeletedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos que se eliminaron correctamente.|
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a eliminar.|
|`TreatErrorsAsWarnings`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, los errores se registran como advertencias. El valor predeterminado es `false`.|

## <a name="remarks"></a>Comentarios

Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Tenga cuidado al usar comodines con la tarea `Delete`. Puede eliminar fácilmente los archivos equivocados con expresiones como `$(SomeProperty)\**\*.*` o `$(SomeProperty)/**/*.*`, especialmente si la propiedad se evalúa como una cadena vacía, en cuyo caso el parámetro `Files` puede evaluarse como raíz de la unidad y eliminar mucho más de lo que se quiere.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se elimina el archivo *MyApp.pdb* al compilar el destino `DeleteDebugSymbolFile`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Si necesita realizar un seguimiento de los archivos eliminados, establezca `TaskParameter` en `DeletedFiles` con el nombre de elemento, como se indica a continuación:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

En lugar de usar caracteres comodines directamente en la tarea `Delete`, cree un grupo `ItemGroup` de archivos que se vayan a eliminar y ejecute en él la tarea `Delete`. No obstante, asegúrese de colocar `ItemGroup` con cuidado. Si coloca `ItemGroup` en el nivel superior de un archivo de proyecto, se evalúa antes de que se inicie la compilación, por lo que no incluirá los archivos compilados como parte del proceso de compilación. Por lo tanto, coloque el grupo `ItemGroup` que crea la lista de elementos que se van a eliminar en un destino cercano a la tarea `Delete`. También puede especificar una condición para comprobar que la propiedad no está vacía, así que no creará una lista de elementos con una ruta de acceso que se inicie en la raíz de la unidad.

La tarea `Delete` está pensada para eliminar archivos. Si quiere eliminar un directorio, use [RemoveDir](removedir-task.md).

La tarea `Delete` no proporciona una opción para eliminar archivos de solo lectura. Para ello, puede usar la tarea `Exec` para ejecutar el comando `del` o equivalente, con la opción adecuada para permitir la eliminación de archivos de solo lectura. Debe prestar atención a la longitud de la lista de elementos de entrada, ya que hay una limitación de longitud en la línea de comandos; además, asegúrese de usar los nombres de archivo con espacios, como en este ejemplo:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

En general, al escribir scripts de compilación, tenga en cuenta si la eliminación es una parte lógica de una operación `Clean`. Si necesita configurar algunos archivos para que se limpien como parte de una operación `Clean` normal, puede agregarlos a la lista `@(FileWrites)` y se eliminarán en la siguiente operación `Clean`. Si se necesita más procesamiento personalizado, defina un destino y especifique que se ejecute mediante el establecimiento del atributo `BeforeTargets="Clean"` o `AfterTargets="Clean"`, o bien defina la versión personalizada de los destinos `BeforeClean` o `AfterClean`. Consulte [Personalizar una compilación](customize-your-build.md).

## <a name="see-also"></a>Vea también

- [Tarea RemoveDir](removedir-task.md)
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
