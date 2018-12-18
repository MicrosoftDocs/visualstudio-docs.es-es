---
title: Objetivos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3700074a1d087c0626a86559ff1342698d8a4628
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176120"
---
# <a name="msbuild-targets"></a>Destinos de MSBuild
Los destinos agrupan tareas en un orden concreto y permiten que el proceso de compilación se factorice en unidades más pequeñas. Por ejemplo, un destino podría eliminar todos los archivos del directorio de salida para prepararlo para la compilación, mientras que otro compila las entradas para el proyecto y las coloca en el directorio vacío. Para más información sobre las tareas, consulte [Tareas](../msbuild/msbuild-tasks.md).  
  
## <a name="declare-targets-in-the-project-file"></a>Declaración de destinos en el archivo de proyecto  
 Los destinos se declaran en un archivo del proyecto con el elemento [Target](../msbuild/target-element-msbuild.md). Por ejemplo, el código XML siguiente crea un destino denominado Construct que, a continuación, llama a la tarea Csc con el tipo de elemento de compilación.  
  
```xml  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Al igual que las propiedades de MSBuild, los destinos se pueden redefinir. Por ejemplo,  
  
```xml  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Si AfterBuild se ejecuta, muestra solamente "Second occurrence".  
  
## <a name="target-build-order"></a>Orden de compilación de destinos  
 Los destinos se deben ordenar si la entrada a un destino depende de la salida de otro destino. Hay varias maneras de especificar el orden de ejecución de los destinos.  
  
-   Destinos iniciales  
  
-   Destinos predeterminados  
  
-   Primer destino  
  
-   Dependencias de destino  
  
-   `BeforeTargets` y `AfterTargets` (MSBuild 4.0)  

Un destino nunca se ejecuta dos veces durante una compilación única, incluso si un destino subsiguiente en la compilación depende de él. Una vez que se ejecuta un destino, su contribución a la compilación finaliza.  

Para obtener detalles y más información sobre el orden de compilación de destinos, vea [Orden de compilación de destinos](../msbuild/target-build-order.md).  

## <a name="target-batching"></a>Procesamiento por lotes de destinos  
Un elemento de destino puede tener un atributo `Outputs` que especifique los metadatos en el formato %(\<Metadatos>). Si es así, MSBuild ejecuta el destino una vez para cada valor de metadatos único, y agrupa o "procesa por lotes" los elementos que tienen ese valor de metadatos. Por ejemplo,  
  
```xml  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 procesa por lotes los elementos de referencia por sus metadatos RequiredTargetFramework. El resultado del destino es similar a lo siguiente:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 El procesamiento por lotes de destinos apenas se usa en las compilaciones reales. El procesamiento por lotes de tareas es más habitual. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Compilaciones incrementales  
 Las compilaciones incrementales son compilaciones que se optimizan para que no se ejecuten los destinos con archivos de salida que están actualizados con respecto a sus archivos de entrada correspondientes. Un elemento de destino puede tener atributos `Inputs` y `Outputs`, que indican qué elementos espera el destino como entrada y qué elementos genera como salida.  
  
 Si todos los elementos de salida están actualizados, MSBuild omite el destino, lo que mejora significativamente la velocidad de compilación. Esto se denomina una compilación incremental del destino. Si solo están actualizados algunos archivos, MSBuild ejecuta el destino sin los elementos actualizados. Esto se denomina una compilación incremental parcial del destino. Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Cómo: Utilizar el mismo destino en varios archivos de proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)