---
title: Procedimiento Excluir archivos de la compilación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2df391440e8fe175b86a37cd02d0aec8fee372e6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603175"
---
# <a name="how-to-exclude-files-from-the-build"></a>Procedimiento Excluir archivos de la compilación
En un archivo de proyecto puede utilizar comodines para incluir todos los archivos de un directorio o un conjunto de directorios anidado como entradas para una compilación. Sin embargo, puede haber un archivo en el directorio o un directorio en el conjunto anidado de directorios que no quiera incluir como entrada para una compilación. Puede excluir explícitamente ese archivo o directorio de la lista de entradas. También puede haber un archivo en un proyecto que solo quiera incluir bajo determinadas condiciones. Se pueden declarar explícitamente las condiciones para incluir un archivo en una compilación.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Excluir un archivo o directorio de las entradas de una compilación
 Las listas de elementos son los archivos de entrada para una compilación. Los elementos que se van a incluir se declaran por separado o como un grupo mediante el atributo `Include`. Por ejemplo:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Si se han utilizado comodines para incluir todos los archivos de un directorio o un conjunto de directorios anidado como entradas para una compilación, puede haber uno o más archivos en el directorio o un directorio en el conjunto de directorios anidado que no quiera incluir. Para excluir un elemento de la lista de elementos, utilice el atributo `Exclude`.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Para incluir todos los archivos *.cs* o *.vb* excepto *Form2*

-   Utilice uno de los siguientes atributos `Include` y `Exclude`:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    o

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Para incluir todos los archivos *.cs* o *.vb* excepto *Form2* y *Form3*

-   Utilice uno de los siguientes atributos `Include` y `Exclude`:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    o

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Para incluir todos los archivos *.jpg* de los subdirectorios del directorio *Images*, excepto los del directorio *Version2*

-   Utilice los siguientes atributos `Include` y `Exclude`:

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    >  Debe especificar la ruta de acceso de ambos atributos. Si utiliza una ruta de acceso absoluta para especificar ubicaciones de archivos en el atributo `Include`, también debe utilizar una ruta de acceso absoluta en el atributo `Exclude`; si utiliza una ruta de acceso relativa en el atributo `Include`, también debe utilizar una ruta de acceso relativa en el atributo `Exclude`.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Usar condiciones para excluir un archivo o un directorio de las entradas de una compilación
 Si hay elementos que quiere incluir, por ejemplo, en una compilación de depuración, pero no en una compilación de versión, puede utilizar el atributo `Condition` para especificar las condiciones en las que se va a incluir el elemento.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Para incluir el archivo *Formula.vb* solo en compilaciones de versión

-   Utilice un atributo `Condition` similar al siguiente:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se compila un proyecto con todos los archivos *.cs* del directorio, excepto *Form2.cs*.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs Exclude="Form2.cs"/>

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
- [Elementos](../msbuild/msbuild-items.md)
- [MSBuild](../msbuild/msbuild.md)
- [Cómo: Seleccionar los archivos que se van a compilar](../msbuild/how-to-select-the-files-to-build.md)
