---
title: "MSBuild (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild (tarea) [MSBuild]"
  - "MSBuild, tarea MSBuild"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# MSBuild (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Compila proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a partir de otro proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `MSBuild`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`BuildInParallel`|Parámetro `Boolean` opcional.<br /><br /> Si su valor es `true`, los proyectos especificados en el parámetro `Projects` se compilan en paralelo, si es posible.  El valor predeterminado es `false`.|  
|`Projects`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos de proyecto que se van a compilar.|  
|`Properties`|Parámetro `String` opcional.<br /><br /> Lista de los pares de nombre y valor de propiedad delimitados por signos de punto y coma que se van a aplicar al proyecto secundario como propiedades globales.  Especificar este parámetro equivale funcionalmente a establecer las propiedades con el modificador **\/property** cuando se compila con [MSBuild.exe](../msbuild/msbuild-command-line-reference.md).  Por ejemplo:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Cuando se pasan las propiedades al proyecto mediante el parámetro `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crea una nueva instancia del proyecto aunque ya se haya cargado el archivo de proyecto.  Cuando se ha creado una nueva instancia del proyecto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] la trata como un proyecto diferente con propiedades globales diferentes y que se puede compilar en paralelo con otras instancias del proyecto.  Por ejemplo, una configuración Release podría compilarse al mismo tiempo que una configuración Debug.|  
|`RebaseOutputs`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, las rutas de acceso relativas de los elementos resultantes de destino de los proyectos compilados tienen las rutas de acceso ajustadas para ser relativas al proyecto que realiza la llamada.  El valor predeterminado es `false`.|  
|`RemoveProperties`|Parámetro `String` opcional.<br /><br /> Especifica el conjunto de propiedades globales que se van a quitar.|  
|`RunEachTargetSeparately`|Parámetro `Boolean` opcional.<br /><br /> Si su valor es `true`, la tarea [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] invoca cada destino de la lista pasado a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de uno en uno, en lugar de todos al mismo tiempo.  Establecer este parámetro en `true` garantiza que se invocarán los destinos siguientes aunque se produjera un error en los destinos previamente invocados.  En caso contrario, un error de compilación detendría la invocación de todos los destinos siguientes.  El valor predeterminado es `false`.|  
|`SkipNonexistentProjects`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se omitirán los archivos de proyecto que no existen en el disco.  De lo contrario, esos proyectos producirán un error.|  
|`StopOnFirstFailure`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, no se compilará ningún proyecto más cuando uno de los proyectos no se pueda compilar.  Esta acción no se admite actualmente al compilar en paralelo \(con varios procesadores\).|  
|`TargetAndPropertyListSeparators`|Parámetro `String[]` opcional.<br /><br /> Especifica una lista de destinos y propiedades como metadatos del elemento `Project`\).  A los separadores se les quitarán los caracteres de escape antes del procesamiento.  eg... %3B \(pierde “; "\) se trata como si fuera O.N.U\- pierde “; ”.|  
|`TargetOutputs`|Parámetro de salida de sólo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Devuelve los resultados de los destinos compilados de todos los archivos de proyecto.  Se devuelven únicamente los resultados de los destinos especificados; no se devuelven los resultados que puedan existir en los destinos de los que dependen esos destinos.<br /><br /> El parámetro `TargetOutputs` también contiene los metadatos siguientes:<br /><br /> -   `MSBuildSourceProjectFile`: archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que contiene el destino que establece los resultados.<br />-   `MSBuildSourceTargetName`: El destino que establece los resultados. **Note:**  Si desea identificar los resultados de cada archivo de proyecto o destino por separado, ejecute la tarea `MSBuild` por separado para cada archivo de proyecto o destino.  Si ejecuta la tarea `MSBuild` sólo una vez para compilar todos los archivos de proyecto, los resultados de todos los destinos se recogen en una matriz.|  
|`Targets`|Parámetro `String` opcional.<br /><br /> Especifica el destino o destinos que se compilarán en los archivos de proyecto.  Utilice un punto y coma para separar los nombres de destino en la lista.  Si no se especifica ningún destino en la tarea `MSBuild`, se compilarán los destinos predeterminados especificados en los archivos de proyecto. **Note:**  Los destinos deben existir en todos los archivos de proyecto.  De lo contrario, se genera un error de compilación.|  
|`ToolsVersion`|Parámetro `String` opcional.<br /><br /> Especifica la `ToolsVersion` que se desea utilizar al compilar proyectos pasados a esta tarea.<br /><br /> Permite a una tarea [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] compilar un proyecto que tiene como destino una versión diferente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que la especificada en el proyecto.  Los valores válidos son `2.0`, `3.0` y `3.5`.  El valor predeterminado es `3.5`.|  
|`UnloadProjectsOnCompletion`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se descargará el proyecto una vez completada la operación.|  
|`UseResultsCache`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, el resultado en caché será devuelto, si está presente.  Si se ejecuta la tarea de MSBuild, su resultado se almacenará en caché en un ámbito \(nombreDeArchivoDeProyecto, propiedadesGlobales\)\[nombresDeDestino\]<br /><br /> como una lista de elementos de compilación|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
 A diferencia de cuando se utiliza [Exec \(Tarea\)](../msbuild/exec-task.md) para iniciar MSBuild.exe, esta tarea utiliza los mismos procesos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para compilar los proyectos secundarios.  Las compilaciones primarias y secundarias comparten la lista de destinos ya compilados que se pueden omitir.  Esta tarea también es más rápida porque no se crea ningún nuevo proceso de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Esta tarea no sólo puede procesar archivos de proyecto sino también archivos de solución.  
  
 Es necesario que cualquier configuración requerida por [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para que los proyectos se puedan compilar al mismo tiempo, aunque la configuración implique una infraestructura remota \(por ejemplo, puertos, protocolos, tiempos de espera, intentos, etc.\), debe poderse configurar mediante un archivo de configuración.  Cuando sea posible, los elementos de configuración se deben poder especificar como parámetros en la tarea `MSBuild`.  
  
 A partir de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, los proyectos de solución extraen TargetOutputs de todos los subproyectos que compila.  
  
## Pasar propiedades a los proyectos  
 En las versiones de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] anteriores a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, pasar conjuntos diferentes de propiedades a los diferentes proyectos enumerados en el elemento [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] resultaba un reto.  Si utilizaba el atributo Properties de [MSBuild Task](../msbuild/msbuild-task.md), se aplicaba su valor a todos los proyectos que se estaban compilando a menos que [MSBuild Task](../msbuild/msbuild-task.md) se procesara por lotes y proporcionara condicionalmente las diferentes propiedades para cada proyecto de la lista del elemento.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, sin embargo, dispone de dos nuevos elementos de metadatos reservados, Properties y AdditionalProperties, que ofrece una manera flexible de pasar las diferentes propiedades para los diferentes proyectos que se están compilando con [MSBuild Task](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Estos nuevos elementos de metadatos sólo se aplican a los elementos pasados en el atributo Projects de [MSBuild Task](../msbuild/msbuild-task.md).  
  
## Ventajas de la compilación para varios procesadores  
 Una de las principales ventajas de utilizar estos nuevos metadatos se observa al compilar los proyectos en paralelo en un sistema de varios procesadores.  Los metadatos permiten consolidar todos los proyectos en una única llamada a [MSBuild Task](../msbuild/msbuild-task.md) sin tener que realizar cualquier tarea [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] por lotes o condicional.  Y, cuando se llama a una única [MSBuild Task](../msbuild/msbuild-task.md), todos los proyectos enumerados en el atributo Projects se compilan en paralelo.  \(Únicamente si el atributo `BuildInParallel=true` se encuentra en [MSBuild Task](../msbuild/msbuild-task.md).\) Para obtener más información, vea [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## Metadatos Properties  
 Un escenario habitual es cuando se compilan varios archivos de solución mediante [MSBuild Task](../msbuild/msbuild-task.md), utilizando únicamente diferentes configuraciones de compilación.  Es posible que desee compilar la solución a1 con la configuración Debug y la solución a2 con la configuración Release.  En [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, este archivo de proyecto tendría el siguiente aspecto:  
  
> [!NOTE]
>  En el ejemplo siguiente, "…" representa los archivos de solución adicionales.  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Sin embargo, con los metadatos Properties, puede simplificar este proceso y utilizar una única [MSBuild Task](../msbuild/msbuild-task.md), como se muestra a continuación:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \-O bien\-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## Metadatos AdditionalProperties  
 Considere un escenario donde se están compilando dos archivos de solución mediante [MSBuild Task](../msbuild/msbuild-task.md), ambos utilizan la configuración Release, pero uno utiliza la arquitectura x86 y el otro la arquitectura ia64.  En [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, sería necesario crear varias instancias de [MSBuild Task](../msbuild/msbuild-task.md): una para compilar el proyecto con la configuración Release y la arquitectura x86, y otra con la configuración Release y la arquitectura ia64.  Su archivo de proyecto tendría el siguiente aspecto:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 Con los metadatos AdditionalProperties, puede simplificar este proceso para utilizar una única [MSBuild Task](../msbuild/msbuild-task.md) utilizando lo siguiente:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `MSBuild` para compilar los proyectos especificados por la colección de elementos `ProjectReferences`.  Los resultados de destino obtenidos se almacenan en la colección de elementos `AssembliesBuiltByChildProjects`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)