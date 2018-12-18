---
title: 'Cómo: Extender el proceso de compilación de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 777c2c4ecb5ea8561a43a12f1897c2260d6638d0
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081558"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Cómo: Extender el proceso de compilación de Visual Studio
El proceso de compilación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se define mediante una serie de archivos *.targets* de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se importan en el archivo de proyecto. Uno de estos archivos importados, *Microsoft.Common.targets*, se puede extender para que pueda ejecutar tareas personalizadas en varios puntos del proceso de compilación. En este artículo se explican dos métodos que puede usar para extender el proceso de compilación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Reemplazar destinos predefinidos concretos definidos en *Microsoft.Common.targets*.  
  
-   Reemplazar las propiedades "DependsOn" definidas en *Microsoft.Common.targets*.  
  
## <a name="override-predefined-targets"></a>Reemplazar destinos predefinidos  
 El archivo *Microsoft.Common.targets* contiene un conjunto de destinos vacíos predefinidos al que se llama antes y después de algunos de los destinos principales del proceso de compilación. Por ejemplo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] llama al destino `BeforeBuild` antes del destino `CoreBuild` principal y al destino `AfterBuild` después del destino `CoreBuild`. De forma predeterminada, los destinos vacíos de *Microsoft.Common.targets* no hacen nada, pero puede reemplazar su comportamiento predeterminado si define los destinos que quiere en un archivo de proyecto que importa *Microsoft.Common.targets*. Al reemplazar los destinos predefinidos, puede usar tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para tener más control sobre el proceso de compilación.  
  
#### <a name="to-override-a-predefined-target"></a>Para reemplazar un destino predefinido  
  
1.  Identifique un destino predefinido de *Microsoft.Common.targets* que quiera reemplazar. Consulte la tabla siguiente para ver la lista completa de destinos que puede reemplazar de forma segura.  
  
2.  Defina el destino o los destinos al final del archivo del proyecto, inmediatamente antes de la etiqueta `</Project>`. Por ejemplo:  
  
    ```xml  
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
  
3.  Compile el archivo del proyecto.  

En la tabla siguiente se muestran todos los destinos de *Microsoft.Common.targets* que puede reemplazar de forma segura.  
  
|Nombre de destino|Descripción|  
|-----------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de que se realice la compilación básica. La mayoría de las personalizaciones se realiza en uno de estos dos destinos.|  
|`BeforeBuild`, `AfterBuild`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de todo lo demás de la compilación. **Nota:** Los destinos `BeforeBuild` y `AfterBuild` ya están definidos en los comentarios al final de la mayoría de los archivos de proyecto, lo que permite agregar con facilidad eventos anteriores y posteriores a la compilación al archivo de proyecto.|  
|`BeforeRebuild`, `AfterRebuild`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la invocación a la funcionalidad de recompilación básica. El orden de ejecución de destino en *Microsoft.Common.targets* es: `BeforeRebuild`, `Clean`, `Build` y luego `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la invocación a la funcionalidad de limpieza básica.|  
|`BeforePublish`, `AfterPublish`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la invocación a la funcionalidad de publicación de limpieza básica.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la resolución de las referencias de ensamblados.|  
|`BeforeResGen`, `AfterResGen`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de generar los recursos.|  
  
## <a name="override-dependson-properties"></a>Reemplazar propiedades DependsOn  
 Reemplazar destinos predefinidos es una manera sencilla de extender el proceso de compilación, pero, dado que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] evalúa la definición de destinos secuencialmente, no hay manera de evitar que otro proyecto que importe su proyecto reemplace los destinos que ya ha reemplazado. Por lo tanto, por ejemplo, el último destino `AfterBuild` definido en el archivo del proyecto, después de que se hayan importado todos los demás proyectos, será el que se utiliza durante la compilación.  
  
 Para protegerse de reemplazos de destinos imprevistos, puede reemplazar las propiedades DependsOn que se usan en los atributos `DependsOnTargets` en el archivo *Microsoft.Common.targets*. Por ejemplo, el valor del atributo `DependsOnTargets` del destino `Build` es `"$(BuildDependsOn)"`. Tenga en cuenta que:  
  
```xml  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Este fragmento de XML indica que, antes de que el destino `Build` se pueda ejecutar, primero se deben ejecutar todos los destinos especificados en la propiedad `BuildDependsOn`. La propiedad `BuildDependsOn` se define como:  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Para reemplazar este valor de propiedad, puede declarar otra propiedad denominada `BuildDependsOn` al final del archivo del proyecto. Al incluir la propiedad `BuildDependsOn` anterior en la propiedad nueva, puede agregar nuevos destinos al principio y al final de la lista de destinos. Por ejemplo:  
  
```xml  
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
  
 Los proyectos que importan los archivos del proyecto pueden reemplazar estas propiedades sin sobrescribir las personalizaciones que haya realizado.  
  
#### <a name="to-override-a-dependson-property"></a>Para reemplazar una propiedad DependsOn  
  
1.  Identifique una propiedad DependsOn predefinida de *Microsoft.Common.targets* que quiera reemplazar. Vea la tabla siguiente para obtener una lista de las propiedades DependsOn que normalmente se reemplazan.  
  
2.  Defina otra instancia de la propiedad o de las propiedades al final del archivo del proyecto. Incluya la propiedad original, por ejemplo `$(BuildDependsOn)`, en la propiedad nueva.  
  
3.  Defina sus destinos personalizados antes o después de la definición de la propiedad.  
  
4.  Compile el archivo del proyecto.  
  
### <a name="commonly-overridden-dependson-properties"></a>Propiedades DependsOn que normalmente se reemplazan  
  
|Nombre de la propiedad|Descripción|  
|-------------------|-----------------|  
|`BuildDependsOn`|La propiedad que se debe reemplazar si quiere insertar destinos personalizados antes o después del proceso de compilación completo.|  
|`CleanDependsOn`|La propiedad que se debe reemplazar si quiere limpiar el resultado del proceso de compilación personalizado.|  
|`CompileDependsOn`|La propiedad que se debe reemplazar si quiere insertar procesos personalizados antes o después del paso de compilación.|  
  
## <a name="see-also"></a>Vea también  
 [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Archivos .targets](../msbuild/msbuild-dot-targets-files.md)