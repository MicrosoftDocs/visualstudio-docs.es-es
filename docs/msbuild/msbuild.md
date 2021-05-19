---
title: MSBuild | Microsoft Docs
description: Obtenga información sobre cómo la plataforma Microsoft Build Engine (MSBuild) proporciona un archivo de proyecto con un esquema XML para controlar las compilaciones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 372fc5c81b963cbb8e46cab689713e476fcfff7d
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848284"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine es una plataforma para compilar aplicaciones. Este motor, que también se conoce como MSBuild, proporciona un esquema XML para un archivo del proyecto que controla cómo la plataforma de compilación procesa y compila el software. Visual Studio usa MSBuild, pero MSBuild no depende de Visual Studio. Al invocar *msbuild.exe* en el archivo de proyecto o solución, puede orquestar y compilar productos en entornos donde no está instalado Visual Studio.

 Visual Studio utiliza MSBuild para cargar y compilar proyectos administrados. Los archivos de proyecto de Visual Studio ( *.csproj*, *.vbproj*, *.vcxproj*, etc.) contienen código XML de MSBuild que se ejecuta cuando se compila un proyecto mediante el IDE. Los proyectos de Visual Studio importan todos los valores y procesos de compilación necesarios para realizar el trabajo de desarrollo típico, pero se pueden extender o modificar dentro de Visual Studio o mediante un editor XML.

 Para obtener información sobre MSBuild para C++, consulte [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 En los ejemplos siguientes se muestra cuándo se podrían ejecutar compilaciones mediante la invocación de MSBuild desde la línea de comandos en lugar de usar el IDE de Visual Studio.

- Visual Studio no está instalado. ([Descargue MSBuild sin Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools)).

- Desea utilizar la versión de 64 bits de MSBuild. Esta versión de MSBuild normalmente es innecesaria, pero permite que MSBuild tenga acceso a más memoria.

- Desea ejecutar una compilación en varios procesos. Sin embargo, puede utilizar el IDE para lograr el mismo resultado en proyectos de C++ y C#.

- Desea modificar el sistema de compilación. Por ejemplo, quizá desee habilitar las acciones siguientes:

  - Preprocesar los archivos antes de alcanzar el compilador.

  - Copiar los resultados de compilación en un lugar diferente.

  - Crear archivos comprimidos a partir de los resultados de la compilación.

  - Realizar un paso de procesamiento posterior. Por ejemplo, puede ser conveniente crear una marca de tiempo en un ensamblado con una versión diferente.

Puede escribir código en el IDE de Visual Studio, pero ejecutar las compilaciones con MSBuild. Otra alternativa consiste en compilar el código en el IDE en un equipo de desarrollo, pero ejecutar MSBuild desde la línea de comandos para compilar el código que se integra de varios desarrolladores. También puede usar la [interfaz de la línea de comandos (CLI) de .NET Core](/dotnet/core/tools/), que usa MSBuild, para compilar proyectos de .NET Core.

> [!NOTE]
> Puede usar Azure Pipelines para compilar, probar e implementar de forma automática la aplicación. El sistema de compilación puede ejecutar automáticamente las compilaciones cuando los desarrolladores protegen el código (por ejemplo, como parte de una estrategia de integración continua) o según una programación (por ejemplo, una prueba nocturna de comprobación de la compilación). Azure Pipelines compila el código mediante MSBuild. Para obtener más información, consulte [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

En este artículo se proporciona información general sobre MSBuild. Para obtener un tutorial de introducción, consulte [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Uso de MSBuild en un símbolo del sistema

 Para ejecutar MSBuild en un símbolo del sistema, pase un archivo del proyecto a *MSBuild.exe* junto con las opciones de la línea de comandos adecuadas. Las opciones de la línea de comandos permiten establecer propiedades, ejecutar destinos concretos y establecer otras opciones que controlan el proceso de compilación. Por ejemplo, para compilar el archivo *MyProj.proj* con la propiedad `Configuration` establecida en `Debug`, usaría la siguiente sintaxis de línea de comandos.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Para obtener más información acerca de las opciones de la línea de comandos de MSBuild, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Antes de descargar un proyecto, asegúrese de que su código es de confianza.

## <a name="project-file"></a>Archivo del proyecto

 MSBuild usa un formato de archivo del proyecto basado en XML que es sencillo y extensible. El formato de archivo del proyecto de MSBuild permite a los desarrolladores describir los elementos que se van a compilar, y también cómo se van a compilar en diferentes sistemas operativos y configuraciones. Además, el formato del archivo de proyecto permite a los desarrolladores crear reglas de compilación reutilizables que se pueden factorizar en archivos independientes para que las compilaciones se ejecuten de forma coherente en los distintos proyectos del producto.

 En las secciones siguientes se describen algunos de los elementos básicos del formato de archivo de proyecto de MSBuild. Para obtener un tutorial sobre cómo crear un archivo de proyecto básico, vea [Tutorial: Crear un archivo de proyecto de MSBuild desde cero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a> Propiedades

 Las propiedades representan pares clave/valor que se pueden utilizar para configurar compilaciones. Las propiedades se declaran mediante la creación de un elemento que tenga el nombre de la propiedad como elemento secundario de un elemento [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Por ejemplo, el código siguiente crea una propiedad denominada `BuildDir` cuyo valor es `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Puede definir una propiedad condicionalmente si coloca un atributo `Condition` en el elemento. El contenido de los elementos condicionales se omite, a menos que la condición se evalúe como `true`. En el ejemplo siguiente, se define el elemento `Configuration` si aún no se ha definido.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Para hacer referencia a las propiedades en el archivo del proyecto, se usa la sintaxis $(\<PropertyName>). Por ejemplo, se puede hacer referencia a las propiedades de los ejemplos anteriores mediante `$(BuildDir)` y `$(Configuration)`.

 Para más información sobre las propiedades, consulte [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Elementos

 Los elementos son entradas del sistema de compilación y suelen representar archivos. Se agrupan en tipos de elemento en función de los nombres de elemento definidos por el usuario. Estos tipos de elemento se pueden utilizar como parámetros para tareas, que utilizan los elementos individuales para llevar a cabo los pasos del proceso de compilación.

 Los elementos se declaran en el archivo del proyecto mediante la creación de un elemento con el nombre del tipo de elemento como elemento secundario de un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Por ejemplo, el código siguiente crea un tipo de elemento denominado `Compile` que incluye dos archivos.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Para hacer referencia a los tipos de elemento en el archivo de proyecto, se usa la sintaxis @(\<ItemType>). Por ejemplo, para hacer referencia al tipo de elemento del ejemplo, se usaría `@(Compile)`.

 En MSBuild, los nombres de elementos y atributos distinguen mayúsculas de minúsculas. Sin embargo, los nombres de propiedad, elemento y metadatos no las distinguen. El ejemplo siguiente crea el tipo de elemento `Compile`, `comPile` o cualquier otra variación de grafía, y asigna al tipo de elemento el valor "one.cs;two.cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Los elementos se pueden declarar utilizando caracteres comodín y pueden contener metadatos adicionales para escenarios de compilación más avanzados. Para obtener más información sobre los elementos, consulte [Elementos](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Tareas

 Las tareas son unidades de código ejecutable que se utilizan en proyectos de MSBuild para realizar operaciones de compilación. Por ejemplo, una tarea podría compilar archivos de entrada o ejecutar una herramienta externa. Las tareas se pueden reutilizar y las pueden compartir desarrolladores diferentes en distintos proyectos.

 La lógica de ejecución de una tarea se escribe en código administrado y se asigna a MSBuild mediante el elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Puede escribir una tarea creando un tipo administrado que implemente la interfaz <xref:Microsoft.Build.Framework.ITask>. Para más información sobre cómo escribir tareas, consulte [Escribir tareas](../msbuild/task-writing.md).

 MSBuild incluye tareas comunes que puede modificar para adaptarlas a sus necesidades. Algunos ejemplos son [Copy](../msbuild/copy-task.md), que copia archivos, [MakeDir](../msbuild/makedir-task.md), que crea directorios, y [Csc](../msbuild/csc-task.md), que compila archivos de código fuente de Visual C#. Para obtener una lista de las tareas disponibles junto con información de uso, consulte [Referencia de tareas](../msbuild/msbuild-task-reference.md).

 Para ejecutar una tarea en un archivo del proyecto de MSBuild, se crea un elemento con el nombre de la tarea como elemento secundario de un elemento [Target](../msbuild/target-element-msbuild.md). Las tareas aceptan normalmente parámetros, que se pasan como atributos del elemento. Tanto las propiedades como los elementos de MSBuild se pueden utilizar como parámetros. Por ejemplo, el código siguiente llama a la tarea [MakeDir](../msbuild/makedir-task.md) y le pasa el valor de la propiedad `BuildDir` que se declaró en el ejemplo anterior.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Para obtener más información sobre las tareas, consulte [Tareas](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Destinos

 Los destinos agrupan tareas en un orden particular y exponen secciones del archivo de proyecto como puntos de entrada en el proceso de compilación. Los destinos suelen agruparse en secciones lógicas para aumentar la legibilidad y permitir la expansión. Dividir los pasos de compilación en destinos permite llamar a una parte del proceso de compilación desde otros destinos sin necesidad de copiar dicha sección de código en cada destino. Por ejemplo, si varios puntos de entrada del proceso de compilación necesitan que se compilen referencias, se puede crear un destino que compile referencias y, a continuación, ejecutar dicho destino desde cada punto de entrada que sea necesario.

 Los destinos se declaran en el archivo del proyecto mediante el elemento [Target](../msbuild/target-element-msbuild.md). Por ejemplo, en el código siguiente se crea un destino denominado `Compile` que, a continuación, llama a la tarea [Csc](../msbuild/csc-task.md) que tiene la lista de elementos que se declaró en el ejemplo anterior.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 En escenarios más avanzados, los destinos se pueden usar para describir relaciones mutuas y llevar a cabo análisis de dependencia, de modo que se pueden omitir secciones completas del proceso de compilación si un destino concreto está actualizado. Para obtener más información sobre los destinos, consulte [Destinos](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Registros de compilación

 Puede registrar errores de compilación, advertencias y mensajes en la consola o en otro dispositivo de salida. Para más información, consulte [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md) y [Registro de MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Uso de MSBuild en Visual Studio

 Visual Studio usa el formato de archivo de proyecto de MSBuild para almacenar información de generación sobre proyectos administrados. La configuración del proyecto que se agrega o se modifica mediante la interfaz de Visual Studio se refleja en el archivo *.\*proj* que se genera para cada proyecto. Visual Studio utiliza una instancia hospedada de MSBuild para compilar proyectos administrados. Esto significa que un proyecto administrado se puede compilar en Visual Studio o en el símbolo del sistema (aunque Visual Studio no esté instalado) y los resultados serán idénticos.

 Para obtener un tutorial sobre cómo utilizar MSBuild en Visual Studio, vea [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Compatibilidad con múltiples versiones (multi-targeting)

 Con Visual Studio, puede compilar una aplicación para que se ejecute en cualquiera de las versiones de .NET Framework. Por ejemplo, puede compilar una aplicación para que se ejecute en .NET Framework 2.0 en una plataforma de 32 bits y compilar esa misma aplicación para que se ejecute en .NET Framework 4.5 en una plataforma de 64 bits. La capacidad de compilar para más de una versión de Framework se denomina multitargeting.

 Estas son algunas de las ventajas de la compatibilidad con múltiples versiones (multitargeting):

- Puede desarrollar aplicaciones que tengan como destino versiones anteriores de .NET Framework, por ejemplo, las versiones 2.0, 3.0 y 3.5.

- Puede usar como destino otros marcos que no sean .NET Framework, por ejemplo, Silverlight.

- Puede tener como destino un *perfil de Framework*, que es un subconjunto predefinido de un marco de trabajo de destino.

- Si se publica un Service Pack para la versión actual de .NET Framework, podría usarlo como destino.

- La compatibilidad con múltiples versiones (multitargeting) garantiza que una aplicación utilice solo la funcionalidad que está disponible en el marco y plataforma de destino.

Para obtener más información, consulte [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Vea también

| Title | Descripción |
| - | - |
| [Tutorial: Crear un archivo de proyecto de MSBuild desde cero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Muestra la forma de crear un archivo básico del proyecto de forma incremental, utilizando solo un editor de texto. |
| [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md) | Presenta los bloques de compilación de MSBuild y muestra la forma de escribir, manipular y depurar proyectos de MSBuild sin cerrar el IDE de Visual Studio. |
| [Conceptos de MSBuild](../msbuild/msbuild-concepts.md) | Presenta los cuatro bloques de compilación de MSBuild: propiedades, elementos, destinos y tareas. |
| [Elementos](../msbuild/msbuild-items.md) | Describe los conceptos generales en que se basa el formato de archivo de MSBuild y la manera de encajar las piezas. |
| [Propiedades de MSBuild](../msbuild/msbuild-properties.md) | Presenta las propiedades y las colecciones de propiedades. Las propiedades son pares clave/valor que se pueden utilizar para configurar compilaciones. |
| [Destinos](../msbuild/msbuild-targets.md) | Explica cómo agrupar las tareas entre sí en un orden concreto y habilitar las secciones del proceso de compilación para que se las pueda llamar desde la línea de comandos. |
| [Tareas](../msbuild/msbuild-tasks.md) | Muestra la forma de crear una unidad de código ejecutable que MSBuild puede usar para realizar operaciones de compilación indivisibles. |
| [Condiciones](../msbuild/msbuild-conditions.md) | Explica la forma de utilizar el atributo `Condition` en un elemento de MSBuild. |
| [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md) | Presenta el procesamiento por lotes, la realización de transformaciones, la compatibilidad con múltiples versiones (multitargeting) y otras técnicas avanzadas. |
| [Registro de MSBuild](../msbuild/logging-in-msbuild.md) | Describe cómo registrar los eventos, mensajes y errores de compilación. |
| [Cómo MSBuild compila los proyectos](build-process-overview.md) | En este artículo se describe el proceso de compilación interno que se usa en MSBuild. |
| [Recursos adicionales](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Enumera los recursos de compatibilidad y comunidad para obtener más información sobre MSBuild. |

## <a name="reference"></a>Referencia

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)\
 Muestra vínculos a temas que contienen información de referencia.

- [Glosario](msbuild-glossary.md)\
 Define los términos comunes de MSBuild.
