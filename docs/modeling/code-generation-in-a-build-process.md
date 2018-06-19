---
title: Generación de código en un proceso de compilación en Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1d08aafd31d93c7a07d57dcd5b831b8ae41a6c17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953260"
---
# <a name="code-generation-in-a-build-process"></a>Generación de código en un proceso de compilación

[Transformación de texto](../modeling/code-generation-and-t4-text-templates.md) se pueden invocar como parte de la [proceso de compilación](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) de un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución. Hay tareas de compilación que están especializadas para la transformación de texto. Las tareas de compilación T4 ejecutan plantillas de texto en tiempo de diseño y también compilan plantillas de texto en tiempo de ejecución (preprocesadas).

Hay algunas diferencias en cuanto a lo que las tareas de compilación pueden hacer, según el motor de compilación que utilice. Cuando se compila la solución en Visual Studio, una plantilla de texto puede tener acceso a la API de Visual Studio (EnvDTE) si el [hostspecific = "true"](../modeling/t4-template-directive.md) atributo está establecido. Pero eso no es cierto cuando se compila la solución desde la línea de comandos o cuando se inicia una compilación de servidor a través de Visual Studio. En esos casos, la compilación la realiza MSBuild y se utiliza un host T4 diferente.

Esto significa que no tiene acceso cosas como nombres de archivo de proyecto de la misma manera cuando se compila una plantilla de texto en MSBuild. Sin embargo, puede utilizar [pasar información del entorno a plantillas de texto y procesadores de directivas mediante el uso de parámetros de compilación](#parameters).

##  <a name="buildserver"></a> Configurar los equipos

Para habilitar las tareas de compilación en el equipo de desarrollo, instale el SDK de modelado para Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Si [el servidor de compilación](http://msdn.microsoft.com/Library/788443c3-0547-452e-959c-4805573813a9) se ejecuta en un equipo en el que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no es está instalado, copie los siguientes archivos en el equipo de compilación desde el equipo de desarrollo. Sustituya los números de versión más reciente de ' *'.

-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    -   Microsoft.TextTemplating.Build.Tasks.dll

    -   Microsoft.TextTemplating.targets

-   $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    -   Microsoft.VisualStudio.TextTemplating.*.0.dll

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (varios archivos)

    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

-   $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Para editar el archivo de proyecto

Tendrá que editar el archivo de proyecto para configurar algunas de las características de MSBuild.

En el Explorador de soluciones, elija **Unload** en el menú contextual del proyecto. Esto permite editar el archivo .csproj o .vbproj en el editor XML.

Cuando haya terminado de editar, elija **volver a cargar**.

## <a name="import-the-text-transformation-targets"></a>Importar los destinos de transformación de texto

En el archivo .vbproj o .csproj, busque una línea como esta:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- o -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Después de esa línea, inserte la importación de plantillas de texto:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version - defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>Transformar plantillas en una compilación

Hay algunas propiedades que se pueden insertar en el archivo de proyecto para controlar la tarea de transformación:

-   Ejecute la tarea de transformación al principio de cada compilación:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

-   Sobrescriba los archivos que son de solo lectura, por ejemplo porque no se han desprotegido:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

-   Transforme todas las plantillas cada vez:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     De forma predeterminada, la tarea MSBuild de T4 regenera un archivo de salida si es más antiguo que su archivo de plantilla, que cualquier archivo que se ha incluido, que cualquier archivo que ha leído previamente la plantilla o que un procesador de directivas que utiliza. Tenga en cuenta que esto es una prueba de dependencia mucho más eficaz que la utilizada por el comando Transformar todas las plantillas de Visual Studio, que solo compara las fechas de la plantilla y del archivo de salida.

 Para realizar solo las transformaciones de texto en el proyecto, invoque la tarea TransformAll:

 `msbuild myProject.csproj /t:TransformAll`

 Para transformar una plantilla de texto específica:

 `msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

 Puede utilizar caracteres comodín en TransformFile:

 `msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Control de código fuente

No hay ninguna integración específica con un sistema de control de código fuente. Sin embargo, puede agregar sus propias extensiones, por ejemplo para desproteger y proteger un archivo generado. De forma predeterminada, la tarea de transformación de texto evita sobrescribir un archivo marcado como solo lectura; cuando se encuentra un archivo de este tipo, se registra un error en la lista de errores de Visual Studio y se produce un error en la tarea.

 Para especificar que los archivos de solo lectura se deben sobrescribir, inserte esta propiedad:

 `<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOuputFiles>`

 A menos que personalice el paso de procesamiento posterior, se registrará una advertencia en la lista de errores cuando se sobrescriba un archivo.

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

-   GeneratedFiles: lista de archivos en los que ha escrito el proceso. En los archivos que sobrescribieron archivos de solo lectura existentes, %(GeneratedFiles.ReadOnlyFileOverwritten) será true. Estos archivos se pueden desproteger del control de código fuente.

-   NonGeneratedFiles: lista de archivos de solo lectura que no se sobrescribieron.

Por ejemplo, defina una tarea para desproteger GeneratedFiles.

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

 Una carpeta útil como destino de la redirección es `$(IntermediateOutputPath).`

 Si especifica y genera el nombre de archivo, tendrá prioridad sobre la extensión especificada en la directiva de salida en las plantillas.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

 Especificar un OutputFileName o OutputFilePath no se recomienda si va a transformar también plantillas dentro de VS mediante Transformar todas las o ejecutar el generador de archivo único. Terminará con diferentes rutas de acceso de archivos en función de cómo desencadenara la transformación. Esto puede ser muy confuso.

## <a name="add-reference-and-include-paths"></a>Agregar referencia e incluir las rutas de acceso

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

##  <a name="parameters"></a> Pasar datos del contexto de compilación en las plantillas

Puede establecer valores de parámetro en el archivo de proyecto. Por ejemplo, puede pasar [generar](../msbuild/msbuild-properties.md) propiedades y [variables de entorno](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

 En una plantilla de texto, establezca `hostspecific` en la directiva de plantilla. Use la [parámetro](../modeling/t4-parameter-directive.md) directiva obtener valores:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

En un procesador de directivas, se puede llamar a [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` obtiene datos de `T4ParameterValues` solo cuando se usa MSBuild. Cuando se transforma la plantilla mediante Visual Studio, los parámetros tienen sus valores predeterminados.

##  <a name="msbuild"></a> Usar propiedades del proyecto de ensamblado y las directivas de inclusión

Macros de Visual Studio como $ (SolutionDir) no funcionan en MSBuild. En su lugar, puede utilizar las propiedades del proyecto.

Modifique el archivo .csproj o .vbproj para definir una propiedad de proyecto. En este ejemplo se define una propiedad denominada `myLibFolder`:

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

 **¿Por qué desearía transformar plantillas en el servidor de compilación? Ya he transformado plantillas en Visual Studio antes de proteger el código.**

 Si actualiza un archivo incluido, u otro archivo leído por la plantilla, Visual Studio no transforma el archivo automáticamente. Transformación de plantillas como parte de la compilación se asegura de que todo está actualizado.

 **¿Qué otras opciones existen para transformar plantillas de texto?**

-   El [utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) pueden usarse en las secuencias de comandos. En la mayoría de los casos, es más fácil usar MSBuild.

-   [Invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

-   [Plantillas de texto en tiempo de diseño](../modeling/design-time-code-generation-by-using-t4-text-templates.md) se transforman mediante Visual Studio.

-   [Plantillas de texto de tiempo de ejecución](../modeling/run-time-text-generation-with-t4-text-templates.md) se transforman en tiempo de ejecución de la aplicación.

## <a name="see-also"></a>Vea también

- Hay una buena guía en la plantilla de T4 MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets
- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)
- [Oleg Sych: Descripción de T4: integración](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)
- [!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]