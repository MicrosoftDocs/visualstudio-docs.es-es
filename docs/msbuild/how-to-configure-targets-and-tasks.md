---
title: "Configuración de destinos y tareas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>Cómo: Configurar destinos y tareas
Las tareas de MSBuild seleccionadas se pueden establecer para ejecutarlas en el entorno de destino, independientemente del entorno del equipo de desarrollo. Por ejemplo, cuando se utiliza un equipo de 64 bits para compilar una aplicación destinada a una arquitectura de 32 bits, las tareas seleccionadas se ejecutan en un proceso de 32 bits.  
  
> [!NOTE]
>  Si una tarea de compilación se escribe en un lenguaje .NET, como Visual C# o Visual Basic, y no utiliza recursos o herramientas nativos, se ejecutará en cualquier contexto de destino sin adaptación.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>Atributos UsingTask y parámetros de tareas  
 Los siguientes atributos de `UsingTask` afectan a todas las operaciones de una tarea en un proceso de compilación determinado:  
  
-   El atributo de `Runtime`, si está presente, establece la versión de Common Language Runtime (CLR), y puede tomar cualquiera de estos valores: `CLR2`, `CLR4`, `CurrentRuntime` o `*` (cualquier tiempo de ejecución).  
  
-   El atributo de `Architecture`, si está presente, establece la plataforma y el valor de bits, y puede tomar cualquiera de estos valores: `x86`, `x64`, `CurrentArchitecture` o `*` (cualquier arquitectura).  
  
-   El atributo de `TaskFactory`, si está presente, establece el generador de tareas que crea y ejecuta la instancia de tarea, y únicamente toma el valor `TaskHostFactory`. Para obtener más información, vea la sección Generadores de tareas más adelante en este documento.  
  
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
  
 Antes de que MSBuild ejecute una tarea, busca un valor `UsingTask` coincidente que tenga el mismo contexto de destino.  Los parámetros que se especifican en `UsingTask` pero no en la tarea correspondiente se consideran coincidentes.  Los parámetros que se especifican en la tarea pero no en el valor `UsingTask` correspondiente también se consideran coincidentes. Si no se especifican valores de parámetros no se especifican en `UsingTask` o la tarea, los valores se establecen de manera predeterminada en `*` (cualquier parámetro).  
  
> [!WARNING]
>  Si existe más de un `UsingTask` y todos tienen atributos `TaskName`, `Runtime` y `Architecture` coincidentes, el último que se evalúe reemplaza a los demás.  
  
 Si se definen parámetros en la tarea, MSBuild intenta encontrar un valor `UsingTask` que coincida con estos parámetros o, al menos, que no esté en conflicto con ellos.  Más de un `UsingTask` puede especificar el contexto de destino de la misma tarea.  Por ejemplo, una tarea que tiene archivos ejecutables diferentes para entornos de destino diferentes podría parecerse a esta:  
  
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
 Antes de ejecutar una tarea, MSBuild comprueba si está designada para ejecutarse en el contexto actual del software.  De ser así, MSBuild la pasa a AssemblyTaskFactory, que la ejecuta en el proceso actual; de lo contrario, MSBuild pasa la tarea a la TaskHostFactory, que la ejecuta en un proceso que coincida con el contexto de destino. Incluso si el contexto actual y el contexto de destino coinciden, puede forzar que una tarea se ejecute fuera de proceso (por motivos de aislamiento, seguridad, o de otra índole) estableciendo `TaskFactory` en `TaskHostFactory`.  
  
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
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
