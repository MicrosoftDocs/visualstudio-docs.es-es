---
title: "Orden de compilación de destinos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: "18"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7fbe62b55fde85127756b9d73be333068bb9aad3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="target-build-order"></a>Orden de compilación de destinos
Los destinos se deben ordenar si la entrada a un destino depende de la salida de otro destino. Puede usar estos atributos para especificar el orden en el que se ejecutan los destinos:  
  
-   `InitialTargets`. Este atributo `Project` especifica los destinos que se ejecutarán en primer lugar, incluso si los destinos se especifican en la línea de comandos o en el atributo `DefaultTargets`.  
  
-   `DefaultTargets`. Este atributo `Project` especifica qué destinos se ejecutan si un destino no se especifica explícitamente en la línea de comandos.  
  
-   `DependsOnTargets`. Este atributo `Target` especifica los destinos que se deben ejecutar antes de poder ejecutar este destino.  
  
-   `BeforeTargets` y `AfterTargets`. Estos atributos `Target` especifican que este destino se debe ejecutar antes o después de los destinos especificados (MSBuild 4.0).  
  
 Un destino nunca se ejecuta dos veces durante una compilación, incluso si un destino subsiguiente en la compilación depende de él. Una vez que se ha ejecutado un destino, su contribución a la compilación finaliza.  
  
 Los destinos pueden tener un atributo `Condition`. Si la condición especificada se evalúa como `false`, el destino no se ejecuta y no tiene ningún efecto en la compilación. Para obtener más información sobre las condiciones, consulte [Condiciones](../msbuild/msbuild-conditions.md).  
  
## <a name="initial-targets"></a>Destinos iniciales  
 El atributo `InitialTargets` del elemento [Project](../msbuild/project-element-msbuild.md) especifica los destinos que se ejecutarán en primer lugar, incluso si los destinos se especifican en la línea de comandos o en el atributo `DefaultTargets`. Los destinos iniciales se utilizan normalmente para la comprobación de errores.  
  
 El valor del atributo `InitialTargets` puede ser una lista delimitada por punto y coma, y ordenada de destinos. En el ejemplo siguiente se especifica que el destino `Warm` se ejecuta y, a continuación, se ejecuta el destino `Eject`.  
  
```xml  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Los proyectos importados pueden tener sus propios atributos `InitialTargets`. Todos los destinos iniciales se agregan conjuntamente y se ejecutan en orden.  
  
 Para obtener más información, consulte [Cómo: Especificar qué destino utilizar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="default-targets"></a>Destinos predeterminados  
 El atributo `DefaultTargets` del elemento [Project](../msbuild/project-element-msbuild.md) especifica qué destinos se compilan si un destino no se especifica explícitamente en la línea de comandos.  
  
 El valor del atributo `DefaultTargets` puede ser una lista delimitada por punto y coma, y ordenada de destinos predeterminados. En el ejemplo siguiente se especifica que el destino `Clean` se ejecuta y, a continuación, se ejecuta el destino `Build`.  
  
```xml  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Puede invalidar los destinos predeterminados mediante el modificador **/target** en la línea de comandos. En el ejemplo siguiente se especifica que el destino `Build` se ejecuta y, a continuación, se ejecuta el destino `Report`. Al especificar los destinos de esta manera, los destinos predeterminados se omiten.  
  
 `msbuild /target:Build;Report`  
  
 Si se especifican tanto destinos iniciales como destinos predeterminados y si no se especifica ningún destino de línea de comandos, MSBuild ejecuta los objetivos iniciales primero y, a continuación, ejecuta los destinos predeterminados.  
  
 Los proyectos importados pueden tener sus propios atributos `DefaultTargets`. El primer atributo `DefaultTargets` encontrado determina qué destinos predeterminados se ejecutarán.  
  
 Para obtener más información, consulte [Cómo: Especificar qué destino utilizar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="first-target"></a>Primer destino  
 Si no hay destinos iniciales, destinos predeterminados ni destinos de línea de comandos, MSBuild ejecuta el primer destino que encuentra en el archivo del proyecto o en cualquier archivo del proyecto importado.  
  
## <a name="target-dependencies"></a>Dependencias de destino  
 Los destinos pueden describir relaciones de dependencia entre sí. El atributo `DependsOnTargets` indica que un destino depende de otros destinos. Por ejemplo,  
  
```xml  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 indica a MSBuild que el destino `Serve` depende de los destinos `Chop` y `Cook`. MSBuild ejecuta el destino `Chop` y, a continuación, ejecuta el destino `Cook` antes de ejecutar el destino `Serve`.  
  
## <a name="beforetargets-and-after-targets"></a>BeforeTargets y AfterTargets  
 En MSBuild 4.0, puede especificar el orden de los destinos mediante los atributos `BeforeTargets` y `AfterTargets`.  
  
 Considere el script siguiente.  
  
```xml  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Para crear un destino intermedio `Optimize` que se ejecuta después del destino `Compile`, pero antes del destino `Link`, agregue el destino siguiente en cualquier lugar en el elemento `Project`.  
  
```xml  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## <a name="determining-the-target-build-order"></a>Determinar el orden de compilación de destinos  
 MSBuild determina el orden de compilación de destinos como sigue:  
  
1.  Se ejecutan los destinos `InitialTargets`.  
  
2.  Se ejecutan los destinos especificados en la línea de comandos mediante el modificador **/target**. Si no se especifica ningún destino en la línea de comandos, se ejecutan los destinos `DefaultTargets`. Si ninguno está presente, se ejecuta el primer destino que se encuentre.  
  
3.  Se evalúa el atributo de destino `Condition`. Si el atributo `Condition` está presente y se evalúa como `false`, el destino no se ejecuta y no tiene ningún efecto adicional en la compilación.  
  
4.  Antes de ejecutar un destino, se ejecutan los destinos `DependsOnTargets`.  
  
5.  Antes de ejecutar un destino, se ejecuta cualquier destino que lo enumere en un atributo `BeforeTargets`.  
  
6.  Antes de ejecutar un destino, se comparan los atributos `Inputs` y `Outputs`. Si MSBuild determina que los archivos de salida no están actualizados con respecto a los archivos de entrada correspondientes, MSBuild ejecuta el destino. De lo contrario, MSBuild omite el destino.  
  
7.  Después de ejecutar u omitir un destino, se ejecuta cualquier destino que lo enumere en un atributo `AfterTargets`.  
  
## <a name="see-also"></a>Vea también  
 [Destinos](../msbuild/msbuild-targets.md)