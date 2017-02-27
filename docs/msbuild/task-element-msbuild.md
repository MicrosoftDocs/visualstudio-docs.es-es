---
title: "Elemento Task (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Task> (elemento) [MSBuild]"
  - "Task (elemento) [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento Task (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea y ejecuta una instancia de una tarea de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  El nombre del elemento se determina mediante el nombre de la tarea que se está creando.  
  
## Sintaxis  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Condition`|Atributo opcional.  Condición que se va a evaluar.  Para obtener más información, vea [Condiciones](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Atributo opcional.  Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**.  Cuando una tarea, las tareas siguientes en el elemento [Destino](../msbuild/target-element-msbuild.md) y compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**.  Cuando una tarea, las tareas siguientes en el elemento `Target` y compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** \(valor predeterminado\).  Cuando una tarea, las tareas restantes del elemento `Target` y la compilación no se ejecutan, y el elemento completo `Target` y la compilación se considera un error.<br /><br /> Las versiones de .NET Framework antes de 4,5 admitidos los valores únicamente `true` y `false` .<br /><br /> Para obtener más información, vea [Cómo: Pasar errores por alto en las tareas](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md).|  
|`Parameter`|Requerido si la clase de tarea contiene una o más propiedades etiquetadas con el atributo `[Required]`.<br /><br /> Un parámetro de tarea definido por el usuario que contiene el valor de parámetro como su valor.  Puede haber cualquier número de parámetros en el elemento `Task`, con cada atributo asignado a una propiedad de .NET en la clase de tarea.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Almacena los resultados de la tarea en el archivo de proyecto.  Puede haber cero o más elementos `Output` en una tarea.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Destino](../msbuild/target-element-msbuild.md)|Elemento contenedor de tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Comentarios  
 Un elemento `Task` en un archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crea una instancia de una tarea, establece sus propiedades y la ejecuta.  El elemento `Output` almacena los parámetros de salida en propiedades o elementos que se van a utilizar en otra parte en el archivo de proyecto.  
  
 Si existen elementos [OnError](../msbuild/onerror-element-msbuild.md) en el elemento principal `Target` de una tarea, podrán evaluarse si la tarea falla y `ContinueOnError` tiene un valor de `false`.  Para obtener más información sobre las tareas, vea [Tareas](../msbuild/msbuild-tasks.md).  
  
## Ejemplo  
 En el siguiente ejemplo de código se crea una instancia de la clase [Csc task](../msbuild/csc-task.md), establece seis de las propiedades y ejecuta la tarea.  Después de la ejecución, el valor de la propiedad `OutputAssembly` del objeto se coloca en una lista de elementos denominada `FinalAssemblyName`.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)