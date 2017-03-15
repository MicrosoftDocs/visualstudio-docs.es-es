---
title: "C&#243;mo: Extender el proceso de compilaci&#243;n de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, DependsOn (propiedades)"
  - "MSBuild, extender compilaciones de Visual Studio"
  - "MSBuild, reemplazar propiedades DependsOn"
  - "MSBuild, reemplazar destinos predefinidos"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# C&#243;mo: Extender el proceso de compilaci&#243;n de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso de compilación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se define mediante una serie de archivos .targets de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se importan en el archivo de proyecto.  Uno de estos archivos importados, Microsoft.Common.targets, se puede extender para permitirle ejecutar tareas personalizadas en varios puntos en el proceso de compilación.  En este tema se explican dos métodos que puede utilizar para extender el proceso de compilación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Reemplazar destinos predefinidos concretos definidos en Microsoft.Common.targets.  
  
-   Reemplazar las propiedades "DependsOn" definidas en Microsoft.Common.targets.  
  
## Reemplazar los destinos predefinidos  
 El archivo Microsoft.Common.targets contiene un conjunto de destinos predefinidos vacíos a los que se llama antes y después de algunos de los destinos principales en el proceso de compilación.  Por ejemplo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] llama al destino `BeforeBuild` antes que al destino principal `CoreBuild`, y al destino `AfterBuild` después del destino `CoreBuild`.  De forma predeterminada, los destinos vacíos en Microsoft.Common.targets no hacen nada, aunque puede reemplazar su comportamiento predeterminado definiendo los destinos que desee en un archivo de proyecto que importe Microsoft.Common.targets.  Esto le permite usar tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que ofrecen más control sobre el proceso de compilación.  
  
#### Para reemplazar un destino predefinido  
  
1.  Identifique el destino predefinido de Microsoft.Common.targets que desee reemplazar.  Consulte la siguiente tabla para ver la lista completa de destinos que puede reemplazar de forma segura.  
  
2.  Defina el destino o destinos al final del archivo de proyecto, inmediatamente antes de la etiqueta `</Project>`.  Por ejemplo:  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  Compile el archivo de proyecto.  
  
 En la tabla siguiente se muestran todos los destinos de Microsoft.Common.targets que puede reemplazar de forma segura.  
  
|Nombre de destino|Descripción|  
|-----------------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de realizar la compilación básica.  La mayoría de las personalizaciones se hacen en uno de estos dos destinos.|  
|`BeforeBuild`, `AfterBuild`|Las tareas que inserte en uno de estos destinos se ejecutarán antes o después de todos los demás pasos de la compilación. **Note:**  Los destinos `BeforeBuild` y `AfterBuild` ya están definidos en los comentarios al final de la mayoría de los archivos de proyecto.  Esto le permite agregar con facilidad al archivo de proyecto eventos anteriores y posteriores a la compilación.|  
|`BeforeRebuild`, `AfterRebuild`|Las tareas que inserte en uno de estos destinos se ejecutan antes o después de invocar la funcionalidad de recompilar principal.  El orden de ejecución de los destinos en Microsoft.Common.targets es: `BeforeRebuild`, `Clean`, `Build` y, por último, `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Las tareas que inserte en uno de estos destinos se ejecutan antes o después invocar la funcionalidad de limpieza principal.|  
|`BeforePublish`, `AfterPublish`|Las tareas que inserte en uno de estos destinos se ejecutan antes o después de invocar la funcionalidad de publicación principal.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Las tareas que inserte en uno de estos destinos se ejecutan antes o después de resolver las referencias a ensamblados.|  
|`BeforeResGen`, `AfterResGen`|Las tareas que inserte en uno de estos destinos se ejecutan antes o después de generar los recursos.|  
  
## Reemplazar propiedades "DependsOn"  
 Reemplazar los destinos predefinidos es una manera fácil de extender el proceso de compilación pero, dado que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] evalúa la definición de destinos secuencialmente, no hay forma de evitar que otro proyecto que importe su proyecto reemplace los destinos ya reemplazados.  A causa de esto, por ejemplo, una vez importados todos los demás proyectos, el último destino `AfterBuild` definido en el archivo de proyecto será el que se utilice durante la compilación.  
  
 Para protegerse de los reemplazos de destinos no deseados, reemplace las propiedades "DependsOn" que se utilizan en los atributos `DependsOnTargets` en el archivo Microsoft.Common.targets.  Por ejemplo, en el destino `Build`, el atributo `DependsOnTargets` tiene un valor de `"$(BuildDependsOn)"`.  Tenga en cuenta que:  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Este fragmento de XML indica que, para que el destino `Build` pueda ejecutarse, se deben ejecutar primero todos los destinos especificados en la propiedad `BuildDependsOn`.  La propiedad `BuildDependsOn` se define como:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Puede reemplazar este valor de propiedad si declara otra propiedad denominada `BuildDependsOn` al final del archivo de proyecto.  Al incluir la propiedad `BuildDependsOn` anterior en la nueva propiedad, puede agregar nuevos destinos al principio y al final de la lista de destinos.  Por ejemplo:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 Los proyectos que importen sus archivos de proyecto pueden reemplazar estas propiedades sin sobrescribir las personalizaciones que haya realizado.  
  
#### Para reemplazar una propiedad "DependsOn"  
  
1.  Identifique una propiedad "DependsOn" predefinida en Microsoft.Common.targets que desee reemplazar.  Consulte la tabla siguiente para obtener una lista de las propiedades "DependsOn" que se reemplazan habitualmente.  
  
2.  Defina otra instancia de la propiedad o propiedades al final del archivo de proyecto.  Incluya la nueva propiedad en la propiedad original, por ejemplo, `$(BuildDependsOn)`.  
  
3.  Defina sus destinos personalizados antes o después de la definición de la propiedad.  
  
4.  Compile el archivo de proyecto.  
  
### Propiedades "DependsOn" reemplazadas habitualmente  
  
|Nombre de la propiedad|Descripción|  
|----------------------------|-----------------|  
|`BuildDependsOn`|Propiedad que debe reemplazar si desea insertar destinos personalizados antes o después de la compilación del proceso completo.|  
|`CleanDependsOn`|Propiedad que debe reemplazar si desea limpiar el resultado del proceso de compilación personalizado.|  
|`CompileDependsOn`|Propiedad que debe reemplazar si desea insertar procesos personalizados antes o después del paso de compilación.|  
  
## Vea también  
 [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Archivos .Targets](../msbuild/msbuild-dot-targets-files.md)