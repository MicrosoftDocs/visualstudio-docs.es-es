---
title: MSBuild (tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 366e73473b442ee52ceac10e1398a7bb3e2b52f4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178219"
---
# <a name="msbuild-task"></a>tareas de MSBuild
Compila proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] desde otro proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `MSBuild` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`BuildInParallel`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, los proyectos especificados en el parámetro `Projects` se compilan en paralelo, si es posible. El valor predeterminado es `false`.|  
|`Projects`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos del proyecto que se van a compilar.|  
|`Properties`|Parámetro `String` opcional.<br /><br /> Lista delimitada por caracteres de punto y coma de pares de nombre/valor de propiedad que se aplicarán como propiedades globales al proyecto secundario. Cuando se especifica este parámetro, es funcionalmente equivalente a establecer las propiedades que tiene el modificador **/property** cuando se compila con [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Por ejemplo:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Al pasar propiedades al proyecto mediante el parámetro `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crea una nueva instancia del proyecto, incluso si ya se ha cargado el archivo del proyecto. Cuando se ha creado una nueva instancia del proyecto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] lo trata como un proyecto diferente con propiedades globales diferentes y que se puede compilar en paralelo con otras instancias del proyecto. Por ejemplo, podría compilar una configuración de versión al mismo tiempo que una configuración de depuración.|  
|`RebaseOutputs`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, las rutas de acceso relativas de los elementos de salida de destino de los proyectos compilados tienen sus rutas de acceso ajustadas para ser relativas al proyecto que realiza la llamada. El valor predeterminado es `false`.|  
|`RemoveProperties`|Parámetro `String` opcional.<br /><br /> Especifica el conjunto de propiedades globales que se va a quitar.|  
|`RunEachTargetSeparately`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, la tarea [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] invoca cada destino de la lista que se pasa a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] uno a uno, en lugar de todos al mismo tiempo. Establecer este parámetro en `true` garantiza que los destinos subsiguientes se invocan incluso si se ha producido un error en los destinos previamente invocados. De lo contrario, un error de compilación detendría la invocación de todos los destinos subsiguientes. El valor predeterminado es `false`.|  
|`SkipNonexistentProjects`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, se omitirán los archivos del proyecto que no existen en el disco. De lo contrario, estos proyectos producirán un error.|  
|`StopOnFirstFailure`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, cuando uno de los proyectos no se puede compilar, no se compilarán más proyectos. Actualmente esto no se admite cuando se compila en paralelo (con varios procesadores).|  
|`TargetAndPropertyListSeparators`|Parámetro `String[]` opcional.<br /><br /> Especifica una lista de destinos y propiedades como metadatos de elemento de `Project`. Los separadores no tendrán escape antes del procesamiento. Por ejemplo, %3B (el carácter de escape ';') se tratará como si fuese un carácter sin escape ';'.|  
|`TargetOutputs`|Parámetro de salida de solo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Devuelve los resultados de los destinos compilados de todos los archivos de proyecto. Solo se devuelven los resultados de los destinos especificados; no se devuelven los resultados que puedan existir en los destinos de los que dependen esos destinos.<br /><br /> El parámetro `TargetOutputs` también contiene los metadatos siguientes:<br /><br /> -   `MSBuildSourceProjectFile`: el archivo del proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que contiene el destino que establece los resultados.<br />-   `MSBuildSourceTargetName`: el destino que establece los resultados. **Nota:** Si quiere identificar los resultados de cada archivo del proyecto o destino por separado, ejecute la tarea `MSBuild` por separado para cada archivo del proyecto o destino. Si ejecuta la tarea `MSBuild` solo una vez para compilar todos los archivos del proyecto, los resultados de todos los destinos se recogen en una matriz.|  
|`Targets`|Parámetro `String` opcional.<br /><br /> Especifica los destinos que se compilarán en los archivos del proyecto. Use un punto y coma para separar una lista de nombres de destino. Si no se especifica ningún destino en la tarea `MSBuild`, se compilan los destinos predeterminados especificados en los archivos del proyecto. **Nota:** Los destinos deben existir en todos los archivos del proyecto. Si no es así, se produce un error de compilación.|  
|`ToolsVersion`|Parámetro `String` opcional.<br /><br /> Especifica el `ToolsVersion` que se va a usar al compilar proyectos pasados a esta tarea.<br /><br /> Permite que una tarea [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] compile un proyecto que tiene como destino una versión diferente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que la especificada en el proyecto. Los valores válidos son `2.0`, `3.0` y `3.5`. El valor predeterminado es `3.5`.|  
|`UnloadProjectsOnCompletion`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, se descargará el proyecto una vez completada la operación.|  
|`UseResultsCache`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, se devolverá el resultado almacenado en caché, si está presente.<br /><br />  Si se ejecuta la tarea de MSBuild, su resultado se almacenará en caché en un ámbito <br /><br /> (ProjectFileName, GlobalProperties)[TargetNames]<br /><br /> como una lista de elementos de compilación|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  
  
 A diferencia de utilizar la [tarea Exec](../msbuild/exec-task.md) para iniciar *MSBuild.exe*, esta tarea utiliza el mismo proceso [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para compilar los proyectos secundarios. La lista de destinos ya generados que se pueden omitir se comparte entre las compilaciones primarias y secundarias. Esta tarea también es más rápida porque no se crea ningún proceso [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nuevo.  
  
 Esta tarea puede procesar no solo los archivos del proyecto, sino también los archivos de solución.  
  
 Cualquier configuración que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] necesite para activar la compilación simultánea de proyectos, incluso si la configuración implica una infraestructura remota (por ejemplo, puertos, protocolos, tiempos de espera, reintentos, etc.), debe poder configurarse mediante el uso de un archivo de configuración. Cuando sea posible, los elementos de configuración deben especificarse como parámetros de tarea en la tarea `MSBuild`.  
  
 A partir de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, los proyectos de soluciones emergen de TargetOutputs desde todos los subproyectos que compila.  
  
## <a name="pass-properties-to-projects"></a>Pasar propiedades a proyectos  
 En las versiones de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] anteriores a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, pasar distintos conjuntos de propiedades a diferentes proyectos enumerados en el elemento [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] era una tarea ardua. Si usó el atributo de propiedades de la [tarea MSBuild](../msbuild/msbuild-task.md), su configuración se aplicaba a todos los proyectos que se estaban compilando, a menos que procesara por lotes la [tarea MSBuild](../msbuild/msbuild-task.md) y proporcionara condicionalmente diferentes propiedades para cada proyecto de la lista de elementos.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, en cambio, ofrece dos nuevos elementos de metadatos reservados, Properties y AdditionalProperties, que proporcionan una manera flexible de pasar propiedades diferentes para distintos proyectos que se están compilando con la [tarea MSBuild](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Estos nuevos elementos de metadatos solo son aplicables a elementos que se pasan en el atributo Projects de la [tarea MSBuild](../msbuild/msbuild-task.md).  
  
## <a name="multi-processor-build-benefits"></a>Ventajas de la compilación de varios procesadores  
 Una de las principales ventajas de utilizar estos nuevos metadatos se produce cuando se compilan los proyectos en paralelo en un sistema de varios procesadores. Los metadatos permiten consolidar todos los proyectos en una sola llamada de la [tarea MSBuild](../msbuild/msbuild-task.md) sin tener que realizar ningún procesamiento por lotes ni tareas [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] condicionales. Y cuando se llama únicamente a una sola [tarea MSBuild](../msbuild/msbuild-task.md), todos los proyectos que aparecen en el atributo Projects se compilarán en paralelo. (Solo, sin embargo, si el atributo `BuildInParallel=true` está presente en la [tarea MSBuild](../msbuild/msbuild-task.md)). Para más información, consulte [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="properties-metadata"></a>Metadatos de propiedades  
 Un escenario común es cuando se compilan varios archivos de solución mediante la [tarea MSBuild](../msbuild/msbuild-task.md), solo con diferentes configuraciones de compilación. Otra opción es compilar la solución a1 con la configuración de depuración y la solución a2 con la configuración de versión. En [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, este archivo del proyecto tendría el aspecto siguiente:  
  
> [!NOTE]
>  En el ejemplo siguiente, "..." representa los archivos de solución adicionales.  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Sin embargo, mediante el uso de los metadatos de propiedades, puede simplificar este proceso para utilizar una sola [tarea MSBuild](../msbuild/msbuild-task.md), como se muestra a continuación:  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
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
  
 \- o -  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln..."/>  
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
  
## <a name="additionalproperties-metadata"></a>Metadatos de AdditionalProperties  
 Considere un escenario en que se están compilando dos archivos de solución mediante la [tarea MSBuild](../msbuild/msbuild-task.md), ambos con la configuración de versión, pero uno mediante la arquitectura x86 y otro con la arquitectura ia64. En [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, habría que crear varias instancias de la [tarea MSBuild](../msbuild/msbuild-task.md): una para compilar el proyecto mediante la configuración de versión con la arquitectura x86, la otra mediante la configuración de versión con la arquitectura ia64. El archivo del proyecto tendría el aspecto siguiente:  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 Con el uso de los metadatos AdditionalProperties, puede simplificar este proceso para utilizar una sola [tarea MSBuild](../msbuild/msbuild-task.md) mediante lo siguiente:  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `MSBuild` para compilar los proyectos especificados por la colección de elementos `ProjectReferences`. Los resultados de destino resultantes se almacenan en la colección de elementos `AssembliesBuiltByChildProjects`.  
  
```xml  
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
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)