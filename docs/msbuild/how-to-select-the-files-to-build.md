---
title: "C&#243;mo: Seleccionar los archivos que se van a compilar | Microsoft Docs"
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
  - "Include (atributo) [MSBuild]"
  - "MSBuild, incluir archivos"
  - "MSBuild, comodines"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Seleccionar los archivos que se van a compilar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se compila un proyecto que contiene varios archivos, se puede enumerar cada archivo en el archivo de proyecto de forma independiente, o bien utilizar comodines para incluir todos los archivos de un directorio o un conjunto anidado de directorios.  
  
## Especificar entradas  
 Los elementos representan las entradas para una compilación.  Para obtener más información sobre elementos, vea [elementos](../msbuild/msbuild-items.md).  
  
 Para incluir archivos para una compilación, deben estar incluidos en una lista de elementos del archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Es posible agregar varios archivos a las listas de elementos incluyendo cada archivo individualmente o usando comodines para incluir muchos archivos a la vez.  
  
#### Para declarar elementos individualmente  
  
-   Utilice atributos `Include` similares a los siguientes:  
  
     `<CSFile Include="form1.cs"/>`  
  
     \-O bien\-  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Si los elementos de una colección de elementos no están en el mismo directorio que el archivo de proyecto, debe especificar la ruta de acceso completa o relativa del elemento.  Por ejemplo: `Include="..\..\form2.cs"`.  
  
#### Para declarar varios elementos  
  
-   Utilice atributos `Include` similares a los siguientes:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     \-O bien\-  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## Especificar las entradas con comodines  
 También se pueden utilizar comodines para incluir recursivamente todos los archivos o sólo archivos concretos de subdirectorios como entradas para una compilación.  Para obtener más información acerca de los caracteres comodín, vea [elementos](../msbuild/msbuild-items.md).  
  
 Los ejemplos siguientes están basados en un proyecto que contiene archivos gráficos en los directorios y subdirectorios siguientes, con el archivo de proyecto ubicado en el directorio Project:  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### Para incluir todos los archivos .jpg del directorio Images y subdirectorios  
  
-   Utilice el atributo `Include` siguiente:  
  
     `Include="Images\**\*.jpg"`  
  
#### Para incluir todos los archivos .jpg que comiencen con "img"  
  
-   Utilice el atributo `Include` siguiente:  
  
     `Include="Images\**\img*.jpg"`  
  
#### Para incluir todos los archivos de los directorios con nombres que terminen en "jpgs"  
  
-   Utilice uno de los atributos `Include` siguientes:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     \-O bien\-  
  
     `Include="Images\**\*jpgs\*"`  
  
## Pasar elementos a una tarea  
 En un archivo de proyecto, se puede utilizar la notación @\(\) en las tareas para especificar una lista de elementos completa como entrada de una compilación.  Se puede utilizar esta notación si enumera los archivos de forma separada o si utiliza comodines.  
  
#### Para utilizar todos los archivos de Visual C\# o Visual Basic como entradas  
  
-   Utilice atributos `Include` similares a los siguientes:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     \-O bien\-  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Se deben utilizar comodines con los elementos para especificar las entradas de una compilación. No se pueden especificar las entradas mediante el atributo `Sources` en tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] como [Csc](../msbuild/csc-task.md) o [Vbc](../msbuild/vbc-task.md).  El ejemplo siguiente no es válido en un archivo de proyecto:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra un proyecto que incluye todos los archivos de entrada de forma independiente.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Ejemplo  
 En el ejemplo de código siguiente se utiliza un comodín para incluir todos los archivos .cs.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Cómo: Excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md)   
 [elementos](../msbuild/msbuild-items.md)