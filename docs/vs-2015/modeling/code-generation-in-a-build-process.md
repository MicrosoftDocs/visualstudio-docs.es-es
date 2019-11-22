---
title: Code Generation in a Build Process | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ae28c59f9c5f19e87b833c90e7dbc6bf3b7497ea
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297935"
---
# <a name="code-generation-in-a-build-process"></a>Generación de código en un proceso de compilación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Text transformation can be invoked as part of the build process of a Visual Studio solution. Hay tareas de compilación que están especializadas para la transformación de texto. Las tareas de compilación T4 ejecutan plantillas de texto en tiempo de diseño y también compilan plantillas de texto en tiempo de ejecución (preprocesadas).

Hay algunas diferencias en cuanto a lo que las tareas de compilación pueden hacer, según el motor de compilación que utilice. When you build the solution in Visual Studio, a text template can access the Visual Studio API (EnvDTE) if the [hostspecific="true"](../modeling/t4-template-directive.md) attribute is set. Pero eso no es cierto cuando se compila la solución desde la línea de comandos o cuando se inicia un servidor compilado mediante Visual Studio. En esos casos, la compilación la realiza MSBuild y se utiliza un host T4 diferente.

Esto significa que no puede tener acceso a elementos como nombres de archivo de proyecto de la misma manera cuando se compila una plantilla de texto en MSBuild. However, you can [pass environment information into text templates and directive processors by using build parameters](#parameters).

## <a name="buildserver"></a> Configure your machines

To enable build tasks on your development computer, install [Modeling SDK for Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148).

If [your build server](https://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) runs on a computer on which Visual Studio is not installed, copy the following files to the build computer from your development machine. Reemplace los números de versión más recientes por ‘*’.

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

  - Microsoft.TextTemplating.Build.Tasks.dll

  - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.*.0.dll

  - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (varios archivos)

  - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

  - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Para editar el archivo de proyecto

Tendrá que editar el archivo de proyecto para configurar algunas de las características de MSBuild.

In solution explorer, choose **Unload** from the context menu of your project. Esto permite editar el archivo .csproj o .vbproj en el editor XML.

When you’ve finished editing, choose **Reload**.

## <a name="import-the-text-transformation-targets"></a>Importar los destinos de transformación de texto

En el archivo .vbproj o .csproj, busque una línea como esta:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- o -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Después de esa línea, inserte la importación de plantillas de texto:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Transformar plantillas en una compilación

Hay algunas propiedades que se pueden insertar en el archivo de proyecto para controlar la tarea de transformación:

- Ejecute la tarea de transformación al principio de cada compilación:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Sobrescriba los archivos que son de solo lectura, por ejemplo porque no se han desprotegido:

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

     De forma predeterminada, la tarea MSBuild de T4 regenera un archivo de salida si es más antiguo que su archivo de plantilla, que cualquier archivo que se ha incluido, que cualquier archivo que ha leído previamente la plantilla o que un procesador de directivas que utiliza. Tenga en cuenta que esto es una prueba de dependencia mucho más eficaz que la utilizada por el comando Transformar todas las plantillas de Visual Studio, que solo compara las fechas de la plantilla y del archivo de salida.

Para realizar solo las transformaciones de texto en el proyecto, invoque la tarea TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Para transformar una plantilla de texto específica:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

Puede utilizar caracteres comodín en TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Control de código fuente

No hay ninguna integración específica con un sistema de control de código fuente. Sin embargo, puede agregar sus propias extensiones, por ejemplo para extraer e insertar en el repositorio un archivo generado. De forma predeterminada, la tarea de transformación de texto evita sobrescribir un archivo marcado como solo lectura; cuando se encuentra un archivo de este tipo, se registra un error en la lista de errores de Visual Studio y se produce un error en la tarea.

Para especificar que los archivos de solo lectura se deben sobrescribir, inserte esta propiedad:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

A menos que personalice el paso de procesamiento posterior, se registrará una advertencia en la lista de errores cuando se sobrescriba un archivo.

## <a name="customizing-the-build-process"></a>Personalizar el proceso de compilación

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

- GeneratedFiles: lista de archivos en los que ha escrito el proceso. En los archivos que sobrescribieron archivos de solo lectura existentes, %(GeneratedFiles.ReadOnlyFileOverwritten) será true. Estos archivos se pueden desproteger del control de código fuente.

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

No se recomienda especificar OutputFileName o OutputFilePath si va a transformar también plantillas dentro de VS mediante Transformar todas las plantillas o si va a ejecutar el generador de un solo archivo. Terminará con diferentes rutas de acceso de archivos en función de cómo desencadenara la transformación. Esto puede ser muy confuso.

## <a name="adding-reference-and-include-paths"></a>Agregar rutas de acceso de referencia y de inclusión

El host tiene un conjunto predeterminado de rutas de acceso donde busca los ensamblados a los que se hace referencia en las plantillas. Para agregar rutas de acceso a este conjunto:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Para establecer las carpetas en las que se buscarán archivos de inclusión, proporcione una lista separada por signos de puntos y coma. Normalmente se agregan a la lista de carpetas existente.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a> Pass build context data into the templates

Puede establecer valores de parámetro en el archivo de proyecto. For example, you can pass build properties and [environment variables](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

En una plantilla de texto, establezca `hostspecific` en la directiva de plantilla. Use the [parameter](../modeling/t4-parameter-directive.md) directive to get values:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

## <a name="msbuild"></a> Using project properties in assembly and include directives

Las macros de Visual Studio, como $ (SolutionDir), no funcionan en MSBuild. En su lugar, puede utilizar las propiedades del proyecto.

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

**Why would I want to transform templates in the build server? I already transformed templates in Visual Studio before I checked in my code.**

Si actualiza un archivo incluido, u otro archivo leído por la plantilla, Visual Studio no transforma el archivo automáticamente. La transformación de plantillas como parte de la compilación se asegura de que todo está actualizado.

**What other options are there for transforming text templates?**

- The [TextTransform utility](../modeling/generating-files-with-the-texttransform-utility.md) can be used in command scripts. En la mayoría de los casos, es más fácil utilizar MSBuild.

- [Invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Design-time text templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md) are transformed by Visual Studio.

- [Run time text templates](../modeling/run-time-text-generation-with-t4-text-templates.md) are transformed at run time in your application.

## <a name="read-more"></a>Leer más

Hay una buena guía en la plantilla de T4 MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets

- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)
- [Visual Studio Visualization and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=185579)
- [Oleg Sych: Understanding T4:MSBuild Integration](https://github.com/olegsych/T4Toolbox)
