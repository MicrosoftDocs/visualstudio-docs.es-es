---
title: "C&#243;mo: Configurar destinos y tareas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Configurar destinos y tareas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las tareas de MSBuild se pueden establecer para ejecutarlas en el entorno de destino, independientemente del entorno del equipo de desarrollo.  Por ejemplo, cuando se utiliza un equipo de 64 bits para compilar una aplicación destinada a una arquitectura de 32 bits, las tareas seleccionado se ejecutan en un proceso de 32 bits.  
  
> [!NOTE]
>  Si una tarea de compilación se escribe en un lenguaje.NET, como Visual c\# o Visual Basic, y no utiliza los recursos nativos o herramientas, después se ejecutará en cualquier contexto de destino sin la adaptación.  
  
## Atributos UsingTask y parámetros de tareas  
 Los siguientes atributos de `UsingTask` afectan a todas las operaciones de una tarea en un proceso de compilación determinado:  
  
-   El atributo de `Runtime` , si está presente, establece la versión \(CLR\) de Common Language Runtime, y puede tomar de estos valores: `CLR2`, `CLR4`, `CurrentRuntime`, o `*` \(cualquier runtime\).  
  
-   El atributo de `Architecture` , si está presente, establece la plataforma y el valor de bits, y puede tomar de estos valores: `x86`, `x64`, `CurrentArchitecture`, o `*` \(cualquier arquitectura\).  
  
-   El atributo de `TaskFactory` , si existe, establece el generador de tareas que crea y ejecuta la instancia de tarea, y únicamente acepta el valor `TaskHostFactory`.  Para obtener más información, vea la sección de los generadores de la tarea más adelante en este documento.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 También puede utilizar los parámetros de `MSBuildRuntime` y de `MSBuildArchitecture` para establecer el contexto del destino de una tarea individual.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Antes de que MSBuild ejecutar una tarea, busca `UsingTask` coincidentes que tiene el mismo contexto de destino.  Los parámetros que se especifican en `UsingTask` pero no en la tarea correspondiente se consideran coincidentes.  Los parámetros especificados en la tarea pero no en `UsingTask` correspondiente también se consideran coincidentes.  Si los valores de parámetros no se especifican en `UsingTask` o la tarea, los valores a `*` \(cualquier parámetro\).  
  
> [!WARNING]
>  Si existe más de un `UsingTask` y todas tienen `TaskName`coincidente, `Runtime`, y atributos de `Architecture` , el último que se evaluará reemplaza los otros.  
  
 Si los parámetros se establecen en la tarea, MSBuild intenta encontrar `UsingTask` que coincide con estos parámetros o, al menos, no está en conflicto con ellos.  Más de un `UsingTask` puede especificar el contexto del destino de la misma tarea.  Por ejemplo, una tarea que tiene varias aplicaciones ejecutables para diferentes entornos de destino podría ser similar esto:  
  
```  
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
  
## Generadores de la tarea  
 Antes de ejecutar una tarea, las comprobaciones de MSBuild para ver si está designada para ejecutarse en el contexto actual del software.  Si la tarea se designa tan, MSBuild la pasa al AssemblyTaskFactory, que se ejecuta en el proceso actual; si no, MSBuild pasa la tarea al TaskHostFactory, que ejecuta la tarea en un proceso que coincida con el contexto de destino.  Aunque coincidan con el contexto actual y el contexto de destino, puede forzar una tarea de ejecutar fuera \(por el aislamiento, la seguridad, u otras razones\) estableciendo `TaskFactory` a `TaskHostFactory`.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## Parámetros ficticios de tarea  
 Como cualquier otro parámetro de tarea, `MSBuildRuntime` y `MSBuildArchitecture` se pueden establecer de las variables.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 A diferencia de otros parámetros de tareas, `MSBuildRuntime` y `MSBuildArchitecture` no se aprecian a la tarea propio.  Para escribir una tarea que tenga en cuenta el contexto en el que se ejecuta, debe probar el contexto llamando a .NET Framework, o utilizar propiedades de compilación para pasar información de contexto con otros parámetros de tareas.  
  
> [!NOTE]
>  los atributos de`UsingTask` se pueden establecer propiedades del conjunto de herramientas y del entorno.  
  
 Los parámetros de `MSBuildRuntime` y de `MSBuildArchitecture` proporcionan la manera más flexible de establecer el contexto de destino, pero también el más limitado de ámbito.  Por una parte, porque se establecen en la propia instancia de tarea y no se evalúan hasta que la tarea se alrededor ejecutarse, pueden derivar su valor de ámbito completo de las propiedades disponibles en el evaluación\-Tiempo y el tiempo de compilación.  Por otra parte, estos parámetros se aplican sólo a una instancia determinada de una tarea de un destino determinado.  
  
> [!NOTE]
>  Los parámetros de la tarea se evalúan en el contexto del nodo primario, no en el contexto de host de la tarea. Las variables de entorno que son el tiempo de ejecución o dependiente de la arquitectura \(como la ubicación de los archivos de programa\) se volverá al valor que coincida con el nodo primario.  Sin embargo, si la misma variable de entorno se lea directamente por la tarea, correctamente se evalúa en el contexto de host de la tarea.  
  
## Vea también  
 [Configurar destinos y tareas](../msbuild/configuring-targets-and-tasks.md)