---
title: "Elemento Target (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Target (elemento) [MSBuild]"
  - "Elemento <Target> [MSBuild]"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Target (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene un conjunto de tareas que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ejecutará secuencialmente.  
  
## Sintaxis  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Atributo necesario.<br /><br /> Nombre del destino.|  
|`Condition`|Atributo opcional.<br /><br /> La condición que se va a evaluar.  Si la condición se evalúa como `false`, el destino no ejecutará el cuerpo del destino o cualquier destino establecido en el atributo `DependsOnTargets`.  Para obtener más información sobre las condiciones, vea [Condiciones](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Atributo opcional.<br /><br /> Los archivos esos entradas de formulario en este destino.  Varios archivos están separados por puntos y coma.  Las marcas de tiempo de los archivos se compararán con las de archivos en `Outputs` para determinar si `Target` está actualizado.  Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md), [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md) y [Transformaciones](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Atributo opcional.<br /><br /> Los archivos que forman los resultados en este destino.  Varios archivos están separados por puntos y coma.  Las marcas de tiempo de los archivos se compararán con las de archivos en `Inputs` para determinar si `Target` está actualizado.  Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md), [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md) y [Transformaciones](../msbuild/msbuild-transforms.md).|  
|`Returns`|Atributo opcional.<br /><br /> El conjunto de elementos que estará disponible para las tareas que invocan a este destino, por ejemplo, las tareas de MSBuild.  Los destinos múltiples están separados con puntos y coma.  Si los destinos del archivo no tienen ningún atributo de `Returns`, los atributos de los resultados se utilizan en su lugar con este fin.|  
|`KeepDuplicateOutputs`|Atributo booleano opcional.<br /><br /> Si se registra `true`, las referencias al mismo elemento del destino cambia.  De forma predeterminada, este atributo es `false`.|  
|`BeforeTargets`|Atributo opcional.<br /><br /> Una lista de nombres de destino separados por punto y coma. Cuando se especifica, indica que este destino debe ejecutarse antes de destino o de los especificados.  Esto permite al autor del proyecto ampliar un conjunto de destinos sin modificaciones de ellos directamente.  Para obtener más información, vea [Orden de compilación de destinos](../msbuild/target-build-order.md).|  
|`AfterTargets`|Atributo opcional.<br /><br /> Una lista de nombres de destino separados por punto y coma.  Cuando se especifica, indica que este destino debe ejecutarse después de destino o de los especificados.  Esto permite al autor del proyecto ampliar un conjunto de destinos sin modificaciones de ellos directamente.  Para obtener más información, vea [Orden de compilación de destinos](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Atributo opcional.<br /><br /> Los destinos que se deben ejecutar antes de este destino se pueden ejecutar o puede tener lugar el análisis de dependencia de nivel superior.  Los destinos múltiples están separados con puntos y coma.|  
|`Label`|Atributo opcional.<br /><br /> Un identificador que puede identificar o ordenar los elementos del sistema y de usuarios.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Tarea](../msbuild/task-element-msbuild.md)|Crea y ejecuta una instancia de una tarea de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Puede haber cero o más tareas en un destino.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Contiene un conjunto de elementos definidos por el usuario de `Property`.  A partir de.NET Framework 3.5, un elemento de `Target` puede contener elementos de `PropertyGroup`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Contiene un conjunto de elementos definidos por el usuario de `Item`.  A partir de.NET Framework 3.5, un elemento de `Target` puede contener elementos de `ItemGroup`.  Para obtener más información, vea [elementos](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Realice uno o más destinos para ejecutarse si el atributo de `ContinueOnError` es ErrorAndStop \(o `false`\) para una tarea errónea.  Puede haber cero o más elementos `OnError` en un destino.  Si están presentes elementos `OnError`, deben ser los últimos elementos en el elemento `Target`.<br /><br /> Para obtener información sobre el atributo de `ContinueOnError`, vea [Elemento Task \(MSBuild\)](../msbuild/task-element-msbuild.md).|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Comentarios  
 El primer destino que se ejecutará se especifica en el tiempo de ejecución.  Los destinos pueden tener dependencias en otros destinos.  Por ejemplo, un destino para la implementación depende de un destino para la compilación.  El motor de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ejecuta las dependencias en el orden en que aparecen en el atributo `DependsOnTargets`, de izquierda a derecha.  Para obtener más información, vea [Destinos](../msbuild/msbuild-targets.md).  
  
 Un destino sólo se ejecuta una vez durante una compilación, incluso si dependen del mismo más de un destino.  
  
 Si se omite un destino porque su atributo `Condition` se evalúa como `false`, todavía se puede ejecutar si se invoca más adelante durante la compilación y su atributo `Condition` se evalúa como `true` en dicho momento.  
  
 Antes de MSBuild 4, `Target` devolvía todos los elementos especificados en el atributo `Outputs` .  Para ello, MSBuild debía grabar estos elementos en caso de que las tareas los pidieran más adelante durante la compilación.  Porque no había forma de indicar qué objetivos tenían salidas necesarias para los llamadores, MSBuild acumulaba todos los elementos de todas las `Outputs` en todas las `Target` invocadas.  Esto llevó a escalar problemas para compilaciones que tenían un gran número de elementos de salida.  
  
 Si el usuario especifica `Returns` en cualquier elemento `Target` de un proyecto, solo los `Target`que tengan un atributo `Returns` graban dichos elementos.  
  
 `Target` puede contener un atributo `Outputs` y un atributo `Returns` .  `Outputs` se utiliza con `Inputs` para determinar si el destino está actualizado.  `Returns`, si existe, reemplaza el valor de `Outputs` para determinar qué elementos se devuelven a los llamadores.  Si `Returns` no está presente, `Outputs` estarán disponibles para los llamadores excepto en el caso descrito anteriormente.  
  
 Antes de MSBuild 4, siempre que un `Target` incluía varias referencias al mismo elemento en sus `Outputs`, esos elementos duplicados se registraban.  En las compilaciones muy grandes que tenían un gran número de resultados y muchas interdependencias de proyecto, esto hacía que se desperdiciara una gran cantidad de memoria porque los elementos duplicados no servían.  Cuando el atributo de `KeepDuplicateOutputs` se establece en `true`, se registran estos duplicados.  
  
## Ejemplo  
 El siguiente ejemplo de código muestra un elemento `Target` que ejecuta la tarea `Csc`.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
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
 [Destinos](../msbuild/msbuild-targets.md)   
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)