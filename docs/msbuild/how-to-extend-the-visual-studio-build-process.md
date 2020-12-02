---
title: Ampliación del proceso de compilación
description: Obtenga información sobre las distintas formas de modificar el proceso de compilación a fin de que pueda controlar y personalizar el modo en que se compilan los proyectos.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07f0312892d9f4f4073cf6fb2c9537ffa52a6267
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970075"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procedimiento para ampliar el proceso de compilación de Visual Studio

El proceso de compilación de Visual Studio se define mediante una serie de archivos *.targets* de MSBuild que se importan en el archivo de proyecto. Uno de estos archivos importados, *Microsoft.Common.targets*, se puede extender para que pueda ejecutar tareas personalizadas en varios puntos del proceso de compilación. En este artículo se explican dos métodos que puede usar para extender el proceso de compilación de Visual Studio:

- Reemplazar destinos predefinidos específicos definidos en los destinos comunes (*Microsoft.Common.targets* o los archivos que importa).

- Reemplazar las propiedades "DependsOn" definidas en los destinos comunes.

## <a name="override-predefined-targets"></a>Reemplazar destinos predefinidos

Los destinos comunes contienen un conjunto de destinos vacíos predefinidos al que se llama antes y después de algunos de los destinos principales del proceso de compilación. Por ejemplo, MSBuild llama al destino `BeforeBuild` antes del destino `CoreBuild` principal y al destino `AfterBuild` después del destino `CoreBuild`. De forma predeterminada, los destinos vacíos de los destinos comunes no hacen nada, pero puede reemplazar su comportamiento predeterminado si define los destinos que quiere en un archivo de proyecto que importa los destinos comunes. Al reemplazar los destinos predefinidos, puede usar tareas de MSBuild para tener más control sobre el proceso de compilación.

> [!NOTE]
> Los proyectos de estilo de SDK tienen una importación implícita de destinos *después de la última línea del archivo del proyecto*. Esto significa que no se pueden reemplazar los destinos predeterminados a menos que se especifiquen las importaciones manualmente, tal como se describe en [Cómo: usar SDK de proyecto de MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Para reemplazar un destino predefinido

1. Identifique un destino predefinido de los destinos comunes que quiera reemplazar. Consulte la tabla siguiente para ver la lista completa de destinos que puede reemplazar de forma segura.

2. Defina el destino o los destinos al final del archivo del proyecto, inmediatamente antes de la etiqueta `</Project>`. Por ejemplo:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Compile el archivo del proyecto.

En la tabla siguiente se muestran todos los destinos incluidos en los destinos comunes que puede reemplazar de forma segura.

|Nombre de destino|Descripción|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de que se realice la compilación básica. La mayoría de las personalizaciones se realiza en uno de estos dos destinos.|
|`BeforeBuild`, `AfterBuild`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de todo lo demás de la compilación. **Nota:** Los destinos `BeforeBuild` y `AfterBuild` ya están definidos en los comentarios al final de la mayoría de los archivos de proyecto, lo que permite agregar con facilidad eventos anteriores y posteriores a la compilación al archivo de proyecto.|
|`BeforeRebuild`, `AfterRebuild`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la invocación a la funcionalidad de recompilación básica. El orden de ejecución de destino en *Microsoft.Common.targets* es: `BeforeRebuild`, `Clean`, `Build` y luego `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la invocación a la funcionalidad de limpieza básica.|
|`BeforePublish`, `AfterPublish`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la invocación a la funcionalidad de publicación de limpieza básica.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de la resolución de las referencias de ensamblados.|
|`BeforeResGen`, `AfterResGen`|Las tareas insertadas en uno de estos destinos se ejecutan antes o después de generar los recursos.|

## <a name="example-aftertargets-and-beforetargets"></a>Ejemplo: BeforeTargets y AfterTargets

En el ejemplo siguiente se muestra cómo usar el atributo `AfterTargets` para agregar un destino personalizado que realice una acción en los archivos de salida. En este caso, copia los archivos de salida en una nueva carpeta *CustomOutput*.  En el ejemplo también se muestra cómo limpiar los archivos creados por la operación de compilación personalizada con un destino `CustomClean` mediante un atributo `BeforeTargets` y especificando que la operación de limpieza personalizada se ejecuta antes que el destino de `CoreClean`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Asegúrese de usar nombres distintos de los destinos predefinidos que se enumeran en la tabla de la sección anterior (por ejemplo, aquí el destino de la compilación personalizada se denomina `CustomAfterBuild`, no `AfterBuild`), ya que la importación del SDK reemplaza los destinos predefinidos y también los define. No verá la importación del archivo de destino que invalida esos destinos, pero se agrega implícitamente al final del archivo de proyecto cuando usa el método del atributo `Sdk` para hacer referencia a un SDK.

## <a name="override-dependson-properties"></a>Reemplazar propiedades DependsOn

Reemplazar destinos predefinidos es una manera sencilla de extender el proceso de compilación, pero, dado que MSBuild evalúa la definición de destinos secuencialmente, no hay manera de evitar que otro proyecto que importe su proyecto reemplace los destinos que ya ha reemplazado. Por lo tanto, por ejemplo, el último destino `AfterBuild` definido en el archivo del proyecto, después de que se hayan importado todos los demás proyectos, será el que se utiliza durante la compilación.

Para protegerse de reemplazos de destinos imprevistos, puede reemplazar las propiedades DependsOn que se usan en los atributos `DependsOnTargets` en los destinos comunes. Por ejemplo, el valor del atributo `DependsOnTargets` del destino `Build` es `"$(BuildDependsOn)"`. Tenga en cuenta lo siguiente:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Este fragmento de XML indica que, antes de que el destino `Build` se pueda ejecutar, primero se deben ejecutar todos los destinos especificados en la propiedad `BuildDependsOn`. La propiedad `BuildDependsOn` se define como:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Para reemplazar este valor de propiedad, puede declarar otra propiedad denominada `BuildDependsOn` al final del archivo del proyecto. Al incluir la propiedad `BuildDependsOn` anterior en la propiedad nueva, puede agregar nuevos destinos al principio y al final de la lista de destinos. Por ejemplo:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Los proyectos que importan los archivos del proyecto pueden reemplazar estas propiedades sin sobrescribir las personalizaciones que haya realizado.

#### <a name="to-override-a-dependson-property"></a>Para reemplazar una propiedad DependsOn

1. Identifique una propiedad DependsOn predefinida en los destinos comunes que quiera reemplazar. Vea la tabla siguiente para obtener una lista de las propiedades DependsOn que normalmente se reemplazan.

2. Defina otra instancia de la propiedad o de las propiedades al final del archivo del proyecto. Incluya la propiedad original, por ejemplo `$(BuildDependsOn)`, en la propiedad nueva.

3. Defina sus destinos personalizados antes o después de la definición de la propiedad.

4. Compile el archivo del proyecto.

### <a name="commonly-overridden-dependson-properties"></a>Propiedades DependsOn que normalmente se reemplazan

|Nombre de propiedad|Descripción|
|-------------------|-----------------|
|`BuildDependsOn`|La propiedad que se debe reemplazar si quiere insertar destinos personalizados antes o después del proceso de compilación completo.|
|`CleanDependsOn`|La propiedad que se debe reemplazar si quiere limpiar el resultado del proceso de compilación personalizado.|
|`CompileDependsOn`|La propiedad que se debe reemplazar si quiere insertar procesos personalizados antes o después del paso de compilación.|

## <a name="example-builddependson-and-cleandependson"></a>Ejemplo: BuildDependsOn y CleanDependsOn

El ejemplo siguiente es parecido al ejemplo de `BeforeTargets` y `AfterTargets`, y muestra cómo lograr una funcionalidad similar. Amplía la compilación mediante `BuildDependsOn` para que pueda agregar su propia tarea `CustomAfterBuild`, la cual copia los archivos de salida después de la compilación y agrega la tarea `CustomClean` correspondiente usando `CleanDependsOn`.  

En este ejemplo, se trata de un proyecto tipo SDK. Como se ha mencionado anteriormente en este artículo en la nota sobre los proyectos tipo SDK, debe usar el método de importación manual en lugar del atributo `Sdk` que usa Visual Studio al generar archivos de proyecto.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

El orden de los elementos es importante. Los elementos `BuildDependsOn` y `CleanDependsOn` deben aparecer después de importar el archivo de destinos SDK estándar.

## <a name="see-also"></a>Consulte también

- [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [Archivos .targets](../msbuild/msbuild-dot-targets-files.md)
