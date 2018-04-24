---
title: Elementos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d860d2d80cbb93c36a75c56a73895a401bc47660
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-items"></a>Elementos de MSBuild
Los elementos de MSBuild son entradas del sistema de compilación y suelen representar archivos. Se agrupan en tipos de elemento de acuerdo con sus nombres de elemento. Los tipos de elemento son listas de elementos con nombre que se pueden usar como parámetros de las tareas. Las tareas utilizan los valores de los elementos para llevar a cabo los pasos del proceso de compilación.  
  
 Dado que el nombre de los elementos viene determinado por el tipo de elemento al que pertenecen, los términos "elemento" y "valor de elemento" se pueden utilizar indistintamente.  
  
 **En este tema**  
  
-   [Crear elementos en un archivo del proyecto](#BKMK_Creating1)  
  
-   [Crear elementos durante la ejecución](#BKMK_Creating2)  
  
-   [Hacer referencia a elementos en un archivo del proyecto](#BKMK_ReferencingItems)  
  
-   [Utilizar caracteres comodín para especificar elementos](#BKMK_Wildcards)  
  
-   [Utilizar el atributo Exclude](#BKMK_ExcludeAttribute)  
  
-   [Metadatos de elementos](#BKMK_ItemMetadata)  
  
    -   [Hacer referencia a metadatos de elementos en un archivo del proyecto](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadatos de elementos conocidos](#BKMK_WellKnownItemMetadata)  
  
    -   [Transformar tipos de elemento mediante metadatos](#BKMK_Transforming)  
  
-   [Definiciones de elementos](#BKMK_ItemDefinitions)  
  
-   [Atributos de los elementos de un ItemGroup de un destino](#BKMK_AttributesWithinTargets)  
  
    -   [Atributo Remove](#BKMK_RemoveAttribute)  
  
    -   [Atributo KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Atributo RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Atributo KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a> Crear elementos en un archivo del proyecto  
 Declara los elementos del archivo del proyecto como elementos secundarios de un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). El nombre del elemento secundario es el tipo del elemento. El atributo `Include` del elemento especifica los elementos (archivos) que se incluirán con ese tipo de elemento. Por ejemplo, el código XML siguiente crea un tipo de elemento denominado `Compile`, que incluye dos archivos.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 El elemento "file2.cs" no reemplaza el elemento "file1.cs"; en su lugar, se anexa el nombre de archivo a la lista de valores del tipo de elemento `Compile`. No se puede quitar un elemento de un tipo de elemento durante la fase de evaluación de una compilación.  
  
 El código XML siguiente crea el mismo tipo de elemento declarando ambos archivos en un atributo `Include`. Observe que los nombres de archivo están separados por un punto y coma.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a> Crear elementos durante la ejecución  
 Durante la fase de evaluación de una compilación, se asignan valores a los elementos que están fuera de los elementos [Target](../msbuild/target-element-msbuild.md). En la siguiente fase de la ejecución, se pueden crear o modificar elementos como se indica a continuación:  
  
-   Cualquier tarea puede emitir un elemento. Para emitir un elemento, el elemento [Task](../msbuild/task-element-msbuild.md) debe tener un elemento [Output](../msbuild/output-element-msbuild.md) secundario que tenga un atributo `ItemName`.  
  
-   La tarea [CreateItem](../msbuild/createitem-task.md) puede emitir un elemento. (en desuso).  
  
-   A partir de .NET Framework 3.5, los elementos `Target` pueden contener elementos [ItemGroup](../msbuild/itemgroup-element-msbuild.md) que pueden contener elementos de elemento.  
  
##  <a name="BKMK_ReferencingItems"></a> Hacer referencia a elementos en un archivo del proyecto  
 Para hacer referencia a tipos de elemento en el archivo del proyecto, utilice la sintaxis @(`ItemType`). Por ejemplo, podría hacer referencia al tipo de elemento del ejemplo anterior utilizando `@(Compile)`. Con esta sintaxis, puede pasar elementos a las tareas especificando el tipo de elemento como un parámetro de la tarea. Para obtener más información, consulte [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md).  
  
 De manera predeterminada, los elementos de un tipo de elemento se separan con punto y coma (;) cuando se expanden. Puede utilizar la sintaxis @(*ItemType*, '*separator*') para especificar un separador distinto del predeterminado. Para obtener más información, consulte [Cómo: Mostrar una lista de elementos separados por comas](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a> Utilizar caracteres comodín para especificar elementos  
 Puede utilizar los caracteres comodín **, \* y ? para especificar un grupo de archivos como entradas para una compilación en lugar de enumerar cada archivo por separado.  
  
-   El carácter comodín ? coincide con un único carácter.  
  
-   El carácter comodín * coincide con cero o más caracteres.  
  
-   La secuencia de caracteres comodín ** coincide con una ruta de acceso parcial.  
  
 Por ejemplo, puede utilizar el elemento siguiente en el archivo del proyecto para especificar todos los archivos .cs del directorio que contiene el archivo del proyecto.  
  
```xml  
<CSFile Include="*.cs"/>  
```  
  
 El elemento siguiente selecciona todos los archivos .vb en la unidad D:  
  
```xml  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Para obtener más información sobre los caracteres comodín, consulte [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a> Utilizar el atributo Exclude  
 Los elementos de elemento pueden contener el atributo `Exclude`, que excluye elementos específicos (archivos) del tipo de elemento. El `Exclude` atributo se usa normalmente junto con caracteres comodín. Por ejemplo, el código XML siguiente agrega todos los archivos .cs del directorio al tipo de elemento CSFile, excepto el archivo `DoNotBuild.cs`.  
  
```xml  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 El atributo `Exclude` solamente afecta a los elementos agregados por el atributo `Include` en el elemento de elemento que contiene ambos. En el ejemplo siguiente no se excluiría el archivo Form1.cs, que se ha agregado en el elemento de elemento anterior.  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Para obtener más información, consulte [Cómo: Excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a> Metadatos de elementos  
 Los elementos pueden contener metadatos además de la información recopilada en los atributos `Include` y `Exclude`. Estos metadatos pueden ser utilizados por las tareas que requieren más información sobre los elementos o para procesar por lotes tareas y destinos. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).  
  
 Los metadatos son una colección de pares clave-valor que se declaran en el archivo del proyecto como elementos secundarios de un elemento de elemento. El nombre de los metadatos es el nombre del elemento secundario, y el valor de los metadatos es el valor del elemento secundario.  
  
 Los metadatos están asociados al elemento de elemento que los contiene. Por ejemplo, el siguiente código XML agrega metadatos `Culture` que tienen el valor `Fr` a los elementos "one.cs" y "two.cs" del tipo de elemento CSFile.  
  
```xml  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Un elemento puede tener cero o varios valores de metadatos. Puede cambiar los valores de los metadatos en cualquier momento. Si establece los metadatos en un valor vacío, se quitan eficazmente de la compilación.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Hacer referencia a metadatos de elementos en un archivo del proyecto  
 Puede hacer referencia a los metadatos de elementos en el archivo del proyecto mediante la sintaxis %(`ItemMetadataName`). Si existe ambigüedad, se puede calificar una referencia mediante el nombre del tipo de elemento. Por ejemplo, puede especificar %(*ItemType.ItemMetaDataName*). En el ejemplo siguiente se utilizan los metadatos Display para procesar por lotes la tarea Message. Para obtener más información sobre cómo utilizar los metadatos de elementos para el procesamiento por lotes, consulte [Metadatos de elementos en el procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Metadatos de elementos conocidos  
 Cuando se agrega un elemento a un tipo de elemento, se le asignan metadatos conocidos. Por ejemplo, todos los elementos tienen los metadatos conocidos `%(Filename)`, cuyo valor es el nombre de archivo del elemento. Para obtener más información, consulte [Metadatos de elementos conocidos](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Transformar tipos de elemento mediante metadatos  
 Puede transformar listas de elementos en nuevas listas de elementos mediante metadatos. Por ejemplo, puede transformar un tipo de elemento `CppFiles` que tiene elementos que representan archivos .cpp en una lista correspondiente de archivos .obj mediante la expresión `@(CppFiles -> '%(Filename).obj')`.  
  
 El código siguiente crea un tipo de elemento `CultureResource` que contiene copias de todos los elementos `EmbeddedResource` con metadatos `Culture`. El valor de los metadatos `Culture` se convierte en el valor de los nuevos metadatos `CultureResource.TargetDirectory`.  
  
```xml  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a> Definiciones de elementos  
 A partir de .NET Framework 3.5, puede agregar metadatos predeterminados a cualquier tipo de elemento mediante el [elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Al igual que los metadatos conocidos, los metadatos predeterminados están asociados a todos los elementos del tipo de elemento que especifique. Puede invalidar explícitamente los metadatos predeterminados en una definición de elemento. Por ejemplo, el siguiente código XML proporciona los elementos `Compile` "one.cs" y "three.cs" a los metadatos `BuildDay` con el valor "Monday". El código proporciona el elemento "two.cs" a los metadatos `BuildDay` con el valor "Tuesday".  
  
```xml  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Para obtener más información, consulte [Definiciones de elementos](../msbuild/item-definitions.md).  
  
##  <a name="BKMK_AttributesWithinTargets"></a> Atributos de los elementos de un ItemGroup de un destino  
 A partir de .NET Framework 3.5, los elementos `Target` pueden contener elementos [ItemGroup](../msbuild/itemgroup-element-msbuild.md) que pueden contener elementos de elemento. Los atributos de esta sección son válidos cuando se especifican para un elemento en un `ItemGroup` que se encuentra en un `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Atributo Remove  
 Los elementos de un `ItemGroup` de un destino pueden contener el atributo `Remove`, que quita los elementos específicos (archivos) del tipo de elemento. Este atributo se introdujo en .NET Framework 3.5.  
  
 En el ejemplo siguiente se quitan todos los archivos .config del tipo de elemento Compile.  
  
```xml  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> Atributo KeepMetadata  
 Si se genera un elemento dentro de un destino, el elemento de elemento puede contener el atributo `KeepMetadata`. Si se especifica este atributo, solo los metadatos que se especifican en la lista delimitada por punto y coma de nombres se transferirán desde el elemento de origen al elemento de destino. Un valor vacío para este atributo equivale a no especificarlo. El atributo `KeepMetadata` se introdujo en .NET Framework 4.5.  
  
 En el ejemplo siguiente se muestra cómo utilizar el atributo `KeepMetadata`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> Atributo RemoveMetadata  
 Si se genera un elemento dentro de un destino, el elemento de elemento puede contener el atributo `RemoveMetadata`. Si se especifica este atributo, todos los metadatos se transfieren desde el elemento de origen al elemento de destino excepto aquellos cuyos nombres figuran en la lista de nombres delimitada por punto y coma. Un valor vacío para este atributo equivale a no especificarlo. El atributo `RemoveMetadata` se introdujo en .NET Framework 4.5.  
  
 En el ejemplo siguiente se muestra cómo utilizar el atributo `RemoveMetadata`.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> Atributo KeepDuplicates  
 Si se genera un elemento dentro de un destino, el elemento de elemento puede contener el atributo `KeepDuplicates`. `KeepDuplicates` es un atributo `Boolean` que especifica si se debe agregar al grupo de destino un elemento que es un duplicado exacto de un elemento existente.  
  
 Si los elementos de origen y de destino tienen el mismo valor Include, pero distintos metadatos, los elementos se agregan aunque `KeepDuplicates` esté establecido en `false`. Un valor vacío para este atributo equivale a no especificarlo. El atributo `KeepDuplicates` se introdujo en .NET Framework 4.5.  
  
 En el ejemplo siguiente se muestra cómo utilizar el atributo `KeepDuplicates`.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)   
 [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md)   
 [Cómo: Excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Cómo: Mostrar una lista de elementos separados por comas](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definiciones de elementos](../msbuild/item-definitions.md)   
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)   
 [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)