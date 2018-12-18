---
title: Definiciones de elementos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c267c8a0d76fdda08112e428c0fc7403daa1f30
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178567"
---
# <a name="item-definitions"></a>Definiciones de elementos
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 permite la declaración estática de los elementos de archivos de proyecto mediante el elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Sin embargo, sólo se pueden agregar metadatos en el nivel de elemento, aunque los metadatos sean idénticos para todos los elementos. A partir de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, un elemento de proyecto denominado [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) resuelve esta limitación. *ItemDefinitionGroup* permite definir un conjunto de definiciones de elementos, las cuales agregan valores de metadatos predeterminados a todos los elementos del tipo de elemento especificado.  
  
 El elemento *ItemDefinitionGroup* aparece inmediatamente después del elemento [Project](../msbuild/project-element-msbuild.md) del archivo de proyecto. Las definiciones de elementos proporcionan la funcionalidad siguiente:  
  
-   Puede definir metadatos predeterminados globales para los elementos fuera de un destino. Es decir, los mismos metadatos se aplican a todos los elementos del tipo especificado.  
  
-   Los tipos de elementos pueden tener varias definiciones. Cuando se agregan otras especificaciones de metadatos al tipo, la última especificación tiene la prioridad. \(Los metadatos siguen el mismo orden de importación que las propiedades.\)  
  
-   Los metadatos pueden ser aditivos. Por ejemplo, los valores de CDefines se acumulan condicionalmente, dependiendo de las propiedades que se establezcan. Por ejemplo: `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Se puede quitar los metadatos.  
  
-   Se puede utilizar condiciones para controlar la inclusión de metadatos.  
  
## <a name="item-metadata-default-values"></a>Valores predeterminados de los metadatos de elementos  
 Los metadatos de elemento definidos en ItemDefinitionGroup son simplemente una declaración de los metadatos predeterminados. Los metadatos no se aplican a menos que defina un elemento que utilice un ItemGroup para contener los valores de los metadatos.  
  
> [!NOTE]
>  En muchos de los ejemplos de este tema, se muestra un elemento de ItemDefinitionGroup pero se omite su definición de ItemGroup correspondiente para mayor claridad.  
  
 Los metadatos definidos explícitamente en un ItemGroup tienen prioridad sobre los metadatos de ItemDefinitionGroup. Los metadatos de ItemDefinitionGroup sólo se aplican para los metadatos no definidos en ItemGroup. Por ejemplo:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 En este ejemplo, los metadatos predeterminados "m" se aplican al elemento "i" porque los metadatos "m" no están definidos explícitamente por el elemento "i". Sin embargo, los metadatos predeterminados "n" no se aplican al elemento "i" porque los metadatos "n" ya están definidos por el elemento "i".  
  
> [!NOTE]
>  Los nombres de los elementos y parámetros XML distinguen entre mayúsculas y minúsculas. Los nombres de los metadatos de elemento y los nombres de elementos\/propiedades no distinguen entre mayúsculas y minúsculas. Por consiguiente, los elementos de ItemDefinitionGroup que tienen nombres que sólo difieren en las mayúsculas y minúsculas se deberán tratar como el mismo ItemGroup.  
  
## <a name="value-sources"></a>Orígenes de los valores  
 Los valores de los metadatos definidos en ItemDefinitionGroup pueden proceder de muchos orígenes diferentes, como se indica a continuación:  
  
-   Propiedad PropertyGroup  
  
-   Elemento de un ItemDefinitionGroup  
  
-   Transformación de un elemento de ItemDefinitionGroup  
  
-   Variable de entorno  
  
-   Propiedad global (de la línea de comandos de *MSBuild.exe*)  
  
-   Propiedad reservada  
  
-   Metadatos conocidos en un elemento de un ItemDefinitionGroup  
  
-   Sección CDATA\<\!\[CDATA\[no se analiza nada de lo que se escriba aquí\]\]\>  
  
> [!NOTE]
>  Los metadatos de elemento de un ItemGroup no son útiles en una declaración de metadatos de ItemDefinitionGroup porque los elementos de ItemDefinitionGroup se procesan antes que los elementos de ItemGroup.  
  
## <a name="additive-and-multiple-definitions"></a>Definiciones aditivas y múltiples  
 Al agregar definiciones o utilizar varios ItemDefinitionGroups, recuerde lo siguiente:  
  
-   La especificación de los metadatos adicionales se agrega al tipo.  
  
-   La última especificación tiene prioridad.  
  
Cuando hay varios ItemDefinitionGroups, cada especificación posterior agrega sus metadatos a la definición anterior. Por ejemplo:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
En este ejemplo, los metadatos "o" se agregan a "m" y "n".  
  
Además, se puede agregar también los valores de los metadatos previamente definidos. Por ejemplo:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
En este ejemplo, el valor previamente definido para los metadatos "m" \(m1\) se agrega al nuevo valor \(m2\), de modo que el valor final es "m1;m2".  
  
> [!NOTE]
>  Esto también puede ocurrir en el mismo ItemDefinitionGroup.  
  
Cuando se invalidan los metadatos previamente definidos, la última especificación toma la prioridad. En el ejemplo siguiente, el valor final de los metadatos "m" va de "m1" a "m1a".  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Uso de condiciones en ItemDefinitionGroup  
 Puede utilizar condiciones en un ItemDefinitionGroup para controlar la inclusión de metadatos. Por ejemplo:  
  
```xml  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
En este caso, los metadatos predeterminados "m1" en el elemento "i" sólo se incluyen si el valor de la propiedad "Configuration" es "Debug".  
  
> [!NOTE]
>  Las condiciones sólo admiten las referencias a los metadatos locales.  
  
Las referencias a los metadatos definidos en un ItemDefinitionGroup anterior son locales del elemento, no del grupo de definiciones. Es decir, el ámbito de las referencias es específico del elemento. Por ejemplo:  
  
```xml  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i> 
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
  
```  
  
En el ejemplo anterior, el elemento "i" hace referencia al elemento "test" de Condition. Esta condición nunca será true porque MSBuild interpreta una referencia a metadatos de otro elemento en ItemDefinitionGroup como una cadena vacía. Por lo tanto, "m" se establecerá en "m0".
 
```xml 
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

En el ejemplo anterior, "m" se establecería en el valor "m1", ya que Condition hace referencia al valor de metadatos de "i" para el elemento "yes". 
  
## <a name="override-and-delete-metadata"></a>Invalidación y eliminación de metadatos  
 Los metadatos definidos en un elemento ItemDefinitionGroup se pueden invalidar en un elemento ItemDefinitionGroup posterior estableciendo los valores de los metadatos en blanco. También puede eliminar eficazmente un elemento de metadatos estableciéndolo en un valor vacío. Por ejemplo:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
El elemento "i" aún los metadatos "m" pero, ahora, su valor es vacío.  
  
## <a name="scope-of-metadata"></a>Ámbito de metadatos  
 ItemDefinitionGroup tiene un ámbito global en las propiedades definidas y globales, independientemente de donde se definan. Las definiciones de los metadatos predeterminadas en un ItemDefinitionGroup pueden ser de autorreferencia. Por ejemplo, a continuación se utiliza una referencia de metadatos simple:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
También se puede utilizar una referencia de metadatos calificada:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Sin embargo, el siguiente ejemplo no es válido:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
A partir de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, ItemGroups también puede ser de autorreferencia. Por ejemplo:  
  
```xml  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vea también  
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)
