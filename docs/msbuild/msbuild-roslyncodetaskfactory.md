---
title: Tareas insertadas de MSBuild con RoslynCodeTaskFactory | Microsoft Docs
description: Obtenga información sobre RoslynCodeTaskFactory de MSBuild, que usa los compiladores de Roslyn multiplataforma para generar ensamblados de la tarea en memoria para su uso como tareas insertadas.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c033c4d0ee36b9cb01618dd3ac3183e8782c70d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878427"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Tareas insertadas de MSBuild con RoslynCodeTaskFactory

De forma similar a [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory usa los compiladores de Roslyn multiplataforma para generar ensamblados de la tarea en memoria para su uso como tareas insertadas.  Las tareas RolynCodeTaskFactory establecen como destino .NET Standard y pueden funcionar en los runtimes de .NET Framework y .NET Core, así como con otras plataformas como Linux y Mac OS.

>[!NOTE]
>La tarea RoslynCodeTaskFactory solo está disponible en MSBuild 15.8 y versiones posteriores. Las versiones de MSBuild siguen a las versiones de Visual Studio, por lo que RoslynCodeTaskFactory está disponible en Visual Studio 2017, versión 15.8 y posteriores.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>La estructura de una tarea insertada con RoslynCodeTaskFactory

 Las tareas insertadas con RoslynCodeTaskFactory se declaran de forma idéntica a [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), con la única diferencia de que el destino es .NET Standard.  La tarea insertada y el elemento `UsingTask` que la contiene se suelen incluir en un archivo *.targets* y se importan en otros archivos de proyecto según se requiera. A continuación se muestra una tarea insertada básica. Observe que no se realiza ninguna acción.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 El elemento `UsingTask` del ejemplo tiene tres atributos que describen la tarea y el generador de tareas insertadas que lo compila.

- El atributo `TaskName` asigna un nombre a la tarea, en este caso, `DoNothing`.

- El atributo `TaskFactory` asigna un nombre a la clase que implementa el generador de tareas insertadas.

- El atributo `AssemblyFile` proporciona la ubicación del generador de tareas insertadas. Alternativamente, puede utilizar el atributo `AssemblyName` para especificar el nombre completo de la clase de generador de tareas insertadas, que está ubicada normalmente en la caché global de ensamblados (GAC).

Los elementos restantes de la tarea `DoNothing` están vacíos y se proporcionan para mostrar el orden y la estructura de una tarea insertada. Un ejemplo más completo se presenta posteriormente en este tema.

- El elemento `ParameterGroup` es opcional. Cuando se especifica, declara los parámetros para la tarea. Para obtener más información sobre los parámetros de entrada y salida, vea [Parámetros de entrada y salida](#input-and-output-parameters) más adelante en este tema.

- El elemento `Task` describe y contiene el código fuente de la tarea.

- El elemento `Reference` especifica las referencias a los ensamblados de .NET que se utilizan en el código. Esto es equivalente a agregar una referencia a un proyecto en Visual Studio. El atributo `Include` especifica la ruta de acceso del ensamblado al que se hace referencia.

- El elemento `Using` enumera los espacios de nombres a los que se desea obtener acceso. Esto es similar a la instrucción `Using` de Visual C#. El atributo `Namespace` especifica el espacio de nombres que se va a incluir.

Los elementos `Reference` y `Using` son independientes del lenguaje. Las tareas insertadas se pueden escribir en cualquiera de los lenguajes CodeDom para .NET admitidos, por ejemplo, Visual Basic o Visual C#.

> [!NOTE]
> Los elementos contenidos en el elemento `Task` son específicos del generador de tareas, en este caso, el generador de tareas de código.

### <a name="code-element"></a>Elemento de código

El último elemento secundario que aparece dentro del elemento `Task` es el elemento `Code`. El elemento `Code` contiene o localiza el código que se desea compilar en una tarea. Lo que se incluye en el elemento `Code` depende de cómo se desea escribir la tarea.

El atributo `Language` especifica el lenguaje en el que se escribe el código. Los valores aceptables son `cs` para C#, `vb` para Visual Basic.

El atributo `Type` especifica el tipo de código que se encuentra en el elemento `Code`.

- Si el valor de `Type` es `Class`, el elemento `Code` contiene el código para una clase que deriva de la interfaz <xref:Microsoft.Build.Framework.ITask>.

- Si el valor de `Type` es `Method`, el código define un reemplazo del método `Execute` de la interfaz <xref:Microsoft.Build.Framework.ITask>.

- Si el valor de `Type` es `Fragment`, el código define el contenido del método `Execute`, pero no la firma o la instrucción `return`.

El propio código aparece normalmente entre un marcador `<![CDATA[` y un marcador `]]>`. Dado que el código está en una sección CDATA, no tiene que preocuparse de anteponer caracteres de escape a los caracteres reservados, como "\<" or ">".

Alternativamente, puede utilizar el atributo `Source` del elemento `Code` para especificar la ubicación de un archivo que contiene el código para la tarea. El código del archivo de código fuente debe ser del tipo especificado por el atributo `Type`. Si el atributo `Source` está presente, el valor predeterminado de `Type` es `Class`. Si `Source` no está presente, el valor predeterminado es `Fragment`.

> [!NOTE]
> Al definir la clase de tarea en el archivo de origen, el nombre de clase debe corresponder al atributo `TaskName` del elemento [UsingTask](../msbuild/usingtask-element-msbuild.md) correspondiente.

## <a name="hello-world"></a>Hello World

 Esta es una tarea insertada más sólida con RoslynCodeTaskFactory. La tarea HelloWorld muestra "Hello, world!" en el dispositivo de registro de errores predeterminado, que suele ser la consola del sistema o la ventana de **salida** de Visual Studio. El elemento `Reference` del ejemplo se incluye solamente a efectos de ilustración.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

Puede guardar la tarea HelloWorld en un archivo denominado *HelloWorld.targets* y luego invocarlo desde un proyecto del modo siguiente.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Parámetros de entrada y salida

 Los parámetros de las tareas insertadas son elementos secundarios de un elemento `ParameterGroup`. Cada parámetro toma el nombre del elemento que lo define. En el código siguiente se define el parámetro `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Los parámetros pueden tener uno o más de estos atributos:

- `Required` es un atributo opcional que es `false` de forma predeterminada. Si es `true`, el parámetro es necesario y se le debe proporcionar un valor antes de llamar a la tarea.

- `ParameterType` es un atributo opcional que es `System.String` de forma predeterminada. Se puede establecer en cualquier tipo completo que sea un elemento o un valor que se pueda convertir a y de una cadena utilizando System.Convert.ChangeType. (En otras palabras, cualquier tipo que se pueda pasar a y desde una tarea externa).

- `Output` es un atributo opcional que es `false` de forma predeterminada. Si es `true`, se debe proporcionar al parámetro un valor antes de volver del método Execute.

Por ejemplo,

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

define estos tres parámetros:

- `Expression` es un parámetro de entrada necesario de tipo System.String.

- `Files` es un parámetro de entrada de lista de elementos necesario.

- `Tally` es un parámetro de salida de tipo System.Int32.

Si el elemento `Code` tiene el atributo `Type` de `Fragment` o `Method`, las propiedades se crean automáticamente para cada parámetro.  En RoslynCodeTaskFactory, si el elemento `Code` tiene el atributo `Type` de `Class`, no es necesario especificar `ParameterGroup`, ya que se deduce del código fuente (esto es una diferencia con respecto a `CodeTaskFactory`). De lo contrario, las propiedades se deben declarar explícitamente en el código fuente de la tarea y deben coincidir exactamente con sus definiciones de parámetro.

## <a name="example"></a>Ejemplo

 La tarea insertada siguiente registra algunos mensajes y devuelve una cadena.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Estas tareas insertadas pueden combinar rutas y obtener el nombre de archivo.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Proporcionar compatibilidad con versiones anteriores

`RoslynCodeTaskFactory` está disponible por primera vez en la versión 15.8 de MSBuild. Imaginemos un escenario en el que quiere admitir versiones anteriores de Visual Studio y MSBuild, cuando `RoslynCodeTaskFactory` no estaba disponible, pero `CodeTaskFactory` sí lo estaba, pero quiere usar el mismo script de compilación. Puede usar una construcción `Choose` que use la propiedad `$(MSBuildVersion)` para decidir en tiempo de compilación si usar `RoslynCodeTaskFactory` o revertir a `CodeTaskFactory`, como en el ejemplo siguiente:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Tutorial: Creación de una tarea insertada](../msbuild/walkthrough-creating-an-inline-task.md)
