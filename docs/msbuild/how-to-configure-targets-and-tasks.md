---
title: Procedimiento Configurar destinos y tareas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8f1bc76789ef80c1138efb94bda42442702c05
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596351"
---
# <a name="how-to-configure-targets-and-tasks"></a>Procedimiento Configurar destinos y tareas
Las tareas de MSBuild seleccionadas se pueden establecer para ejecutarlas en el entorno de destino, independientemente del entorno del equipo de desarrollo. Por ejemplo, cuando se utiliza un equipo de 64 bits para compilar una aplicación destinada a una arquitectura de 32 bits, las tareas seleccionadas se ejecutan en un proceso de 32 bits.

> [!NOTE]
> Si una tarea de compilación se escribe en un lenguaje .NET, como Visual C# o Visual Basic, y no utiliza recursos o herramientas nativos, se ejecutará en cualquier contexto de destino sin adaptación.

## <a name="usingtask-attributes-and-task-parameters"></a>Atributos UsingTask y parámetros de tareas
Los siguientes atributos de `UsingTask` afectan a todas las operaciones de una tarea en un proceso de compilación determinado:

- El atributo de `Runtime`, si está presente, establece la versión de Common Language Runtime (CLR), y puede tomar cualquiera de estos valores: `CLR2`, `CLR4`, `CurrentRuntime` o `*` (cualquier tiempo de ejecución).

- El atributo de `Architecture`, si está presente, establece la plataforma y el valor de bits, y puede tomar cualquiera de estos valores: `x86`, `x64`, `CurrentArchitecture` o `*` (cualquier arquitectura).

- El atributo de `TaskFactory`, si está presente, establece el generador de tareas que crea y ejecuta la instancia de tarea, y únicamente toma el valor `TaskHostFactory`. Para obtener más información, vea [Generadores de tareas](#task-factories) más adelante en este documento.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

También puede utilizar los parámetros `MSBuildRuntime` y `MSBuildArchitecture` para establecer el contexto de destino de una tarea individual.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Antes de que MSBuild ejecute una tarea, busca un valor `UsingTask` coincidente que tenga el mismo contexto de destino. Los parámetros que se especifican en `UsingTask` pero no en la tarea correspondiente se consideran coincidentes. Los parámetros que se especifican en la tarea pero no en el valor `UsingTask` correspondiente también se consideran coincidentes. Si no se especifican valores de parámetros no se especifican en `UsingTask` o la tarea, los valores se establecen de manera predeterminada en `*` (cualquier parámetro).

> [!WARNING]
> Si existe más de un `UsingTask` y todos tienen atributos `TaskName`, `Runtime` y `Architecture` coincidentes, el último que se evalúe reemplaza a los demás.

 Si se definen parámetros en la tarea, MSBuild intenta encontrar un valor `UsingTask` que coincida con estos parámetros o, al menos, que no esté en conflicto con ellos. Más de un `UsingTask` puede especificar el contexto de destino de la misma tarea. Por ejemplo, una tarea que tiene archivos ejecutables diferentes para entornos de destino diferentes podría parecerse a esta:

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>Generadores de tareas
Antes de ejecutar una tarea, MSBuild comprueba si está designada para ejecutarse en el contexto actual del software. De ser así, MSBuild la pasa a AssemblyTaskFactory, que la ejecuta en el proceso actual; de lo contrario, MSBuild pasa la tarea a la TaskHostFactory, que la ejecuta en un proceso que coincida con el contexto de destino. Incluso si el contexto actual y el contexto de destino coinciden, puede forzar que una tarea se ejecute fuera de proceso (por motivos de aislamiento, seguridad, o de otra índole) estableciendo `TaskFactory` en `TaskHostFactory`.

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Parámetros de tareas fantasma
Al igual que cualquier otro parámetro de tarea, `MSBuildRuntime` y `MSBuildArchitecture` se pueden establecer desde las propiedades de compilación.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

A diferencia de otros parámetros de tarea, `MSBuildRuntime` y `MSBuildArchitecture` no son evidentes para la propia tarea. Para escribir una tarea que tenga en cuenta el contexto en el que se ejecuta, debe probar el contexto mediante una llamada a .NET Framework o bien debe usar propiedades de compilación para pasar información de contexto a través de otros parámetros de tarea.

> [!NOTE]
> Es posible establecer atributos `UsingTask` desde las propiedades del conjunto de herramientas y del entorno.

Los parámetros `MSBuildRuntime` y `MSBuildArchitecture` proporcionan la manera más flexible de establecer el contexto de destino, pero también la manera más limitada en cuanto al ámbito. Por un lado, dado que se establecen en la propia instancia de tarea y no se evalúan hasta que la tarea está a punto de ejecutarse, pueden derivar su valor del ámbito completo de propiedades disponibles en tiempo de evaluación y tiempo de compilación. Por otro lado, estos parámetros solo se aplican a una instancia determinada de una tarea en un destino determinado.

> [!NOTE]
> Los parámetros de tareas se evalúan en el contexto del nodo primario, no en el del host de tareas. Las variables de entorno dependientes del tiempo de ejecución o de la arquitectura (por ejemplo, la ubicación *Archivos de programa*) se evalúan como el valor que coincide con el nodo primario. Pero si la tarea lee directamente la misma variable de entorno, se evaluará correctamente en el contexto del host de la tarea.

## <a name="see-also"></a>Vea también
- [Configurar destinos y tareas](../msbuild/configuring-targets-and-tasks.md)
