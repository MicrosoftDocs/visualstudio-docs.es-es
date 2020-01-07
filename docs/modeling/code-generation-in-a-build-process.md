---
title: Generación de código en un proceso de compilación
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e01136b845124d74c22ceb1c7cab877a8e2d1d04
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590558"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Invocar la transformación de texto en el proceso de compilación

La [transformación de texto](../modeling/code-generation-and-t4-text-templates.md) se puede invocar como parte del proceso de [compilación](/azure/devops/pipelines/index) de una solución de Visual Studio. Hay tareas de compilación que están especializadas para la transformación de texto. Las tareas de compilación T4 ejecutan plantillas de texto en tiempo de diseño y también compilan plantillas de texto en tiempo de ejecución (preprocesadas).

Hay algunas diferencias en cuanto a lo que las tareas de compilación pueden hacer, según el motor de compilación que utilice. Al compilar la solución en Visual Studio, una plantilla de texto puede tener acceso a la API de Visual Studio (EnvDTE) si se establece el atributo [HostSpecific = "true"](../modeling/t4-template-directive.md) . Pero esto no es cierto cuando se compila la solución desde la línea de comandos o cuando se inicia una compilación de servidor a través de Visual Studio. En esos casos, la compilación la realiza MSBuild y se utiliza un host T4 diferente. Esto significa que no puede tener acceso a elementos como nombres de archivo de proyecto de la misma manera que cuando se crea una plantilla de texto con MSBuild. Sin embargo, puede [pasar información de entorno a plantillas de texto y procesadores de directivas mediante el uso de parámetros de compilación](#parameters).

## <a name="buildserver"></a>Configurar las máquinas

Para habilitar las tareas de compilación en el equipo de desarrollo, instale el SDK de modelado para Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Si [el servidor de compilación](/azure/devops/pipelines/agents/agents) se ejecuta en un equipo que no tiene instalado Visual Studio, copie los siguientes archivos en el equipo de compilación desde el equipo de desarrollo:

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft. VisualStudio. TextTemplating. SDK. host. 15.0. dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft. VisualStudio. TextTemplating. 15.0. dll
  - Microsoft. VisualStudio. TextTemplating. interfaces. 15.0. dll
  - Microsoft. VisualStudio. TextTemplating. VSHost. 15.0. dll

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft. VisualStudio. TextTemplating. Modeling. 15.0. dll

> [!TIP]
> Si obtiene un `MissingMethodException` para un método Microsoft. CodeAnalysis al ejecutar los destinos de compilación de TextTemplating en un servidor de compilación, asegúrese de que los ensamblados Roslyn se encuentren en un directorio denominado *Roslyn* que se encuentre en el mismo directorio que el ejecutable de compilación (por ejemplo, *MSBuild. exe*).

## <a name="edit-the-project-file"></a>Edición del archivo del proyecto

Edite el archivo de proyecto para configurar algunas de las características de MSBuild, por ejemplo, para importar los destinos de transformación de texto.

En **Explorador de soluciones**, elija **Descargar** en el menú contextual del proyecto. Esto permite editar el archivo .csproj o .vbproj en el editor XML. Cuando haya terminado de editar, elija **recargar**.

## <a name="import-the-text-transformation-targets"></a>Importar los destinos de transformación de texto

En el archivo .vbproj o .csproj, busque una línea como esta:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- o -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Después de esa línea, inserte la importación de plantillas de texto:

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Transformación de plantillas en una compilación

Hay algunas propiedades que se pueden insertar en el archivo de proyecto para controlar la tarea de transformación:

- Ejecute la tarea de transformación al principio de cada compilación:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Sobrescriba los archivos que sean de solo lectura, por ejemplo, porque no están desprotegidos:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Transforme todas las plantillas cada vez:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     De forma predeterminada, la tarea de MSBuild T4 regenera un archivo de salida si es anterior a:

     - su archivo de plantilla
     - los archivos que se incluyen
     - los archivos leídos previamente por la plantilla o por un procesador de directivas que utiliza

     Se trata de una prueba de dependencia más eficaz que la que usa el comando **transformar todas las plantillas** en Visual Studio, que solo compara las fechas de la plantilla y el archivo de salida.

Para realizar solo las transformaciones de texto en el proyecto, invoque la tarea TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Para transformar una plantilla de texto específica:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

Puede utilizar caracteres comodín en TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Control de código fuente

No hay ninguna integración específica con un sistema de control de código fuente. Sin embargo, puede agregar sus propias extensiones, por ejemplo, para desproteger y proteger un archivo generado. De forma predeterminada, la tarea de transformación de texto evita sobrescribir un archivo marcado como de solo lectura. Cuando se encuentra un archivo de este tipo, se registra un error en la Lista de errores de Visual Studio y se produce un error en la tarea.

Para especificar que los archivos de solo lectura se deben sobrescribir, inserte esta propiedad:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

A menos que personalice el paso de postprocesamiento, se registrará una advertencia en el Lista de errores cuando se sobrescriba un archivo.

## <a name="customize-the-build-process"></a>Personalizar el proceso de compilación

La transformación de texto se realiza antes que otras tareas del proceso de compilación. Para definir las tareas que se invocan antes y después de la transformación, establezca las propiedades `$(BeforeTransform)` y `$(AfterTransform)`:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

En `AfterTransform`, se puede hacer referencia a listas de archivos:

- GeneratedFiles: lista de archivos en los que ha escrito el proceso. En el caso de los archivos que sobrescribieron los archivos de solo lectura existentes, `%(GeneratedFiles.ReadOnlyFileOverwritten)` será true. Estos archivos se pueden desproteger del control de código fuente.

- NonGeneratedFiles: lista de archivos de solo lectura que no se sobrescribieron.

Por ejemplo, defina una tarea para extraer del repositorio GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath y OutputFileName

Estas propiedades solo las utiliza MSBuild. No afectan a la generación de código en Visual Studio. Redirigen el archivo de salida generado a otra carpeta o archivo. La carpeta de destino debe existir.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Una carpeta útil a la que redirigir es `$(IntermediateOutputPath)`.

Si especifica un nombre de archivo de salida, tiene prioridad sobre la extensión especificada en la Directiva de salida en las plantillas.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

No se recomienda especificar OutputFileName o OutputFilePath si también está transformando plantillas dentro de Visual Studio mediante **transformar todo** o ejecutar el generador de un solo archivo. Terminará con diferentes rutas de acceso de archivo en función de cómo haya desencadenado la transformación. Esto puede resultar confuso.

## <a name="add-reference-and-include-paths"></a>Agregar referencias e incluir rutas de acceso

El host tiene un conjunto predeterminado de rutas de acceso donde busca los ensamblados a los que se hace referencia en las plantillas. Para agregar rutas de acceso a este conjunto:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Para establecer las carpetas en las que se buscarán archivos de inclusión, proporcione una lista separada por signos de puntos y coma. Normalmente se agregan a la lista de carpetas existente.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a>Pasar datos de contexto de compilación a las plantillas

Puede establecer valores de parámetro en el archivo de proyecto. Por ejemplo, puede pasar propiedades de [compilación](../msbuild/msbuild-properties.md) y [variables de entorno](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

En una plantilla de texto, establezca `hostspecific` en la directiva de plantilla. Use la Directiva de [parámetros](../modeling/t4-parameter-directive.md) para obtener valores:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

En un procesador de directivas, puede llamar a [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` obtiene los datos de `T4ParameterValues` solo cuando se usa MSBuild. Al transformar la plantilla con Visual Studio, los parámetros tienen valores predeterminados.

## <a name="msbuild"></a>Usar las propiedades del proyecto en las directivas de inclusión y ensamblado

Las macros de Visual Studio como **$ (SolutionDir)** no funcionan en MSBuild. En su lugar, puede utilizar las propiedades del proyecto.

Edite el archivo *. csproj* o *. vbproj* para definir una propiedad de proyecto. En este ejemplo se define una propiedad denominada **myLibFolder**:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Ahora puede usar la propiedad del proyecto en directivas de ensamblado e inclusión:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

Estas directivas obtienen valores de T4parameterValues tanto en hosts de MSBuild y como en hosts de Visual Studio.

## <a name="q--a"></a>Preguntas y respuestas

**¿Por qué sería conveniente transformar las plantillas en el servidor de compilación? Ya he transformado plantillas en Visual Studio antes de proteger el código.**

Si actualiza un archivo incluido u otro archivo leído por la plantilla, Visual Studio no transforma el archivo automáticamente. La transformación de plantillas como parte de la compilación garantiza que todo está actualizado.

**¿Qué otras opciones hay para transformar las plantillas de texto?**

- La [utilidad textTransform](../modeling/generating-files-with-the-texttransform-utility.md) se puede usar en scripts de comandos. En la mayoría de los casos, es más fácil usar MSBuild.

- [Invocar la transformación de texto en una extensión de Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- Visual Studio transforma [las plantillas de texto en tiempo de diseño](../modeling/design-time-code-generation-by-using-t4-text-templates.md) .

- [Las plantillas de texto en tiempo de ejecución](../modeling/run-time-text-generation-with-t4-text-templates.md) se transforman en tiempo de ejecución en la aplicación.

## <a name="see-also"></a>Vea también

::: moniker range="vs-2017"

- Hay una buena orientación en la plantilla de MSbuild T4 en `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- Hay una buena orientación en la plantilla de MSbuild T4 en `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)
