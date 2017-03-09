---
title: "Elementos de MSBuild | Microsoft Docs"
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
  - "MSBuild, elementos"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elementos de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elementos de MSBuild son entradas del sistema de compilación, y representan normalmente archivos. Los elementos se agrupan en tipos de elementos basados en los nombres de elemento. Los tipos de elemento son listas de elementos con nombre que se pueden usar como parámetros de las tareas. Las tareas utilizan los valores de los elementos para llevar a cabo los pasos del proceso de compilación.  
  
 Dado que el nombre de elementos viene determinado por el tipo de elemento al que pertenecen, los términos "elemento" y "valor de elemento" pueden usarse indistintamente.  
  
 **En este tema**  
  
-   [Creación de elementos en un archivo de proyecto](#BKMK_Creating1)  
  
-   [Crear elementos durante la ejecución](#BKMK_Creating2)  
  
-   [Hacer referencia a elementos en un archivo de proyecto](#BKMK_ReferencingItems)  
  
-   [Uso de caracteres comodín para especificar elementos](#BKMK_Wildcards)  
  
-   [Utilizar el atributo Exclude](#BKMK_ExcludeAttribute)  
  
-   [Metadatos de elemento](#BKMK_ItemMetadata)  
  
    -   [Hacer referencia a metadatos de elementos en un archivo de proyecto](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadatos de elementos conocidos](#BKMK_WellKnownItemMetadata)  
  
    -   [Transformar tipos de elemento mediante metadatos](#BKMK_Transforming)  
  
-   [Definiciones de elementos](#BKMK_ItemDefinitions)  
  
-   [Atributos para los elementos de ItemGroup de un destino](#BKMK_AttributesWithinTargets)  
  
    -   [Quite el atributo](#BKMK_RemoveAttribute)  
  
    -   [Atributo KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Atributo RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Atributo KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Creación de elementos en un archivo de proyecto  
 Elementos se declara en el archivo de proyecto como elemento secundario de un [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elemento. El nombre del elemento secundario es el tipo del elemento. El `Include` atributo del elemento especifica los elementos (archivos) que se incluirá con ese tipo de elemento. Por ejemplo, el código XML siguiente crea un tipo de elemento denominado `Compile`, que incluye dos archivos.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 El elemento "file2.cs" no reemplaza el elemento "file1.cs"; en su lugar, se anexa el nombre de archivo a la lista de valores para el `Compile` tipo de elemento. No se puede quitar un elemento de un tipo de elemento durante la fase de evaluación de una compilación.  
  
 El siguiente código XML crea el mismo tipo de elemento declarando ambos archivos en una `Include` atributo. Observe que los nombres de archivo están separados por un punto y coma.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Crear elementos durante la ejecución  
 Los elementos que están fuera de [destino](../msbuild/target-element-msbuild.md) elementos se les asignan valores durante la fase de evaluación de una compilación. Durante la fase de ejecución posteriores, los elementos se pueden crear o modificar de las maneras siguientes:  
  
-   Cualquier tarea puede emitir un elemento. Para emitir un elemento, la [tarea](../msbuild/task-element-msbuild.md) elemento debe tener un elemento secundario [salida](../msbuild/output-element-msbuild.md) elemento que tiene un `ItemName` atributo.  
  
-   El [CreateItem](../msbuild/createitem-task.md) tarea puede emitir un elemento. (en desuso).  
  
-   A partir de .NET Framework 3.5, `Target` pueden contener elementos [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementos que pueden contener elementos de elemento.  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Hacer referencia a elementos en un archivo de proyecto  
 Para hacer referencia a tipos de elemento en el archivo del proyecto, use la sintaxis @(`ItemType`). Por ejemplo, podría hacer referencia al tipo de elemento en el ejemplo anterior utilizando `@(Compile)`. Con esta sintaxis, puede pasar elementos a las tareas especificando el tipo de elemento como un parámetro de la tarea. Para obtener más información, vea [Cómo: seleccionar los archivos de compilación](../msbuild/how-to-select-the-files-to-build.md).  
  
 De manera predeterminada, los elementos de un tipo de elemento se separan con punto y coma (;) cuando se expande. Puede utilizar la sintaxis @(*ItemType*, '*separador*') para especificar un separador distinto del predeterminado. Para obtener más información, vea [Cómo: mostrar una lista de elementos separados por comas](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Uso de caracteres comodín para especificar elementos  
 ¿Puede usar el **, \*, y? caracteres comodín para especificar un grupo de archivos como entradas para una compilación en lugar de enumerar cada archivo por separado.  
  
-   ¿El? carácter comodín coincide con un único carácter.  
  
-   El * carácter comodín coincide con cero o más caracteres.  
  
-   El ** secuencia de caracteres comodín coincide con una ruta de acceso parcial.  
  
 Por ejemplo, puede especificar todos los archivos .cs en el directorio que contiene el archivo de proyecto mediante el elemento siguiente en el archivo de proyecto.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 El elemento siguiente selecciona todos los archivos .vb en la unidad D::  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Para obtener más información acerca de los caracteres comodín, vea [Cómo: seleccionar los archivos de compilación](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Utilizar el atributo Exclude  
 Elementos pueden contener el `Exclude` atributo, que excluye elementos específicos (archivos) del tipo de elemento. El `Exclude` atributo se usa normalmente junto con caracteres comodín. Por ejemplo, el código XML siguiente agrega todos los archivos .cs en el directorio para el tipo de elemento CSFile, excepto los `DoNotBuild.cs` archivos.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 El `Exclude` atributo afecta únicamente los elementos agregados por el `Include` atributo en el elemento que contiene ambos. El ejemplo siguiente no excluir el archivo Form1.cs, que se agregó en el elemento anterior.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Para obtener más información, vea [Cómo: excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> Metadatos de elemento  
 Los elementos pueden contener metadatos además de la información en el `Include` y `Exclude` atributos. Estos metadatos se pueden utilizar las tareas que requieren más información acerca de los elementos o a los destinos y tareas por lotes. Para obtener más información, consulte [procesamiento por lotes](../msbuild/msbuild-batching.md).  
  
 Los metadatos son una colección de pares clave-valor que se declaran en el archivo de proyecto como elementos secundarios de un elemento. El nombre del elemento secundario es el nombre de los metadatos y el valor del elemento secundario es el valor de los metadatos.  
  
 Los metadatos están asociados con el elemento que lo contiene. Por ejemplo, se agrega el siguiente código XML `Culture` metadatos que tiene el valor `Fr` "one.cs" y los elementos "two.cs" de la CSFile el tipo de elemento.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Un elemento puede tener cero o varios valores de metadatos. Puede cambiar los valores de metadatos en cualquier momento. Si establece los metadatos en un valor vacío, se quita eficazmente desde la compilación.  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Hacer referencia a metadatos de elementos en un archivo de proyecto  
 Puede hacer referencia a los metadatos de elemento en el archivo del proyecto utilizando la sintaxis %(`ItemMetadataName`). Si existe ambigüedad, se puede calificar una referencia utilizando el nombre del tipo de elemento. Por ejemplo, puede especificar %(*ItemType.ItemMetaDataName*). El ejemplo siguiente utiliza los metadatos de la pantalla para procesar por lotes la tarea de mensaje. Para obtener más información acerca de cómo usar los metadatos de elemento para el procesamiento por lotes, consulte [metadatos de elementos en procesamiento por lotes de tarea](../msbuild/item-metadata-in-task-batching.md).  
  
```  
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
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Metadatos de elementos conocidos  
 Cuando se agrega un elemento a un tipo de elemento, que se le asignan metadatos conocidos. Por ejemplo, todos los elementos tienen los metadatos conocidos `%(Filename)`, cuyo valor es el nombre de archivo del elemento. Para obtener más información, consulte [Well-Known metadatos del elemento](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Transformar tipos de elemento mediante metadatos  
 Listas de elementos puede transformar en nuevas listas de elementos mediante metadatos. Por ejemplo, puede transformar un tipo de elemento `CppFiles` que tiene elementos que representan archivos .cpp en una lista correspondiente de archivos .obj mediante la expresión `@(CppFiles -> '%(Filename).obj')`.  
  
 El código siguiente crea un `CultureResource` de elemento de tipo que contiene copias de todos los `EmbeddedResource` elementos con `Culture` metadatos. La `Culture` valor de metadatos se convierte en el valor de los nuevos metadatos `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Para obtener más información, consulte [transforma](../msbuild/msbuild-transforms.md).  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Definiciones de elementos  
 A partir de .NET Framework 3.5, puede agregar metadatos predeterminados a cualquier tipo de elemento mediante la [elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Al igual que los metadatos conocidos, los metadatos predeterminados están asociado con todos los elementos del tipo de elemento que especifique. Se pueden reemplazar explícitamente los metadatos predeterminados en una definición de elemento. Por ejemplo, el siguiente código XML proporciona el `Compile` elementos "one.cs" y "three.cs" los metadatos `BuildDay` con el valor "Monday". El código proporciona al elemento "two.cs" los metadatos `BuildDay` con el valor "Tuesday".  
  
```  
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
  
 Para obtener más información, consulte [definiciones de elementos](../msbuild/item-definitions.md).  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Atributos para los elementos de ItemGroup de un destino  
 A partir de .NET Framework 3.5, `Target` pueden contener elementos [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementos que pueden contener elementos de elemento. Los atributos de esta sección son válidos cuando se especifican para un elemento en un `ItemGroup` que se encuentra en un `Target`.  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Quite el atributo  
 Los elementos de un `ItemGroup` de un destino puede contener el `Remove` atributo, que quita los elementos específicos (archivos) desde el tipo de elemento. Este atributo se introdujo en .NET Framework 3.5.  
  
 El ejemplo siguiente quita todos los archivos .config del tipo de elemento de compilación.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Atributo KeepMetadata  
 Si se genera un elemento dentro de un destino, el elemento puede contener el `KeepMetadata` atributo. Si se especifica este atributo, solo los metadatos que se especifica en la lista delimitada por punto y coma de nombres se transferirán desde el elemento de origen para el elemento de destino. Es equivalente a no se especifica como un valor vacío para este atributo. El `KeepMetadata` atributo se introdujo en .NET Framework 4.5.  
  
 En el ejemplo siguiente se muestra cómo utilizar el `KeepMetadata` atributo.  
  
```  
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
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Atributo RemoveMetadata  
 Si se genera un elemento dentro de un destino, el elemento puede contener el `RemoveMetadata` atributo. Si se especifica este atributo, la todos los metadatos se transfieren desde el elemento de origen para el elemento de destino excepto aquellos cuyos nombres figuran en la lista delimitada por punto y coma de nombres. Es equivalente a no se especifica como un valor vacío para este atributo. El `RemoveMetadata` atributo se introdujo en .NET Framework 4.5.  
  
 En el ejemplo siguiente se muestra cómo utilizar el `RemoveMetadata` atributo.  
  
```  
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
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Atributo KeepDuplicates  
 Si se genera un elemento dentro de un destino, el elemento puede contener el `KeepDuplicates` atributo. `KeepDuplicates` es un `Boolean` atributo que especifica si se debe agregar un elemento al grupo de destino si el elemento es un duplicado exacto de un elemento existente.  
  
 Si el elemento de origen y de destino tienen el mismo valor de inclusión pero distintos metadatos, el elemento se agrega aunque `KeepDuplicates` está establecido en `false`. Es equivalente a no se especifica como un valor vacío para este atributo. El `KeepDuplicates` atributo se introdujo en .NET Framework 4.5.  
  
 En el ejemplo siguiente se muestra cómo utilizar el `KeepDuplicates` atributo.  
  
```  
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
 [MSBuild](../msbuild/msbuild1.md)   
 [Cómo: seleccionar los archivos de compilación](../msbuild/how-to-select-the-files-to-build.md)   
 [Cómo: excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Cómo: mostrar una lista de elementos separada por comas](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definiciones de elementos](../msbuild/item-definitions.md)   
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)   
 [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)