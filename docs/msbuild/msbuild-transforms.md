---
title: "Transformaciones de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, transformaciones"
  - "transformaciones [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Transformaciones de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una transformación es una conversión unívoca de una lista de elementos en otra.  Además de permitir que un proyecto convierta listas de elementos, una transformación permite que un destino identifique una asignación directa entre sus entradas y salidas.  En este tema se explican las transformaciones y cómo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] las utiliza para compilar los proyectos más eficazmente.  
  
## Modificadores de transformación  
 Las transformaciones no son arbitrarias, pero están limitadas por una sintaxis especial en la que todos los modificadores de transformación deben tener el formato %\(*ItemMetaDataName*\).  Se puede usar cualquier metadato de los elementos como modificador de transformación.  Esto incluye los metadatos conocidos que se asignan a todos los elementos en el momento de su creación.  Para obtener una lista de metadatos de elementos conocidos, vea [Metadatos de los elementos conocidos](../msbuild/msbuild-well-known-item-metadata.md).  
  
 En el ejemplo siguiente, una lista de archivos .resx se transforma en una lista de archivos .resources.  El modificador de transformación % \(nombre de archivo\) especifica que cada archivo .resources tiene el mismo nombre de archivo que el archivo .resx correspondiente.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Se puede especificar un separador personalizado para una lista de elementos transformada de la misma manera en que se haría para una lista de elementos estándar.  Por ejemplo, para separar una lista de elementos transformada mediante una coma \(,\) en lugar del signo de punto y coma predeterminado \(;\), use el código XML siguiente.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Por ejemplo, si los elementos de la lista de elementos @\(RESXFile\) son `Form1.resx`, `Form2.resx` y `Form3.resx`, el resultado en la lista transformada será `Form1.resources`, `Form2.resources` y `Form3.resources`.  
  
## Utilizar varios modificadores  
 Una expresión de transformación puede contener varios modificadores, que se pueden combinar en cualquier orden y se pueden repetir.  En el ejemplo siguiente, se modifica el nombre del directorio que contiene los archivos, pero los archivos conservan el nombre y la extensión originales.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Por ejemplo, si los elementos de la lista de elementos `RESXFile` son `Project1\Form1.resx`, `Project1\Form2.resx` y `Project1\Form3.text`, el resultado en la lista transformada será `Toolset\Form1.resx`, `Toolset\Form2.resx` y `Toolset\Form3.text`.  
  
## Análisis de dependencia  
 Las transformaciones garantizan una asignación unívoca entre la lista de elementos transformada y la lista de elementos original.  Por consiguiente, si un destino crea resultados que son transformaciones de las entradas, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede analizar las marcas de tiempo de las entradas y los resultados, y decidir si se debe omitir, compilar o recompilar parcialmente un destino.  
  
 En la tarea [Copy \(Tarea\)](../msbuild/copy-task.md) del ejemplo siguiente, cada archivo de la lista de elementos `BuiltAssemblies` se asigna a un archivo en la carpeta de destino de la tarea, que se especifica mediante una transformación en el atributo `Outputs`.  Si cambia un archivo de la lista de elementos `BuiltAssemblies`, la tarea `Copy` se ejecutará únicamente para el archivo modificado y se omitirán todos los demás archivos.  Para obtener más información sobre el análisis de dependencias y la forma de usar las transformaciones, vea [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## Ejemplo  
  
### Descripción  
 En el ejemplo siguiente, se muestra un archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que usa transformaciones.  En este ejemplo, se supone que solo hay un archivo .xsd en el directorio c:\\sub0\\sub1\\sub2\\sub3 y que el directorio de trabajo es c:\\sub0.  
  
### Código  
  
```  
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
  
### Comentarios  
 Este ejemplo produce el siguiente resultado.  
  
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
  
## Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md)