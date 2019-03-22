---
title: Extensibilidad de proyectos de Visual C++
ms.date: 01/25/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a524d242f5c3fb146f3446cd0c020b01e130277c
ms.sourcegitcommit: 5af29226aef0a3b4a506b69a08a97cfd21049521
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58268725"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ sistema extensibilidad y el conjunto de herramientas de integración de Project

El sistema de proyectos de Visual C++ se usa para archivos vcxproj. Se basa en el [sistema común de proyecto (CPS) de Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) y proporciona adicionales, puntos de extensibilidad específica de C++ para facilitar la integración de nuevos conjuntos de herramientas, las arquitecturas de compilación y las plataformas de destino.

## <a name="c-msbuild-targets-structure"></a>Estructura de los destinos de MSBuild de C++

Todos los archivos vcxproj importación estos archivos:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Estos archivos definen poco por sí mismos. En su lugar, importan otros archivos en función de estos valores de propiedad:

- `$(ApplicationType)`

   Ejemplos: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Esto debe ser una cadena de versión válida del formulario de.Revision]].

   Ejemplos: 1.0, 10.0.0.0

- `$(Platform)`

   La arquitectura de la compilación, denominada "Plataforma" por motivos históricos.

   Ejemplos: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Ejemplos: v140, v141, v141_xp, llvm

Estos valores de propiedad especifican los nombres de carpeta en el `$(VCTargetsPath)` carpeta raíz:

`$(VCTargetsPath)`\\ &nbsp;&nbsp;&nbsp;&nbsp;*Tipo de aplicación* \\ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(ApplicationType)` \\ &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ &nbsp;&nbsp;&nbsp;&nbsp;  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *Plataformas* \\ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)` \\ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *PlatformToolsets* \\ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` &nbsp;&nbsp;&nbsp;&nbsp;plataformas\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Se usa cuando `$(ApplicationType)` está vacío, para proyectos de escritorio de Windows) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

### <a name="add-a-new-platform-toolset"></a>Agregar un nuevo conjunto de herramientas de plataforma

Para agregar un nuevo conjunto de herramientas, por ejemplo, "MyToolset" para la plataforma existente de Win32, cree un *MyToolset* carpeta bajo `$(VCTargetsPath)`  *\\plataformas\\Win32\\ PlatformToolsets\\*y crear *Toolset.props* y *Toolset.targets* archivos en ella.

Cada nombre de la carpeta en *PlatformToolsets* aparece en el **las propiedades del proyecto** diálogo como una disponibilidad **conjunto de herramientas de plataforma** para la plataforma especificada, como se muestra aquí:

![La propiedad de conjunto de herramientas de plataforma en el cuadro de diálogo de páginas de propiedades del proyecto](media/vc-project-extensibility-platform-toolset-property.png "propiedad de conjunto de herramientas de la plataforma en el cuadro de diálogo de páginas de propiedades del proyecto")

Crear similar *MyToolset* carpetas y *Toolset.props* y *Toolset.targets* admite este conjunto de herramientas de los archivos de cada carpeta de plataforma existente.

### <a name="add-a-new-platform"></a>Agregar una nueva plataforma

Para agregar una nueva plataforma, por ejemplo, "MyPlatform", cree un *MyPlatform* carpeta bajo `$(VCTargetsPath)`  *\\plataformas\\*y crear  *Platform.Default.props*, *Platform.props*, y *Platform.targets* archivos en ella. Cree también un `$(VCTargetsPath)`  *\\plataformas\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets\\*  carpeta y cree al menos un conjunto de herramientas en ella.

Todos los nombres de carpeta la *plataformas* carpeta para cada `$(ApplicationType)` y `$(ApplicationTypeRevision)` aparecen en el IDE como disponible **plataforma** opciones para un proyecto.

![La elección de plataforma de nuevo en el cuadro de diálogo nueva plataforma de proyecto](media/vc-project-extensibility-new-project-platform.png "elección de la nueva plataforma en el cuadro de diálogo nueva plataforma de proyecto")

### <a name="add-a-new-application-type"></a>Agregar un nuevo tipo de aplicación

Para agregar un nuevo tipo de aplicación, cree un *MyApplicationType* carpeta bajo `$(VCTargetsPath)` *\\tipo de aplicación\\* y cree un *Defaults.props* archivos en ella. Al menos una revisión es necesaria para un tipo de aplicación, por lo que también cree un `$(VCTargetsPath)`  *\\tipo de aplicación\\MyApplicationType\\1.0* carpeta y crear un  *Defaults.props* archivos en ella. También debe crear un `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\plataformas* carpeta y cree al menos una plataforma en ella.

`$(ApplicationType)` y `$(ApplicationTypeRevision)` propiedades no son visibles en la interfaz de usuario. Se definen en las plantillas de proyecto y no se puede cambiar después de crear el proyecto.

## <a name="the-vcxproj-import-tree"></a>El árbol de importación .vcxproj

Un árbol simplificado de las importaciones de archivos de propiedades y destinos de Microsoft C++ tiene el siguiente aspecto:

`$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(MSBuildExtensionsPath)` \\ `$(MSBuildToolsVersion)` \\ *Microsoft.Common.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportBefore*\\*predeterminado* \\ \*. *props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *tipo de aplicación* \\ `$(ApplicationType)` \\ *Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *tipo de aplicación* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Tipo de aplicación*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*plataformas* \\ `$(Platform)` \\ *Platform.default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportAfter*\\*predeterminado*\\\*. *props*

Los proyectos de escritorio de Windows no definen `$(ApplicationType)`, por lo que se importan solo

`$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(MSBuildExtensionsPath)` \\ `$(MSBuildToolsVersion)` \\ *Microsoft.Common.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportBefore*\\*predeterminado* \\ \*. *props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *plataformas* \\ `$(Platform)` \\ *Platform.default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportAfter* \\  *Default*\\\*. *props*

Vamos a usar el `$(_PlatformFolder)` propiedad para alojar el `$(Platform)` las ubicaciones de carpeta de plataforma. Esta propiedad es

`$(VCTargetsPath)`\\*Plataformas*\\`$(Platform)`

para las aplicaciones de escritorio de Windows, y

`$(VCTargetsPath)`\\*Tipo de aplicación*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*plataformas*\\`$(Platform)`

para todo lo demás.

Los archivos props se importan en este orden:

`$(VCTargetsPath)`\\*Microsoft.Cpp.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *Platform.props* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Microsoft.Cpp.Platform.props* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *ImportBefore* \\\*. *props* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props* &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ *</c152>ImportAfter<spanclass="notranslate">*\\\*. *props</span>*

Los archivos de destinos se importan en este orden:

`$(VCTargetsPath)`\\*Microsoft.Cpp.targets* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Microsoft.Cpp.Current.targets* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *Platform.targets* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Microsoft.Cpp.Platform.targets*  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</c102><spanclass="notranslate">&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *destinos* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *PlatformToolsets* \\ `$(PlatformToolset)` \\ *Toolset.target* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *ImportAfter* \\\*. *destinos</span>*

Si tiene que definir algunas propiedades predeterminadas para el conjunto de herramientas, puede agregar archivos a las carpetas ImportBefore e ImportAfter correspondientes.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Archivos Toolset.props autor y Toolset.targets

*Toolset.props* y *Toolset.targets* archivos tienen control total sobre lo que sucede durante una compilación cuando se usa este conjunto de herramientas. También pueden controlar los depuradores disponibles, algunas de la interfaz de usuario IDE, como el contenido de la **páginas de propiedades** cuadro de diálogo y algunos otros aspectos del comportamiento del proyecto.

Aunque un conjunto de herramientas puede invalidar el proceso de compilación completa, normalmente tan solo quiere su conjunto de herramientas para modificar o agregar que algunos pasos de compilación o usar herramientas de compilación diferentes, como parte de un proceso de compilación existente. Para lograr este objetivo, hay una serie de archivos comunes de propiedades y destinos, que puede importar el conjunto de herramientas. Dependiendo de qué desea hacer su conjunto de herramientas, estos archivos pueden resultar útiles para utilizarla como importaciones o como ejemplos:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Este archivo define las partes principales del proceso de compilación nativa y también importa:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Establece los valores predeterminados para los conjuntos de herramientas que usan los compiladores de Microsoft y Windows de destino.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Este archivo determina la ubicación del SDK de Windows y define algunas propiedades importantes para aplicaciones destinadas a Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrar destinos específicos del conjunto de herramientas con la predeterminada del proceso de compilación de C++

El proceso de compilación de C++ de predeterminado se define en *Microsoft.CppCommon.targets*. Allí los destinos no llame a las herramientas de compilación concreta; especifican los principales pasos, el orden y sus dependencias de compilación.

La compilación de C++ tiene tres pasos principales que están representados por los siguientes destinos:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Dado que cada paso de compilación se puede ejecutar de forma independiente, los destinos que se ejecutan en un paso no pueden confiar en los grupos de elementos y propiedades definidos en los destinos que se ejecutan como parte de un paso diferente. Esta división permite cierta compilación optimizaciones de rendimiento. Aunque no se usa de forma predeterminada, está todavía le anima a respetar esta separación.

Los destinos que se ejecutan dentro de cada paso se controlan mediante estas propiedades:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Cada paso tiene también propiedades precedentes y posteriores.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Consulte la *Microsoft.CppBuild.targets* archivo para ver ejemplos de los destinos que se incluyen en cada paso:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Si observa los destinos, como `_ClCompile`, verá que no hacen nada directamente por sí mismos, pero en su lugar, dependen de otros destinos, incluidos `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` y otro compilar destinos específicos de la herramienta se definen como destinos vacíos de *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Dado que el `ClCompile` destino está vacío, a menos que se haya reemplazado por un conjunto de herramientas, no se realiza ninguna acción de compilación real. Los destinos del conjunto de herramientas pueden reemplazar el `ClCompile` de destino, es decir, puede contener otro `ClCompile` definición después de importar *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

A pesar de su nombre, que se creó antes de Visual Studio implementa la compatibilidad multiplataforma, el `ClCompile` destino no tiene que llamar a CL.exe. También puede llamar gcc, Clang o con otros compiladores mediante el uso de las tareas de MSBuild adecuadas.

El `ClCompile` destino no debe contener todas las dependencias, excepto el `SelectClCompile` destino, que es necesario para el comando de compilación de único archivo trabajar en el IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Tareas de MSBuild para usar en los destinos del conjunto de herramientas

Para invocar una herramienta de compilación real, el destino debe llamar a una tarea de MSBuild. Hay un basic [tarea Exec](../msbuild/exec-task.md) que le permite especificar una línea de comandos para ejecutar. Sin embargo, las herramientas de compilación normalmente tienen muchas opciones, las entradas. y las salidas para realizar el seguimiento de compilaciones incrementales, por lo que tiene más sentido tener tareas especiales para ellos. Por ejemplo, la `CL` tarea traduce las propiedades de MSBuild en conmutadores de CL.exe, escribe en un archivo de respuesta y llama a CL.exe. También realiza un seguimiento todos los archivos de entrada y salidos para las compilaciones incrementales más adelante. Para obtener más información, consulte [las compilaciones incrementales y comprobaciones actualizadas](#incremental-builds-and-up-to-date-checks).

El Microsoft.Cpp.Common.Tasks.dll implementa estas tareas:

- `BSCMake`

- `CL`

- `ClangCompile` (modificadores de clang y gcc)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (como Exec pero con la entrada y salida de seguimiento)

- `SetEnv`

- `GetOutOfDateItems`

Si tiene una herramienta que realiza la misma acción que una herramienta existente y que tiene los modificadores de línea de comandos similar (como clang-cl y CL), puede usar la misma tarea para ambos.

Si necesita crear una nueva tarea para una herramienta de compilación, puede elegir entre las siguientes opciones:

1. Si usa esta tarea con poca frecuencia, o si no importan unos segundos para la compilación, puede usar las tareas de MSBuild 'inline':

   - Tarea de XAML (una regla de compilación personalizada)

     Para obtener un ejemplo de una declaración de la tarea de Xaml, vea `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*y para su uso, consulte `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Tarea de código](../msbuild/msbuild-inline-tasks.md)

1. Si desea obtener un mejor rendimiento de la tarea o simplemente necesita funcionalidad más compleja, use el normal de MSBuild [escribir tareas](../msbuild/task-writing.md) proceso.

   Si no todas las entradas y salidas de la herramienta se muestran en la línea de comandos de la herramienta, como en el `CL`, `MIDL`, y `RC` casos y, si desea entrada automática y seguimiento de archivos de salida y creación de archivos .tlog, derive su tarea desde el `Microsoft.Build.CPPTasks.TrackedVCToolTask`clase. En este momento, aunque no hay documentación para la base de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) de clases, no existen ejemplos o documentación para obtener los detalles de la `TrackedVCToolTask` clase. Si esto es de especial interés, agregar su voz a una solicitud en [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Las compilaciones incrementales y comprobaciones actualizadas

La compilación incremental de MSBuild predeterminado tiene como destino uso `Inputs` y `Outputs` atributos. Si se especifica, MSBuild llama al destino sólo si cualquiera de las entradas tiene una marca de tiempo más reciente de todas las salidas. Porque a menudo archivos de código fuente incluirán o importan otros archivos y generación herramientas generan resultados diferentes dependiendo de las opciones de herramienta, es difícil especificar todas las posibles entradas y salidas en destinos de MSBuild.

Para administrar este problema, la compilación de C++ usa una técnica diferente para admitir las compilaciones incrementales. La mayoría de los destinos no especificar entradas y salidas y como resultado, siempre se ejecutan durante la compilación. Las tareas que se llama a destinos de escriben información acerca de todas las entradas y salidas en *tlog* archivos que tienen una extensión .tlog. Los archivos .tlog son usados por compilaciones posteriores para comprobar qué ha cambiado y debe volver a generar y, lo que está actualizado. Los archivos .tlog también son el único origen para la comprobación de actualización de la compilación de forma predeterminada en el IDE.

Para determinar todas las entradas y salidas, las tareas de la herramienta nativa usan tracker.exe y [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) clase proporcionada por MSBuild.

Microsoft.Build.CPPTasks.Common.dll define el `TrackedVCToolTask` clase base abstracta pública. La mayoría de las tareas de la herramienta nativa se deriva de esta clase.

A partir de Visual Studio 2017 update 15,8, puede usar el `GetOutOfDateItems` implementado en Microsoft.Cpp.Common.Tasks.dll para generar archivos .tlog para destinos personalizados con conocidos entradas y salidas de tareas.
Como alternativa, puede crear mediante la `WriteLinesToFile` tarea. Consulte la `_WriteMasmTlogs` tener como destino en `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* como ejemplo.

## <a name="tlog-files"></a>archivos .tlog

Hay tres tipos de archivos .tlog: *leer*, *escribir*, y *de línea de comandos*. Archivos .tlog de lectura y escritura se usan las compilaciones incrementales y la comprobación actualizada en el IDE. Archivos .tlog de línea de comandos solo se usan en las compilaciones incrementales.

MSBuild proporciona estas clases auxiliares para leer y escribir archivos .tlog:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

El [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) clase puede utilizarse para tener acceso tanto de lectura y escribir archivos .tlog e identificar las entradas que son más recientes que da como resultado, o si falta una salida. Se utiliza en la comprobación de actualización.

Archivos .tlog de línea de comandos contienen información acerca de las líneas de comandos que se usará en la compilación. Solo se usan para las compilaciones incrementales, las comprobaciones no actualizadas, por lo que el formato interno viene determinada por la tarea de MSBuild que los genera.


### <a name="read-tlog-format"></a>Formato de lectura .tlog

*Lectura* archivos .tlog (\*Read.\*. registro de transacciones) contienen información sobre los archivos de origen y sus dependencias.

Un símbolo de intercalación (**^**) al principio de una línea indica uno o varios orígenes. Orígenes que comparten las mismas dependencias están separados por una barra vertical (**\|**).

Archivos de dependencia se muestran después de los orígenes, cada uno en su propia línea. Todos los nombres de archivo son rutas de acceso completas.

Por ejemplo, suponga que los orígenes del proyecto se encuentran en *F:\\probar\\ConsoleApplication1\\ConsoleApplication1*. Si el archivo de origen, *Class1.cpp*, estos se incluye,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

el *CL.read.1.tlog* archivo contiene el archivo de origen, seguido de sus dos dependencias:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

No es necesario escribir los nombres de archivo en mayúsculas, pero resulta práctico para algunas herramientas.

### <a name="write-tlog-format"></a>Escribir .tlog formato

*Escribir* .tlog (\*.write.\*. archivos de registro de transacciones) conectan los orígenes y las salidas.

Un símbolo de intercalación (**^**) al principio de una línea indica uno o varios orígenes. Varios orígenes están separados por una barra vertical (**\|**).

Los archivos de salida que se crean a partir de los orígenes deben aparecer después de los orígenes, cada uno en su propia línea. Todos los nombres de archivo deben ser rutas de acceso completas.

Por ejemplo, para un proyecto de aplicación de consola simple que tiene un archivo de origen adicionales *Class1.cpp*, *link.write.1.tlog* archivo puede contener:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Compilación en tiempo de diseño

En el IDE, .vcxproj proyectos utilizan un conjunto de destinos de MSBuild para obtener información adicional desde el proyecto y volver a generar los archivos de salida. Solo algunos de estos destinos se usan en las compilaciones de tiempo de diseño, pero muchas de ellas se utilizan en las compilaciones regulares y las compilaciones de tiempo de diseño.

Para obtener información general sobre las compilaciones de tiempo de diseño, vea la documentación de CPS para [se basa en tiempo de diseño](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Esta documentación solo está parcialmente aplicable a proyectos de Visual C++.

El `CompileDesignTime` y `Compile` documentación nunca ejecutado para proyectos .vcxproj se basa los destinos que se mencionan en el tiempo de diseño. Proyectos de Visual C++ .vcxproj usan distintos destinos de tiempo de diseño para obtener información de IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Objetivos de tiempo de diseño de la información de IntelliSense

Los objetivos de tiempo de diseño usados en los proyectos .vcxproj se definen en `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

El `GetClCommandLines` destino recopila las opciones del compilador de IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` : tiempo de diseño solo la inicialización de compilación de destinos, necesarios para el tiempo de diseño. Entre otras cosas, estos destinos deshabilitar algunas de las funcionalidades de compilación normal para mejorar el rendimiento.

- `ComputeCompileInputsTargets` : un conjunto de destinos que modifica las opciones del compilador y los elementos. Estos destinos se ejecutan en las compilaciones regulares y de tiempo de diseño.

Las llamadas de destino la `CLCommandLine` tarea para crear la línea de comandos para IntelliSense. De nuevo, a pesar de su nombre, puede controlar no sólo las opciones de CL, sino también las opciones Clang y gcc. El tipo de los modificadores de compilador se controla mediante el `ClangMode` propiedad.

Actualmente, la línea de comandos generada por el `CLCommandLine` tarea siempre usa conmutadores de CL (incluso en modo de Clang) porque son más fáciles para el motor de IntelliSense para analizar.

Si va a agregar un destino que se ejecuta antes de la compilación, ya sea regular o tiempo de diseño, asegúrese de que no se interrumpe el tiempo de diseño se basa o afectar al rendimiento. La manera más sencilla para probar su destino es abrir un símbolo del sistema para desarrolladores y ejecute este comando:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Este comando genera un registro de compilación detalladas, *msbuild.log*, que tiene un resumen de los destinos y tareas de rendimiento al final.

Asegúrese de usar `Condition ="'$(DesignTimeBuild)' != 'true'"` en todas las operaciones que solo tienen sentido para las compilaciones periódicas y no para las compilaciones de tiempo de diseño.

### <a name="design-time-targets-that-generate-sources"></a>Objetivos de tiempo de diseño que generan fuentes

*Esta característica está deshabilitada de forma predeterminada para proyectos nativos de escritorio y no se admite actualmente en los proyectos almacenados en caché*.

Si `GeneratorTarget` los metadatos se definen para un elemento de proyecto, el destino se ejecuta automáticamente tanto cuando se carga el proyecto y cuando se cambia el archivo de origen.

::: moniker range="vs-2017"

Por ejemplo, para generar automáticamente .cpp o .h archivos desde los archivos .xaml, el `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* archivos definen estos entidades:

::: moniker-end

::: moniker range=">=vs-2019"

Por ejemplo, para generar automáticamente .cpp o .h archivos desde los archivos .xaml, el `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v16.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* archivos definen estos entidades:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Para usar `Task.HostObject` para obtener el contenido que no haya guardado de archivos de origen, se deben registrar los destinos y tareas como [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) para los proyectos en un pkgdef determinados:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Extensibilidad de proyectos de Visual C++ en el IDE de Visual Studio

El sistema de proyectos de Visual C++ se basa en el [sistema del proyecto de VS](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)y utiliza sus puntos de extensibilidad. Sin embargo, la implementación de la jerarquía de proyecto es específica de Visual C++ y no se basa en CPS, extensibilidad de la jerarquía se limita a los elementos de proyecto.

### <a name="project-property-pages"></a>Páginas de propiedades del proyecto

Para obtener información general de diseño, vea [Framework Multi-Targeting para proyectos de VC ++](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

En otras palabras, las páginas de propiedades se vea en el **las propiedades del proyecto** cuadro de diálogo para un proyecto de C++ se definen mediante *regla* archivos. Un archivo de reglas especifica un conjunto de propiedades para mostrar en una página de propiedades y cómo y dónde debe guardarse en el proyecto de archivos. Los archivos de reglas son archivos .xml que usar el formato Xaml. Se describen los tipos utilizados para serializarlos en [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Para obtener más información sobre el uso de archivos de reglas en los proyectos, vea [los archivos de reglas de XML de la página de propiedades](/cpp/build/reference/property-page-xml-files).

Los archivos de regla deben agregarse a la `PropertyPageSchema` grupo de elementos:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` metadatos limita la visibilidad de la regla, que también se controla mediante el tipo de regla y puede tener uno de estos valores:

`Project` | `File` | `PropertySheet`

CPS admite otros valores para el tipo de contexto, pero no se usan en proyectos de Visual C++.

Si la regla debe estar visible en más de un contexto, use punto y coma (**;**) para separar los valores de contexto, como se muestra aquí:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Formato de regla y los tipos principales

El formato de la regla es sencillo, por lo que en esta sección solo se describe los atributos que afectan al aspecto de la regla en la interfaz de usuario.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

El `PageTemplate` atributo define cómo se muestra la regla en el **páginas de propiedades** cuadro de diálogo. El atributo puede tener uno de estos valores:

| Atributo | Descripción |
|------------| - |
| `generic` | Todas las propiedades se muestran en una sola página bajo los encabezados de categoría<br/>La regla puede ser visible para `Project` y `PropertySheet` contextos, pero no `File`.<br/><br/> Ejemplo: `$(VCTargetsPath)`\\*1033*\\*general.xml* |
| `tool` | Las categorías se muestran como subpáginas.<br/>La regla puede ser visible en todos los contextos: `Project`, `PropertySheet` y `File`.<br/>La regla sólo está visible en las propiedades del proyecto si el proyecto tiene elementos con el `ItemType` definido en `Rule.DataSource`, a menos que se incluye el nombre de regla en el `ProjectTools` grupo de elementos.<br/><br/>Ejemplo: `$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | La página se muestra como parte de la página de depuración.<br/>Actualmente se omiten las categorías.<br/>El nombre de la regla debe coincidir con el objeto de MEF de iniciador de depuración `ExportDebugger` atributo.<br/><br/>Ejemplo: `$(VCTargetsPath)`\\*1033*\\*debugger\_local\_windows.xml* |
| *custom* | Plantilla personalizada. Debe coincidir con el nombre de la plantilla de la `ExportPropertyPageUIFactoryProvider` atributo de la `PropertyPageUIFactoryProvider` objeto MEF. Consulte **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Ejemplo: `$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

Si la regla usa una de las plantillas de la cuadrícula de propiedades, pueden usar estos puntos de extensibilidad para sus propiedades:

- [Editores de valores de propiedad](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Proveedor de valores de enumeración dinámica](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Extender una regla

Si desea usar una regla existente, pero necesita agregar o quitar (que es, ocultar) solo unas pocas propiedades, puede crear un [regla extensión](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Invalidar una regla

Quizás desee su conjunto de herramientas para usar la mayoría de las reglas predeterminadas de proyecto, pero para reemplazar solo uno o algunos de ellos. Por ejemplo, supongamos que desea cambiar la regla de C/C ++ para mostrar los modificadores de compilador diferentes. Puede proporcionar una nueva regla con el mismo nombre y nombre para mostrar que la regla existente e incluirlo en el `PropertyPageSchema` grupo de elementos después de la importación de destinos de cpp de forma predeterminada. Se usa solo una regla con el nombre especificado en el proyecto y la última de ellas se incluye en el `PropertyPageSchema` wins de grupo de elementos.

#### <a name="project-items"></a>elementos de proyecto

El *ProjectItemsSchema.xml* archivo define la `ContentType` y `ItemType` valores para los elementos que se tratan como elementos de proyecto y define `FileExtension` elementos para determinar qué grupo de elementos que se agrega un nuevo archivo a.

El archivo de ProjectItemsSchema predeterminado se encuentra en `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*. Incluir en ella, debe crear un archivo de esquema con un nuevo nombre, como *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

A continuación, en el archivo de destinos, agregue:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Ejemplo: `$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Depuradores

El servicio de depuración en Visual Studio admite la extensibilidad para el motor de depuración. Para obtener más información, vea estos ejemplos:

- [MIEngine, proyecto de código abierto que admite la depuración lldb](https://github.com/Microsoft/MIEngine)

- [Ejemplo de motor de depuración de Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Para especificar los motores de depuración y otras propiedades para la sesión de depuración, debe implementar un [iniciador de depuración](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) componente MEF y agregue un `debugger` regla. Para obtener un ejemplo, vea el `$(VCTargetsPath)` \\1033\\depurador\_local\_windows.xml archivo.

### <a name="deploy"></a>Implementar

los proyectos de .vcxproj usan la extensibilidad del sistema de proyectos de Visual Studio para [implementar proveedores](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Comprobación de actualización de compilación

De forma predeterminada, la comprobación de actualización de compilación requiere lectura .tlog y escribir los archivos de .tlog que se van a crearse en el `$(TlogLocation)` carpeta durante la compilación para todas las compilación entradas y salidas.

Para usar una comprobación de actualización personalizada:

1. Deshabilitar la comprobación de actualización predeterminado agregando la `NoVCDefaultBuildUpToDateCheckProvider` capacidad en el *Toolset.targets* archivo:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementar su propia [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Actualización del proyecto

### <a name="default-vcxproj-project-upgrader"></a>Actualizador de proyecto .vcxproj predeterminado

Los cambios de actualizador del proyecto predeterminado .vcxproj el `PlatformToolset`, `ApplicationTypeRevision`, conjunto de herramientas de MSBuild versión y .net framework. Las dos últimas siempre se cambian los valores predeterminados de Visual Studio versión, pero `PlatformToolset` y `ApplicationTypeRevision` puede controlarse mediante propiedades especiales de MSBuild.

El actualizador utiliza estos criterios para decidir si se puede actualizar un proyecto o no:

1. Para los proyectos que definen `ApplicationType` y `ApplicationTypeRevision`, hay una carpeta con un mayor número de revisión de la actual.

1. La propiedad `_UpgradePlatformToolsetFor_<safe_toolset_name>` está definido para el conjunto de herramientas actual y su valor no es igual que el conjunto de herramientas actual.

   En estos nombres de propiedad,  *\<safe_toolset_name >* representa el nombre del conjunto de herramientas con todos los caracteres no alfanuméricos reemplazados por un carácter de subrayado (**\_**).

Cuando se puede actualizar un proyecto, participa en *redestinar solución*. Para obtener más información, consulte [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Si desea agregar adornos a nombres de proyecto de **el Explorador de soluciones** cuando los proyectos usan un conjunto de herramientas específica, defina un `_PlatformToolsetShortNameFor_<safe_toolset_name>` propiedad.

Para obtener ejemplos de `_UpgradePlatformToolsetFor_<safe_toolset_name>` y `_PlatformToolsetShortNameFor_<safe_toolset_name>` definiciones de propiedades, vea el *Microsoft.Cpp.Default.props* archivo. Para obtener ejemplos de uso, consulte el `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* archivo.

### <a name="custom-project-upgrader"></a>Actualizador de proyecto personalizadas

Para usar un objeto del actualizador de proyecto personalizadas, implemente un componente MEF, como se muestra aquí:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

El código puede importar y llamar al objeto de actualizador .vcxproj predeterminada:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` se define en *Microsoft.VisualStudio.ProjectSystem.VS.dll* y es similar a `IVsRetargetProjectAsync`.

Definir la `VCProjectUpgraderObjectName` propiedad para indicar al sistema de proyecto para utilizar su objeto personalizado del actualizador:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Deshabilitar la actualización del proyecto

Para deshabilitar las actualizaciones del proyecto, use un `NoUpgrade` valor:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Caché de proyectos y extensibilidad

Para mejorar el rendimiento cuando se trabaja con grandes soluciones de C++ en Visual Studio 2017, el [proyecto caché](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) introducida. Se implementa como una base de datos de SQLite rellena con datos del proyecto y, a continuación, se usa para cargar los proyectos sin cargar los proyectos de MSBuild o CPS en la memoria.

Dado que no hay ningún objeto de CPS presente para los proyectos de .vcxproj cargados desde la memoria caché, los componentes MEF de la extensión importar `UnconfiguredProject` o `ConfiguredProject` no se puede crear. Para admitir la extensibilidad, la caché del proyecto no se usa cuando Visual Studio detecta si un proyecto utiliza (o es probable que use) en las extensiones MEF.

Estos tipos de proyecto siempre se carguen por completo y tienen objetos de CPS en memoria, por lo que se crean todas las extensiones MEF para ellos:

- Proyectos de inicio

- Los proyectos que tienen un actualizador de proyecto personalizadas, es decir, definen un `VCProjectUpgraderObjectName` propiedad

- Los proyectos que no están destinadas a Windows Desktop, es decir, definen un `ApplicationType` propiedad

- Compartir proyectos de elementos (.vcxitems) y todos los proyectos que hacen referencia a ellos mediante la importación de proyectos .vcxitems.

Si se detecta ninguna de estas condiciones, se crea una memoria caché del proyecto. La memoria caché incluye todos los datos desde el proyecto de MSBuild necesarios para responder a `get` consultas en `VCProjectEngine` interfaces. Esto significa que todas las modificaciones en las propiedades de MSBuild y nivel de archivo de destinos realiza por una extensión debería funcionar en los proyectos cargados desde la memoria caché.

## <a name="shipping-your-extension"></a>La extensión de envío

Para obtener información sobre cómo crear archivos VSIX, vea [envío extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Para obtener información acerca de cómo agregar archivos a ubicaciones de instalación especial, por ejemplo, para agregar archivos en `$(VCTargetsPath)`, consulte [instalación fuera de la carpeta de extensiones](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Recursos adicionales

El sistema de compilación de Microsoft ([MSBuild](../msbuild/msbuild.md)) proporciona el motor de compilación y el formato extensible basado en XML para archivos de proyecto. Debe estar familiarizado con basic [conceptos de MSBuild](../msbuild/msbuild-concepts.md) y con la forma [MSBuild de Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) funciona con el fin de ampliar Visual C++ de sistema de proyectos.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) proporciona la extensión de API que se usan por el sistema de proyectos de Visual C++ y CPS. Para obtener información general de cómo se usa MEF CPS, consulte [CPS y MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) en el [VSProjectSystem introducción de MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Puede personalizar el sistema de compilación existente para agregar pasos de compilación o nuevos tipos de archivo. Para obtener más información, consulte [información general sobre MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) y [trabajar con las propiedades del proyecto](/cpp/build/working-with-project-properties).
