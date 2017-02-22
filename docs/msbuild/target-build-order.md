---
title: "Orden de compilaci&#243;n de destinos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, orden de compilación"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Orden de compilaci&#243;n de destinos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los destinos se deben ordenar si la entrada a un destino depende de la salida de otro destino.  Puede utilizar estos atributos para especificar el orden en que se ejecutan los destinos:  
  
-   `InitialTargets`.  Este atributo de `Project` especifica los destinos que se ejecutarán en primer lugar, aunque los destinos se especifican en la línea de comandos o en el atributo de `DefaultTargets`.  
  
-   `DefaultTargets`.  Este atttribute de `Project` especifica se ejecutan los destinos si no se ha especificado explícitamente ningún destino en la línea de comandos.  
  
-   `DependsOnTargets`.  Este atributo de `Target` especifica los destinos que deben ejecutarse antes de que este destino pueda ejecutarse.  
  
-   `BeforeTargets` y `AfterTargets`.  Estos atributos de `Target` especifican que este destino debe ejecutarse antes o después de los destinos especificados \(MSBuild 4,0\).  
  
 Un destino nunca se ejecuta dos veces durante una compilación, aunque un destino subsiguiente en la compilación dependa de él.  Una vez ejecutado un destino, su contribución a la compilación se ha completado.  
  
 Los destinos pueden tener un atributo `Condition`.  Si la condición especificada se evalúa como `false`, el destino no se ejecuta y no tiene ningún efecto en la compilación.  Para obtener más información sobre las condiciones, vea [Condiciones](../msbuild/msbuild-conditions.md).  
  
## Destinos iniciales  
 El atributo de `InitialTargets` de elemento de [proyecto](../msbuild/project-element-msbuild.md) especifica los destinos que se ejecutarán en primer lugar, aunque los destinos se especifican en la línea de comandos o en el atributo de `DefaultTargets`.  Se utilizan normalmente para la comprobación de errores.  
  
 El valor del atributo de `InitialTargets` puede ser una lista punto y\- delimitada, ordenadas de destinos.  El ejemplo siguiente especifica que el destino de `Warm` ejecuta, y después el destino de `Eject` ejecuta.  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Los proyectos importados pueden tener sus propios atributos `InitialTargets`.  Todos los destinos iniciales se agregan formando un conjunto y se ejecutan en orden.  
  
 Para obtener más información, vea [Cómo: Especificar qué destino utilizar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Destinos predeterminados  
 El atributo de `DefaultTargets` de elemento de [proyecto](../msbuild/project-element-msbuild.md) especifica qué destinos se compilan si un destino no se especifica explícitamente en una línea de comandos.  
  
 El valor del atributo de `DefaultTargets` puede ser una lista punto y\- delimitada, ordenadas de destinos predeterminados.  El ejemplo siguiente especifica que el destino de `Clean` ejecuta, y después el destino de `Build` ejecuta.  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Puede reemplazar los destinos predeterminados utilizando el modificador **\/target** en la línea de comandos.  El ejemplo siguiente especifica que el destino de `Build` ejecuta, y después el destino de `Report` ejecuta.  Al especificar los destinos de esta manera, se omite cualquier destino predeterminado.  
  
 `msbuild /target:Build;Report`  
  
 Si se especifican ambos destinos iniciales y los destinos predeterminados, y si no se especifican destinos de la línea de comandos, MSBuild ejecuta primero los destinos iniciales, y después ejecuta los destinos predeterminados.  
  
 Los proyectos importados pueden tener sus propios atributos `DefaultTargets`.  El primer atributo `DefaultTargets` encontrado determina qué destinos predeterminados se ejecutarán.  
  
 Para obtener más información, vea [Cómo: Especificar qué destino utilizar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Primer destino  
 Si no hay destinos iniciales, destinos predeterminados o destinos de la línea de comandos, MSBuild ejecutará el primer destino que encuentre en el archivo del proyecto o en cualquier archivo del proyecto importado.  
  
## Dependencias de destinos  
 Los destinos pueden describir relaciones de dependencia entre sí.  El atributo `DependsOnTargets` indica que un destino depende de otros destinos.  Por ejemplo,  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 indica a MSBuild que el destino de `Serve` depende del destino de `Chop` y destino de `Cook`.  MSBuild ejecuta el destino de `Chop` y a continuación, ejecuta el destino de `Cook` antes de ejecutar el destino de `Serve`.  
  
## Antes de destinos y los destinos After  
 En MSBuild 4.0, puede especificar el orden de destinos utilizando los atributos `AfterTargets` y `BeforeTargets`.  
  
 Considere el script siguiente.  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Para crear un destino `Optimize` intermedia que se ejecute después del destino de `Compile`, pero antes del destino de `Link`, agregue el destino siguiente en cualquier parte del elemento de `Project`.  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## Determinar el orden de compilación de destinos  
 MSBuild determina el orden de compilación de destinos del modo siguiente:  
  
1.  se ejecutan los destinos de `InitialTargets`.  
  
2.  Se ejecutan los destinos especificados en la línea de comandos por el modificador **\/target**.  Si no especifica ningún destino en la línea de comandos, se ejecutan los destinos de `DefaultTargets`.  Si no está presente, el primer destino encontrado se ejecuta.  
  
3.  Se evalúa el atributo `Condition` del destino.  Si el atributo de `Condition` está presente y se evalúa como `false`, el destino no se ejecuta y no tiene ningún otro efecto en la compilación.  
  
4.  Antes de que se ejecute un destino, se ejecutan sus destinos `DependsOnTargets`.  
  
5.  Antes de que se ejecute un destino, se ejecuta cualquier destino que lo enumere en un atributo `BeforeTargets`.  
  
6.  Antes de que se ejecute un destino, se comparan sus atributos `Inputs` y `Outputs`.  Si MSBuild determina que los archivos de salida no están actualizados con respecto al archivo o archivos de entrada correspondientes, MSBuild ejecuta el destino.  De lo contrario, MSBuild omite el destino.  
  
7.  Después de ejecutarse u omitirse un destino, se ejecuta cualquier destino que lo enumere en un atributo `AfterTargets`.  
  
## Vea también  
 [Destinos](../msbuild/msbuild-targets.md)