---
title: Comparar propiedades y elementos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: "16"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: f1a0f6df56cebe769ec514abea49ade0083c512e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="comparing-properties-and-items"></a>Comparar propiedades y elementos
Las propiedades y elementos de MSBuild se utilizan para pasar información a las tareas, evaluar condiciones y almacenar valores a los que se puede hacer referencia en el archivo del proyecto.  
  
-   Las propiedades son pares de nombre-valor. Para obtener más información, consulte [Propiedades de MSBuild](../msbuild/msbuild-properties.md).  
  
-   Los elementos son objetos que normalmente representan archivos. Los objetos de elemento pueden tener asociadas colecciones de metadatos. Los metadatos son pares de nombre-valor. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Escalares y vectores  
 Dado que las propiedades de MSBuild son pares de nombre-valor que tienen un solo valor de cadena, a menudo se describen como *escalares*. Puesto que los tipos de elemento de MSBuild son listas de elementos, a menudo se describen como *vector*. Sin embargo, en la práctica, las propiedades pueden representar varios valores y los tipos de elemento pueden tener un elemento o ninguno.  
  
### <a name="target-dependency-injection"></a>Inserción de dependencia de destino  
 Para ver cómo las propiedades pueden representar varios valores, considere la posibilidad de un patrón de uso común para agregar un destino a una lista de destinos que se crea. Esta lista normalmente se representa mediante un valor de propiedad, con los nombres de destino separados por punto y coma.  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 La propiedad `BuildDependsOn` se utiliza normalmente como argumento de un atributo `DependsOnTargets` de destino, que lo convierte de hecho en una lista de elementos. Esta propiedad se puede invalidar para agregar un destino o para cambiar el orden de ejecución de destino. Por ejemplo,  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 agrega el destino CustomBuild a la lista de destino, lo que proporciona a `BuildDependsOn` el valor `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 A partir de MSBuild 4.0, la inserción de dependencia de destino está en desuso. Utilice los atributos `AfterTargets` y `BeforeTargets` en su lugar. Para obtener más información, consulte [Orden de compilación de destinos](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Conversiones entre cadenas y listas de elementos  
 MSBuild realiza conversiones de tipos de elemento y valores de cadena según sea necesario. Para ver cómo una lista de elementos puede convertirse en un valor de cadena, considere lo que sucede cuando un tipo de elemento se utiliza como el valor de una propiedad de MSBuild:  
  
```xml  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 El tipo de elemento OutputDir tiene un atributo `Include` con el valor "KeyFiles\\;Certificates\\". MSBuild analiza esta cadena en dos elementos: KeyFiles\ y Certificates\\. Cuando se utiliza el tipo de elemento OutputDir como el valor de la propiedad OutputDirList, MSBuild convierte o "reduce" el tipo de elemento en la cadena separada por punto y coma "KeyFiles\\;Certificates\\".  
  
## <a name="properties-and-items-in-tasks"></a>Propiedades y elementos en tareas  
 Las propiedades y los elementos se utilizan como entradas y salidas de las tareas de MSBuild. Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).  
  
 Las propiedades se pasan a las tareas como atributos. Dentro de la tarea, una propiedad de MSBuild está representada por un tipo de propiedad cuyo valor se puede convertir a una cadena y desde una cadena. Los tipos de propiedad admitidos incluyen `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string` y cualquier tipo que <xref:System.Convert.ChangeType%2A> pueda controlar.  
  
 Los elementos se pasan a las tareas como objetos <xref:Microsoft.Build.Framework.ITaskItem>. Dentro de la tarea, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> representa el valor del elemento y <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> recupera sus metadatos.  
  
 La lista de elementos de un tipo de elemento se puede pasar como una matriz de objetos `ITaskItem`. Desde la versión .NET Framework 3.5, puede usarse el atributo `Remove` para quitar elementos de una lista en un destino. Dado que pueden quitarse los elementos de una lista de elementos, es posible que un tipo de elemento no tenga ningún elemento. Si se pasa una lista de elementos a una tarea, el código de la tarea debe comprobar esta posibilidad.  
  
## <a name="property-and-item-evaluation-order"></a>Orden de evaluación de propiedades y elementos  
 Durante la fase de evaluación de una compilación, los archivos importados se incorporan a la compilación en el orden en que aparecen. Las propiedades y los elementos se definen en tres pasos en el orden siguiente:  
  
-   Las propiedades se definen y modifican en el orden en que aparecen.  
  
-   Las definiciones de elementos se definen y modifican en el orden en que aparecen.  
  
-   Los elementos se definen y modifican en el orden en que aparecen.  
  
 Durante la fase de ejecución de una compilación, las propiedades y los elementos que se definen dentro de los destinos se evalúan conjuntamente en una sola fase en el orden en que aparecen.  
  
 Sin embargo, esto no es todo. Cuando se define una propiedad, una definición de propiedad o un elemento, se evalúa su valor. El evaluador de expresiones expande la cadena que especifica el valor. La expansión de la cadena depende de la fase de compilación. Este es un orden de evaluación de propiedades y elementos más detallado:  
  
-   Durante la fase de evaluación de una compilación:  
  
    -   Las propiedades se definen y modifican en el orden en que aparecen. Las funciones de propiedad se ejecutan. Los valores de propiedad en la forma $(PropertyName) se expanden dentro de las expresiones. El valor de propiedad se establece en la expresión expandida.  
  
    -   Las definiciones de elementos se definen y modifican en el orden en que aparecen. Las funciones de propiedad ya se han expandido dentro de las expresiones. Los valores de metadatos se establecen en las expresiones expandidas.  
  
    -   Los tipos de elemento se definen y modifican en el orden en que aparecen. Los valores de elemento en la forma @(ItemType) se expanden. Las transformaciones de elemento también se expanden. Las funciones de propiedad ya se han expandido dentro de las expresiones. La lista de elementos y los valores de metadatos se establecen en las expresiones expandidas.  
  
-   Durante la fase de ejecución de una compilación:  
  
    -   Las propiedades y los elementos que se definen dentro de los destinos se evalúan conjuntamente en el orden en que aparecen. Las funciones de propiedad se ejecutan y los valores de propiedad se expanden dentro de las expresiones. Los valores de elemento y las transformaciones de elemento también se expanden. Los valores de propiedad, de tipo de elemento y de metadatos se establecen en las expresiones expandidas.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Efectos sutiles del orden de evaluación  
 En la fase de evaluación de una compilación, la evaluación de propiedades precede a la evaluación de elementos. No obstante, las propiedades pueden tener valores que parezcan depender de valores de elemento. Considere el script siguiente.  
  
```xml  
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
  
 Al ejecutar la tarea Message se muestra este mensaje:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Esto es porque el valor de `KeyFileVersion` es realmente la cadena "@(KeyFile->'%(Version)')". El elemento y las transformaciones de elemento no se expandieron cuando la propiedad se definió por primera vez, por lo que el valor de la cadena sin expandir se asignó a la propiedad `KeyFileVersion`.  
  
 Durante la fase de ejecución de la compilación, cuando procesa la tarea Message, MSBuild expande la cadena "@(KeyFile->'%(Version)')" para producir "1.0.0.3".  
  
 Observe que aparecería el mismo mensaje incluso si el orden de los grupos de propiedades y elementos se ha revertido.  
  
 Como segundo ejemplo, tenga en cuenta qué puede ocurrir cuando los grupos de propiedades y elementos se encuentran dentro de los destinos:  
  
```xml  
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
  
 Esto es porque durante la fase de ejecución de la compilación, los grupos de propiedades y elementos definidos dentro de los destinos se evalúan de arriba abajo al mismo tiempo. Cuando `KeyFileVersion` se define, `KeyFile` es desconocido. Por lo tanto, la transformación de elemento se expande a una cadena vacía.  
  
 En este caso, al invertir el orden de los grupos de propiedades y elementos, se restaura el mensaje original:  
  
```xml  
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
  
 El valor de `KeyFileVersion` se establece en "1.0.0.3" y no en "@(KeyFile->'%(Version)')". La tarea Message muestra este mensaje:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)