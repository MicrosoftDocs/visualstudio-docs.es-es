---
title: Tareas de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633140"
---
# <a name="msbuild-tasks"></a>tareas de MSBuild

Una plataforma de compilación debe ser capaz de ejecutar cualquier número de acciones durante el proceso de compilación. MSBuild utiliza *tareas* para realizar estas acciones. Una tarea es una unidad de código ejecutable que MSBuild utiliza para realizar operaciones de compilación atómicas.

## <a name="task-logic"></a>Lógica de las tareas

 El formato de archivo de proyecto XML de MSBuild no puede ejecutar completamente operaciones de compilación por sí mismo, de modo que la lógica de la tarea debe implementarse fuera del archivo del proyecto.

 La lógica de ejecución de una tarea se implementa como clase .NET que, a su vez, implementa la interfaz <xref:Microsoft.Build.Framework.ITask>, definida en el espacio de nombres <xref:Microsoft.Build.Framework>.

 La clase de tarea también define los parámetros de entrada y salida disponibles para la tarea en el archivo del proyecto. En el archivo del proyecto se puede acceder a todas las propiedades públicas configurables no estáticas y no abstractas expuestas por la clase de tarea si se coloca un atributo correspondiente con el mismo nombre en el elemento [Task](../msbuild/task-element-msbuild.md) y se establece su valor como se muestra en los ejemplos más adelante en este artículo.

 Puede escribir su propia tarea creando una clase administrada que implemente la interfaz <xref:Microsoft.Build.Framework.ITask>. Para más información, consulte [Escribir tareas](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Ejecución de una tarea desde un archivo de proyecto

 Antes de ejecutar una tarea en el archivo del proyecto, primero debe asignar el tipo en el ensamblado que implementa la tarea al nombre de tarea con el elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Esto permite a MSBuild saber dónde buscar la lógica de ejecución de la tarea cuando la encuentre en el archivo del proyecto.

 Para ejecutar una tarea en un archivo del proyecto de MSBuild, cree un elemento con el nombre de la tarea como elemento secundario de un elemento `Target`. Si una tarea acepta parámetros, estos se pasan como atributos del elemento.

 Las listas y propiedades de elementos de MSBuild se pueden usar como parámetros. Por ejemplo, el siguiente código llama a la tarea `MakeDir` y establece el valor de la propiedad `Directories` del objeto `MakeDir` igual que el valor de la propiedad `BuildDir`:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Las tareas también pueden devolver información al archivo del proyecto, que se puede almacenar en elementos o propiedades para su uso posterior. Por ejemplo, el siguiente código llama a la tarea `Copy` y almacena la información de la propiedad de salida `CopiedFiles` en la lista de elementos `SuccessfullyCopiedFiles`.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Tareas incluidas

 MSBuild se distribuye con muchas tareas como, por ejemplo, [Copy](../msbuild/copy-task.md) (que copia archivos), [MakeDir](../msbuild/makedir-task.md) (que crea directorios) y [Csc](../msbuild/csc-task.md) (que compila archivos de código fuente de C#). Para obtener una lista completa de tareas disponibles e información de uso, consulte [Referencia de tareas](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Tareas invalidadas

 MSBuild busca tareas en varias ubicaciones. La primera ubicación es en archivos con la extensión *.OverrideTasks* almacenados en los directorios de .NET Framework. Las tareas en estos archivos invalidan cualquier otra tarea con los mismos nombres, incluidas las tareas en el archivo del proyecto. La segunda ubicación es en archivos con la extensión *.Tasks* en los directorios de .NET Framework. Si la tarea no se encuentra en ninguna de estas ubicaciones, se utiliza la tarea en el archivo del proyecto.

## <a name="see-also"></a>Vea también

- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Escribir tareas](../msbuild/task-writing.md)
- [Tareas insertadas](../msbuild/msbuild-inline-tasks.md)
