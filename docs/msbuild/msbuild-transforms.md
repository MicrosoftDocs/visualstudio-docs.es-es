---
title: Transformaciones de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1a3ff7cbd2025a909ab0c5fb044bb61b24388ff
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151205"
---
# <a name="msbuild-transforms"></a>Transformaciones de MSBuild
Una transformación es una conversión unívoca de una lista de elementos en otra. Además de permitir que un proyecto convierta listas de elementos, una transformación permite que un destino identifique una asignación directa entre sus entradas y salidas. En este tema, se explican las transformaciones y cómo las usa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para compilar proyectos de manera más eficaz.  
  
## <a name="transform-modifiers"></a>Modificadores de transformación  
Las transformaciones no son arbitrarias, sino que están limitadas por una sintaxis especial en la que todos los modificadores de transformación deben tener el formato %(\<ItemMetaDataName). Los metadatos de elementos se pueden usar como modificador de transformación. Esto incluye los metadatos de elementos conocidos que se asignan a todos los elementos cuando se crean. Para obtener una lista de metadatos de elementos conocidos, consulte [Metadatos de los elementos conocidos de MSBuild](../msbuild/msbuild-well-known-item-metadata.md).  
  
En el ejemplo siguiente, una lista de archivos *.resx* se transforma en una lista de archivos *.resources*. El modificador de transformación %(filename) especifica que cada archivo *.resources* tiene el mismo nombre de archivo que el archivo *.resx* correspondiente.  
  
```xml  
@(RESXFile->'%(filename).resources')  
```

Por ejemplo, si los elementos de la lista de elementos @(RESXFile) son *Form1.resx*, *Form2.resx* y *Form3.resx*, las salidas en la lista transformada serán  *Form1.resources*, *Form2.resources* y *Form3.resources*.  

> [!NOTE]
>  Puede especificar un separador personalizado para obtener una lista de elementos transformada de la misma manera que especifica un separador de una lista de elementos estándar. Por ejemplo, para separar una lista de elementos transformada mediante una coma (,) en lugar del punto y coma predeterminado (;), use el siguiente XML:  
> `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`
  
## <a name="use-multiple-modifiers"></a>Uso de varios modificadores  
 Una expresión de transformación puede contener varios modificadores, que se pueden combinar en cualquier orden y se pueden repetir. En el ejemplo siguiente, se cambia el nombre del directorio que contiene los archivos, pero los archivos conservan la extensión de nombre de archivo y el nombre originales.  
  
```xml  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Por ejemplo, si los elementos que están contenidos en la lista de elementos `RESXFile` son *Project1\Form1.resx*, *Project1\Form2.resx* y *Project1\Form3.text*, las salidas en la lista transformada serán *Toolset\Form1.resx*, *Toolset\Form2.resx* y *Toolset\Form3.text*.  
  
## <a name="dependency-analysis"></a>Análisis de dependencias  
 Las transformaciones garantizan una asignación unívoca entre la lista de elementos transformada y la lista de elementos original. Por tanto, si un destino crea salidas que son transformaciones de las entradas, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede analizar las marcas de tiempo de las entradas y salidas, y decidir si quiere omitir, compilar o recompilar parcialmente un destino.  
  
 En la [tarea de copia](../msbuild/copy-task.md) del ejemplo siguiente, todos los archivos de la lista de elementos `BuiltAssemblies` se asignan a un archivo en la carpeta de destino de la tarea, que se especifica mediante una transformación en el atributo `Outputs`. Si cambia un archivo en la lista de elementos `BuiltAssemblies`, la tarea `Copy` se ejecutará solo para el archivo modificado y se omitirán todos los demás archivos. Para más información sobre los análisis de dependencias y cómo usar las transformaciones, consulte [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md).  
  
```xml  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente, se muestra un archivo del proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que usa transformaciones. En este ejemplo, se da por hecho que hay solo un archivo *.xsd* en el directorio *c:\sub0\sub1\sub2\sub3* y que el directorio de trabajo es *c:\sub0*.  
  
### <a name="code"></a>Código  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Comentarios  
 Este ejemplo produce el siguiente resultado:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md)