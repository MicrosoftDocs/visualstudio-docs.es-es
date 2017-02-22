---
title: "Objetivos de MSBuild | Microsoft Docs"
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
  - "MSBuild, destinos"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Objetivos de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los destinos agrupan las tareas entre sí en un orden concreto y permiten factorizar el proceso de compilación en unidades más pequeñas.  Por ejemplo, un destino podría eliminar todos los archivos del directorio de salida a fin de prepararlo para la compilación, y otro compilar las entradas del proyecto y colocarlas en el directorio vacío.  Para obtener más información sobre las tareas, vea [Tareas](../msbuild/msbuild-tasks.md).  
  
## Declarar destinos en el archivo de proyecto  
 Los destinos se declaran en un archivo de proyecto con el elemento [Target](../msbuild/target-element-msbuild.md).  Por ejemplo, el código XML siguiente crea un destino denominado Construct que, a continuación, llama a la tarea Csc con el tipo de elemento Compile.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Al igual que las propiedades de MSBuild, los destinos se pueden volver a definir.  Por ejemplo,  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Si AfterBuild se ejecuta, muestra solamente "Second occurrence".  
  
## Orden de compilación de destinos  
 Los destinos se deben ordenar si la entrada a un destino depende de la salida de otro destino.  Hay varias maneras de especificar el orden en el que se ejecutan los destinos.  
  
-   Destinos iniciales  
  
-   Destinos predeterminados  
  
-   Primer destino  
  
-   Dependencias de destinos  
  
-   `BeforeTargets` y `AfterTargets` \(MSBuild 4.0\)  
  
 Un destino nunca se ejecuta dos veces durante una sola compilación, aunque un destino subsiguiente en la compilación dependa de él.  Una vez ejecutado un destino, su contribución a la compilación se ha completado.  
  
 Para obtener detalles y más información sobre el orden de compilación de destinos, vea [Orden de compilación de destinos](../msbuild/target-build-order.md).  
  
## Procesamiento por lotes de destinos  
 Un elemento de destino puede tener un atributo `Outputs` que especifica los metadatos en la forma %\(Metadata\).  En tal caso, MSBuild ejecuta el destino una vez por cada valor de metadatos único, agrupación o "procesamiento por lotes" de los elementos que tienen ese valor de metadatos.  Por ejemplo,  
  
```  
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
  
 procesa por lotes los elementos Reference mediante sus metadatos de RequiredTargetFramework.  La salida del destino presenta el siguiente aspecto:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 El procesamiento por lotes de destinos raramente se utiliza en compilaciones reales.  El procesamiento por lotes de tareas es más común.  Para obtener más información, vea [Procesamiento por lotes](../msbuild/msbuild-batching.md).  
  
## Compilaciones incrementales  
 Las compilaciones incrementales son compilaciones que se optimizan para que no se ejecuten los destinos con archivos de salida que están actualizados con respecto a sus archivos de entrada correspondientes.  Un elemento de destino puede tener los atributos `Inputs` y `Outputs`, indicando qué elementos espera el destino como entrada y qué elementos genera como salida.  
  
 Si todos los elementos de salida están actualizados, MSBuild omite el destino, con lo que mejora significativamente la velocidad de compilación.  Este proceso recibe el nombre de compilación incremental del destino.  Si solo están actualizados algunos archivos, MSBuild ejecuta el destino sin los elementos actualizados.  Este proceso recibe el nombre de compilación incremental parcial del destino.  Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md).  
  
## Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Cómo: Utilizar el mismo destino en varios archivos de proyecto](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)