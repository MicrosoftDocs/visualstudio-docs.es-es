---
title: "Comparar propiedades y elementos | Microsoft Docs"
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
  - "MSBuild, propiedades de msbuild"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comparar propiedades y elementos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elementos y propiedades de MSBuild se usan para pasar información a tareas, evaluar condiciones y almacenar valores que se pueden hacer referencia en el archivo del proyecto.  
  
-   Propiedades son pares de nombre y valor. Para obtener más información, consulte [Propiedades de MSBuild](../msbuild/msbuild-properties.md).  
  
-   Los elementos son objetos que representan normalmente archivos. Objetos de elemento pueden tener asociadas colecciones de metadatos. Metadatos son pares de nombre y valor. Para obtener más información, consulte [elementos](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Escalares y vectores  
 Dado que las propiedades de MSBuild son pares nombre-valor que tienen un solo valor de cadena, a menudo se describen como *escalares*. Dado que los tipos de elemento de MSBuild son listas de elementos, a menudo se describen como *vector*. Sin embargo, en la práctica, propiedades pueden representar varios valores y tipos de elemento pueden tener cero o uno de los elementos.  
  
### <a name="target-dependency-injection"></a>Inyección de dependencia de destino  
 Para ver cómo las propiedades pueden representar varios valores, considere la posibilidad de un patrón de uso común para agregar un destino a una lista de destinos que se crea. Esta lista normalmente se representa mediante un valor de propiedad, con los nombres de destino separados por punto y coma.  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 El `BuildDependsOn` propiedad se utiliza normalmente como argumento de un destino `DependsOnTargets` atributo, convirtiéndolo de hecho en una lista de elementos. Esta propiedad se puede invalidar para agregar un destino o para cambiar el orden de ejecución de destino. Por ejemplo,  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Agrega el destino CustomBuild a la lista de destino, lo que proporciona `BuildDependsOn` el valor `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 A partir de MSBuild 4.0, la inyección de dependencia de destino está en desuso. Utilice la `AfterTargets` y `BeforeTargets` atributos en su lugar. Para obtener más información, consulte [orden de generación de destino](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Conversiones entre cadenas y listas de elementos  
 MSBuild realiza conversiones de tipos de elemento y valores de cadena según sea necesario. Para ver cómo una lista de elementos puede convertirse en un valor de cadena, considere lo que sucede cuando un tipo de elemento se utiliza como el valor de una propiedad de MSBuild:  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 El tipo de elemento OutputDir tiene un `Include` atributo con el valor "archivo de clave\\; Certificados\\". MSBuild analiza esta cadena en dos elementos: KeyFiles\ y certificados\\. Cuando se utiliza el tipo de elemento OutputDir como el valor de la propiedad OutputDirList, MSBuild convierte o el tipo de elemento en la cadena separada por punto y coma "aplana" "archivo de clave\\; Certificados\\".  
  
## <a name="properties-and-items-in-tasks"></a>Propiedades y elementos en tareas  
 Propiedades y elementos se utilizan como entradas y salidas a las tareas de MSBuild. Para obtener más información, consulte [tareas](../msbuild/msbuild-tasks.md).  
  
 Propiedades se pasan a las tareas como atributos. Dentro de la tarea, una propiedad de MSBuild está representada por un tipo de propiedad cuyo valor se puede convertir a y desde una cadena. Los tipos de propiedad admitidos incluyen `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, y cualquier tipo que <xref:System.Convert.ChangeType%2A> puede controlar.  
  
 Los elementos se pasan a las tareas como <xref:Microsoft.Build.Framework.ITaskItem> objetos. Dentro de la tarea, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> representa el valor del elemento y <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> recupera sus metadatos.  
  
 La lista de elementos de un tipo de elemento se puede pasar como una matriz de `ITaskItem` objetos. A partir de .NET Framework 3.5, pueden quitarse elementos de una lista de elementos en un destino mediante el uso de la `Remove` atributo. Dado que pueden quitarse los elementos de una lista de elementos, es posible para un tipo de elemento tener cero elementos. Si se pasa una lista de elementos a una tarea, el código de la tarea debe comprobar esta posibilidad.  
  
## <a name="property-and-item-evaluation-order"></a>Propiedad y orden de evaluación del producto  
 Durante la fase de evaluación de una compilación, los archivos importados se incorporan a la compilación en el orden en que aparecen. Propiedades y elementos se definen en tres pasos en el orden siguiente:  
  
-   Propiedades se definen y modifican en el orden en que aparecen.  
  
-   Definiciones de elementos se definen y modifican en el orden en que aparecen.  
  
-   Los elementos se definen y modifican en el orden en que aparecen.  
  
 Durante la fase de ejecución de una compilación, propiedades y elementos que se definen dentro de los destinos se evalúan conjuntamente en una sola fase en el orden en que aparecen.  
  
 Sin embargo, esto no es todo. Cuando se define una propiedad, una definición de elemento o un elemento, se evalúa su valor. El evaluador de expresiones expande la cadena que especifica el valor. La expansión de la cadena depende de la fase de compilación. Este es un orden de evaluación de propiedades y elementos más detallado:  
  
-   Durante la fase de evaluación de una compilación:  
  
    -   Propiedades se definen y modifican en el orden en que aparecen. Funciones de propiedad se ejecutan. Valores de propiedad en los $ (nombreDePropiedad) formulario se expanden dentro de las expresiones. El valor de propiedad se establece en la expresión expandida.  
  
    -   Definiciones de elementos se definen y modifican en el orden en que aparecen. Funciones de propiedad ya se han expandido dentro de las expresiones. Los valores de metadatos se establecen en las expresiones expandidas.  
  
    -   Tipos de elemento se definen y modifican en el orden en que aparecen. Valores del formulario de elemento @(ItemType) se expanden. Las transformaciones de elemento también se expanden. Valores y funciones de propiedad ya se han expandido dentro de las expresiones. Los valores de elemento de lista y los metadatos se establecen en las expresiones expandidas.  
  
-   Durante la fase de ejecución de una compilación:  
  
    -   Propiedades y elementos que se definen dentro de los destinos se evalúan conjuntamente en el orden en que aparecen. Funciones de propiedad se ejecutan y los valores de propiedad se expanden dentro de las expresiones. Valores de elemento y las transformaciones de elemento también se expanden. Los valores de propiedad, los valores de tipo de elemento y los valores de metadatos se establecen en las expresiones expandidas.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Efectos sutiles del orden de evaluación  
 En la fase de evaluación de una compilación, la evaluación de propiedades precede a evaluación de elementos. No obstante, las propiedades pueden tener valores que parezcan depender de valores de elemento. Considere la siguiente secuencia de comandos.  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Ejecutar la tarea Message muestra este mensaje:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Esto es porque el valor de `KeyFileVersion` es realmente la cadena "@(KeyFile->'%(Version)')". elemento y las transformaciones de elemento no se expandieron cuando la propiedad se definió en primer lugar, por lo que la `KeyFileVersion` propiedad se asignó el valor de la cadena sin expandir.  
  
 Durante la fase de ejecución de la compilación, cuando procesa la tarea Message, MSBuild expande la cadena "@(KeyFile->'%(Version)')" para producir "1.0.0.3".  
  
 Observe que aparecería el mismo mensaje incluso si los grupos de propiedades y elementos se han revertido en orden.  
  
 Como segundo ejemplo, tenga en cuenta qué puede ocurrir cuando los grupos de propiedades y elementos se encuentran dentro de los destinos:  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 La tarea Message muestra este mensaje:  
  
```  
KeyFileVersion:   
```  
  
 Esto es porque durante la fase de ejecución de la compilación, grupos de propiedades y elementos definidos dentro de los destinos se evalúan de arriba a abajo al mismo tiempo. Cuando `KeyFileVersion` está definido, `KeyFile` es desconocido. Por lo tanto, la transformación de elemento se expande a una cadena vacía.  
  
 En este caso, invirtiendo el orden de los grupos de propiedades y elementos restaura el mensaje original:  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 El valor de `KeyFileVersion` se establece en "1.0.0.3" y no a "@(KeyFile->'%(Version)')". tarea el mensaje muestra este mensaje:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)