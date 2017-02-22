---
title: "Elemento UsingTask (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<UsingTask> (elemento) [MSBuild]"
  - "UsingTask (elemento) [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento UsingTask (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Asigna la tarea a la que se hace referencia en un elemento [Task](../msbuild/task-element-msbuild.md) al ensamblado que contiene la implementación de la tarea.  
  
## Sintaxis  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`AssemblyName`|El atributo `AssemblyName` o `AssemblyFile` son obligatorios.<br /><br /> Nombre del ensamblado que se va a cargar.  El atributo `AssemblyName` acepta ensamblados con nombre seguro, aunque no es necesario usar nombres seguros.  Usar este atributo es equivalente a cargar un ensamblado mediante el método <xref:System.Reflection.Assembly.Load%2A> en .NET.<br /><br /> No puede usar este atributo si se usa el atributo `AssemblyFile`.|  
|`AssemblyFile`|El atributo `AssemblyName` o `AssemblyFile` son obligatorios.<br /><br /> Ruta de acceso del archivo del ensamblado.  Este atributo acepta rutas de acceso completas o rutas de acceso relativas.  Las rutas de acceso relativas están relacionadas con el directorio del archivo de proyecto o del archivo de destino cuando se declara el elemento `UsingTask`.  Usar este atributo es equivalente a cargar un ensamblado mediante el método <xref:System.Reflection.Assembly.LoadFrom%2A> en .NET.<br /><br /> No puede usar este atributo si se usa el atributo `AssemblyName`.|  
|`TaskFactory`|Atributo opcional.<br /><br /> Especifica la clase del ensamblado que es responsable de generar instancias del nombre `Task` especificado.  El usuario también puede especificar `TaskBody` como elemento secundario que el generador de tareas recibe y usa para generar la tarea.  El contenido de `TaskBody` es específico del generador de tareas.|  
|`TaskName`|Atributo necesario.<br /><br /> Nombre de la tarea a la que se va a referencia desde un ensamblado.  Si puede darse ambigüedad, este atributo siempre debe especificar espacios de nombres completos.  En caso de ambigüedad, MSBuild elegirá a una coincidencia arbitraria que podría producir resultados inesperados.|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar.  Para obtener más información, vea [Condiciones](../msbuild/msbuild-conditions.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Conjunto de parámetros que aparecen en la tarea que se genera mediante el objeto `TaskFactory` especificado.|  
|[Tarea](../msbuild/task-element-msbuild.md)|Datos que se pasan a `TaskFactory` para generar una instancia de la tarea.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Comentarios  
 Es posible hacer referencia a las variables de entorno, las propiedades de la línea de comandos y las propiedades del nivel de proyecto en cualquier lugar del elemento `UsingTask` si aparece en el archivo del proyecto, ya sea explícitamente o a través de un archivo de proyecto importado.  Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
>  Las propiedades del nivel de proyecto no tienen ningún significado si el elemento `UsingTask` proviene de uno de los archivos .tasks registrados globalmente con el motor de MSBuild.  Las propiedades del nivel de proyecto no son globales para MSBuild.  
  
 En MSBuild 4.0, el uso de tareas puede cargarse a partir de archivos .overridetask.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `UsingTask` con un atributo `AssemblyName`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `UsingTask` con un atributo `AssemblyFile`.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)