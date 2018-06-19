---
title: 'Cómo: Seleccionar los archivos que se van a compilar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 651570ef83f5f87d96ed27538cc4f6ffd569d41f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570683"
---
# <a name="how-to-select-the-files-to-build"></a>Cómo: Seleccionar los archivos que se van a compilar
Cuando se compila un proyecto que contiene varios archivos, se puede enumerar cada archivo en el archivo de proyecto de forma independiente, o bien usar comodines para incluir todos los archivos de un directorio o un conjunto anidado de directorios.  
  
## <a name="specifying-inputs"></a>Especificar entradas  
 Los elementos representan las entradas para una compilación. Para obtener más información sobre los elementos, vea [Elementos](../msbuild/msbuild-items.md).  
  
 Para incluir archivos para una compilación, deben estar incluidos en una lista de elementos del archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Es posible agregar varios archivos a las listas de elementos incluyendo cada archivo individualmente o usando comodines para incluir muchos archivos a la vez.  
  
#### <a name="to-declare-items-individually"></a>Para declarar elementos individualmente  
  
-   Use atributos `Include` similares a los siguientes:  
  
     `<CSFile Include="form1.cs"/>`  
  
     - O  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Si los elementos de una colección de elementos no están en el mismo directorio que el archivo de proyecto, debe especificar la ruta de acceso completa o relativa del elemento. Por ejemplo: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Para declarar varios elementos  
  
-   Use atributos `Include` similares a los siguientes:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     - O  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Especificar las entradas con comodines  
 También se pueden usar comodines para incluir recursivamente todos los archivos o solo archivos concretos de subdirectorios como entradas para una compilación. Para obtener más información sobre los caracteres comodín, vea [Elementos](../msbuild/msbuild-items.md).  
  
 Los ejemplos siguientes están basados en un proyecto que contiene archivos gráficos en los directorios y subdirectorios siguientes, con el archivo de proyecto ubicado en el directorio Project:  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Para incluir todos los archivos .jpg del directorio Images y subdirectorios  
  
-   Use el atributo `Include` siguiente:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Para incluir todos los archivos .jpg que comiencen con "img"  
  
-   Use el atributo `Include` siguiente:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Para incluir todos los archivos de los directorios con nombres que terminen en "jpgs"  
  
-   Use uno de los siguientes atributos `Include`:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     - O  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Pasar elementos a una tarea  
 En un archivo de proyecto, se puede usar la notación @() en las tareas para especificar una lista de elementos completa como entrada de una compilación. Se puede usar esta notación si enumera los archivos de forma separada o si usa comodines.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Para usar todos los archivos de Visual C# o Visual Basic como entradas  
  
-   Use atributos `Include` similares a los siguientes:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     - O  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Se deben usar comodines con los elementos para especificar las entradas de una compilación. No se pueden especificar las entradas mediante el atributo `Sources` en tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] como [Csc](../msbuild/csc-task.md) o [Vbc](../msbuild/vbc-task.md). El ejemplo siguiente no es válido en un archivo de proyecto:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un proyecto que incluye todos los archivos de entrada de forma independiente.  
  
```xml  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se usa un comodín para incluir todos los archivos .cs.  
  
```xml  
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
  
## <a name="see-also"></a>Vea también  
 [Cómo: Excluir archivos de la compilación](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Elementos](../msbuild/msbuild-items.md)