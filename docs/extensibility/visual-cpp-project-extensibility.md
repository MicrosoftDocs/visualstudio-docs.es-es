---
description: El sistema del proyecto Visual C++ se usa para los archivos. vcxproj.
title: Extensibilidad de Visual C++ proyecto
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc538402ae39753f14a3bccd8bcd17ddb0081078
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221241"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Extensibilidad del sistema de proyectos de Visual Studio C++ y integración del conjunto de herramientas

El sistema del proyecto Visual C++ se usa para los archivos. vcxproj. Se basa en el [sistema de proyectos común (CPS) de Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) y proporciona puntos de extensibilidad adicionales específicos de C++ para facilitar la integración de nuevos conjuntos de herramientas, arquitecturas de compilación y plataformas de destino.

## <a name="c-msbuild-targets-structure"></a>Estructura de destinos de MSBuild para C++

Todos los archivos. vcxproj importan estos archivos:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Estos archivos definen unos pocos. En su lugar, importan otros archivos basados en estos valores de propiedad:

- `$(ApplicationType)`

   Ejemplos: tienda Windows, Android, Linux

- `$(ApplicationTypeRevision)`

   Debe ser una cadena de versión válida con el formato principal. secundario [. compilación [. Revisión]].

   Ejemplos: 1,0, 10.0.0.0

- `$(Platform)`

   La arquitectura de compilación, denominada "plataforma" por motivos históricos.

   Ejemplos: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Ejemplos: V140, v141, v141_xp, LLVM

Estos valores de propiedad especifican nombres de carpeta en la `$(VCTargetsPath)` carpeta raíz:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Tipo de aplicación*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Select*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Select*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

La `$(VCTargetsPath)` \\  \\ carpeta Platforms se utiliza cuando `$(ApplicationType)` está vacía, para los proyectos de escritorio de Windows.

### <a name="add-a-new-platform-toolset"></a>Agregar un nuevo conjunto de herramientas de la plataforma

Para agregar un nuevo conjunto de herramientas, por ejemplo, "mi Toolset" para la plataforma Win32 existente, cree una carpeta mi *Toolset* en `$(VCTargetsPath)` *\\ Platforms \\ Win32 \\ \\ PlatformToolsets* y cree archivos *Toolset. props* y *Toolset. targets* en ella.

Cada nombre de carpeta de *PlatformToolsets* aparece en el cuadro de diálogo de **propiedades del proyecto** como un conjunto de herramientas de la **plataforma** disponible para la plataforma especificada, como se muestra aquí:

![Propiedad conjunto de herramientas de la plataforma en el cuadro de diálogo páginas de propiedades del proyecto](media/vc-project-extensibility-platform-toolset-property.png "Propiedad conjunto de herramientas de la plataforma en el cuadro de diálogo páginas de propiedades del proyecto")

Cree carpetas *de un conjunto de* herramientas y archivos *Toolset. props* y *Toolset. targets* similares en cada carpeta de la plataforma existente que este conjunto de herramientas admita.

### <a name="add-a-new-platform"></a>Agregar una nueva plataforma

Para agregar una nueva plataforma, por ejemplo, "mi plataforma", cree una carpeta de la *plataforma* en `$(VCTargetsPath)` *\\ \\ plataformas* y cree archivos *Platform. default. props*, *Platform. props* y *Platform. targets* en ella. Cree también una `$(VCTargetsPath)` carpeta *\\ \\ Platforms**\\ PlatformToolsets \\* de <strong><em>Platform</em></strong>y cree al menos un conjunto de herramientas en ella.

Todos los nombres de carpeta de la carpeta *Platforms* de cada `$(ApplicationType)` y `$(ApplicationTypeRevision)` aparecen en el IDE como opciones de **plataforma** disponibles para un proyecto.

![La nueva opción de plataforma en el cuadro de diálogo Nueva plataforma de proyecto](media/vc-project-extensibility-new-project-platform.png "La nueva opción de plataforma en el cuadro de diálogo Nueva plataforma de proyecto")

### <a name="add-a-new-application-type"></a>Agregar un nuevo tipo de aplicación

Para agregar un nuevo tipo de aplicación, cree una carpeta *MyApplicationType* en `$(VCTargetsPath)` *\\ tipo \\ de aplicación* y cree un archivo *predeterminados. props* en ella. Se requiere al menos una revisión para un tipo de aplicación, por lo que también debe crear una `$(VCTargetsPath)` carpeta de *\\ tipo de aplicación \\ MyApplicationType \\ 1,0* y crear un archivo *defaults. props* en ella. También debe crear una carpeta `$(VCTargetsPath)` *\\ ApplicationType \\ MyApplicationType \\ 1,0 \\ Platforms* y crear al menos una plataforma en ella.

`$(ApplicationType)` las `$(ApplicationTypeRevision)` propiedades y no están visibles en la interfaz de usuario. Se definen en las plantillas de proyecto y no se pueden cambiar una vez creado el proyecto.

## <a name="the-vcxproj-import-tree"></a>Árbol de importación. vcxproj

Un árbol simplificado de importaciones para archivos de destino y propiedades de Microsoft C++ tiene el siguiente aspecto:

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Valor predeterminado* \\ \* . *propiedades* de \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ Tipo `$(ApplicationType)` de \\ aplicación *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ Tipo `$(ApplicationType)` \\ de `$(ApplicationTypeRevision)` aplicación \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ Tipo `$(ApplicationType)` \\ de `$(ApplicationTypeRevision)` aplicación \\ *Plataformas* \\ `$(Platform)` de \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Valor predeterminado* \\ \* . *propiedades* de

Los proyectos de escritorio de Windows no definen `$(ApplicationType)` , por lo que solo importan

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Valor predeterminado* \\ \* . *propiedades* de \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Plataformas* \\ `$(Platform)` de \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Valor predeterminado* \\ \* . *propiedades* de

Usaremos la `$(_PlatformFolder)` propiedad para almacenar las ubicaciones de la carpeta de la `$(Platform)` plataforma. Esta propiedad es

> `$(VCTargetsPath)`\\*Select*\\`$(Platform)`

para las aplicaciones de escritorio de Windows y

> `$(VCTargetsPath)`\\ \\ Tipo `$(ApplicationType)` \\ de `$(ApplicationTypeRevision)` aplicación \\ *Plataformas* de\\`$(Platform)`

para todo lo demás.

Los archivos de propiedades se importan en este orden:

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *propiedades* de \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\ *Toolset. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *propiedades* de

Los archivos de destinos se importan en este orden:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Plataforma. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *destinos* de \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\ *Toolset. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *destinos* de

Si necesita definir algunas propiedades predeterminadas para el conjunto de herramientas, puede Agregar archivos a las carpetas ImportBefore y ImportAfter apropiadas.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Archivos Toolset. props y Toolset. targets de Author

Los archivos *Toolset. props* y *Toolset. targets* tienen control total sobre lo que sucede durante una compilación cuando se usa este conjunto de herramientas. También pueden controlar los depuradores disponibles, algunas de las interfaces de usuario del IDE, como el contenido del cuadro de diálogo **páginas de propiedades** , y otros aspectos del comportamiento del proyecto.

Aunque un conjunto de herramientas puede invalidar todo el proceso de compilación, normalmente solo desea que el conjunto de herramientas modifique o agregue algunos pasos de compilación, o use herramientas de compilación diferentes, como parte de un proceso de compilación existente. Para lograr este objetivo, hay una serie de archivos de propiedades y destinos comunes que el conjunto de herramientas puede importar. Dependiendo de lo que desee hacer con el conjunto de herramientas, estos archivos pueden ser útiles para usarlos como importaciones o como ejemplos:

- `$(VCTargetsPath)`\\*Microsoft. CppCommon. targets*

  Este archivo define las partes principales del proceso de compilación nativo y también importa:

  - `$(VCTargetsPath)`\\*Microsoft. CppBuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. BuildSteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Establece valores predeterminados para los conjuntos de herramientas que usan los compiladores de Microsoft y las ventanas de destino.

- `$(VCTargetsPath)`\\*Microsoft. cpp. WindowsSDK. props*

   Este archivo determina el Windows SDK ubicación y define algunas propiedades importantes para las aplicaciones destinadas a Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrar destinos específicos del conjunto de herramientas con el proceso de compilación de C++ predeterminado

El proceso de compilación predeterminado de C++ se define en *Microsoft. CppCommon. targets*. Los destinos no llaman a ninguna herramienta de compilación específica; especifican los pasos de compilación principales, su orden y sus dependencias.

La compilación de C++ tiene tres pasos principales, que se representan mediante los siguientes destinos:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Dado que cada paso de compilación se puede ejecutar de forma independiente, los destinos que se ejecutan en un paso no pueden basarse en los grupos de elementos y las propiedades definidos en los destinos que se ejecutan como parte de un paso diferente. Esta división permite ciertas optimizaciones de rendimiento de la compilación. Aunque no se utilice de forma predeterminada, se recomienda seguir esta separación.

Estas propiedades controlan los destinos que se ejecutan dentro de cada paso:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Cada paso también tiene las propiedades Before y after.

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

Vea el archivo *Microsoft. CppBuild. targets* para obtener ejemplos de los destinos que se incluyen en cada paso:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Si observa los destinos, como `_ClCompile` , verá que no hacen nada directamente, sino que dependen de otros destinos, entre los que se incluyen `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` y otros destinos específicos de la herramienta de compilación se definen como destinos vacíos en *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"/>
```

Dado `ClCompile` que el destino está vacío, a menos que sea invalidado por un conjunto de herramientas, no se realiza ninguna acción de compilación real. Los destinos del conjunto de herramientas pueden invalidar el `ClCompile` destino, es decir, pueden contener otra `ClCompile` definición después de importar *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

A pesar de su nombre, que se creó antes de que Visual Studio implementara la compatibilidad entre plataformas, el `ClCompile` destino no tiene que llamar a CL.exe. También puede llamar a Clang, GCC u otros compiladores mediante las tareas de MSBuild adecuadas.

El `ClCompile` destino no debe tener ninguna dependencia, excepto el `SelectClCompile` destino, que es necesario para que el comando compilar de un solo archivo funcione en el IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Tareas de MSBuild que se usan en destinos de conjunto de herramientas

Para invocar una herramienta de compilación real, el destino debe llamar a una tarea de MSBuild. Hay una tarea de [ejecución](../msbuild/exec-task.md) básica que le permite especificar la línea de comandos que se va a ejecutar. Sin embargo, las herramientas de compilación suelen tener muchas opciones, entradas. y realiza un seguimiento de las compilaciones incrementales, por lo que tiene más sentido tener tareas especiales para ellas. Por ejemplo, la `CL` tarea convierte las propiedades de MSBuild en CL.exe modificadores, las escribe en un archivo de respuesta y llama a CL.exe. También realiza un seguimiento de todos los archivos de entrada y salida para las compilaciones incrementales posteriores. Para obtener más información, consulte [compilaciones incrementales y comprobaciones actualizadas](#incremental-builds-and-up-to-date-checks).

El Microsoft.Cpp.Common.Tasks.dll implementa estas tareas:

- `BSCMake`

- `CL`

- `ClangCompile` (Clang-GCC modificadores)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (como exec pero con seguimiento de entrada y salida)

- `SetEnv`

- `GetOutOfDateItems`

Si tiene una herramienta que realiza la misma acción que una herramienta existente y que tiene modificadores de línea de comandos similares (como Clang-cl y CL), puede usar la misma tarea para ambos.

Si necesita crear una nueva tarea para una herramienta de compilación, puede elegir entre las siguientes opciones:

1. Si utiliza esta tarea con poca frecuencia, o si algunos segundos no importan la compilación, puede usar las tareas de MSBuild ' en línea ':

   - Tarea XAML (regla de compilación personalizada)

     Para ver un ejemplo de una declaración de tarea XAML, consulte `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml* y, para su uso, consulte `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets*.

   - [Tarea de código](../msbuild/msbuild-inline-tasks.md)

1. Si desea mejorar el rendimiento de las tareas o simplemente necesita una funcionalidad más compleja, use el proceso normal de [escritura de tareas](../msbuild/task-writing.md) de MSBuild.

   Si no todas las entradas y salidas de la herramienta aparecen en la línea de comandos de la herramienta, como en los `CL` `MIDL` casos, y `RC` , y si desea realizar el seguimiento automático de archivos de entrada y salida y la creación del archivo. registro de transacciones, derive su tarea de la `Microsoft.Build.CPPTasks.TrackedVCToolTask` clase. En la actualidad, aunque hay documentación para la clase base [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) , no hay ningún ejemplo o documentación para los detalles de la `TrackedVCToolTask` clase. Si esto es de especial interés, agregue su voz a una solicitud en la [comunidad de desarrolladores](https://aka.ms/feedback/suggest?space=62).

## <a name="incremental-builds-and-up-to-date-checks"></a>Compilaciones incrementales y comprobaciones actualizadas

Los destinos de compilación incremental de MSBuild predeterminados usan `Inputs` `Outputs` atributos y. Si los especifica, MSBuild llama al destino solo si alguna de las entradas tiene una marca de tiempo más reciente que todas las salidas. Dado que los archivos de origen suelen incluir o importar otros archivos, y las herramientas de compilación generan resultados diferentes en función de las opciones de la herramienta, es difícil especificar todas las entradas y salidas posibles en los destinos de MSBuild.

Para administrar este problema, la compilación de C++ utiliza una técnica diferente para admitir compilaciones incrementales. La mayoría de los destinos no especifican entradas y salidas, y como resultado, siempre se ejecutan durante la compilación. Las tareas llamadas por los destinos escriben información sobre todas las entradas y salidas en archivos de *transacciones de transacciones* que tienen una extensión. registration. Las compilaciones posteriores usan los archivos. registro de transacciones para comprobar lo que ha cambiado y es necesario volver a generar y lo que está actualizado. Los archivos. registro de transacciones son también el único origen de la comprobación predeterminada de la compilación actualizada en el IDE.

Para determinar todas las entradas y salidas, las tareas de herramientas nativas usan tracker.exe y la clase [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) proporcionada por MSBuild.

Microsoft.Build.CPPTasks.Common.dll define la `TrackedVCToolTask` clase base abstracta pública. La mayoría de las tareas de herramientas nativas se derivan de esta clase.

A partir de Visual Studio 2017 Update 15,8, puede usar la `GetOutOfDateItems` tarea implementada en Microsoft.Cpp.Common.Tasks.dll para generar archivos. registration para destinos personalizados con entradas y salidas conocidas.
Como alternativa, puede crearlos mediante la `WriteLinesToFile` tarea. Vea el `_WriteMasmTlogs` destino en `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets* como ejemplo.

## <a name="tlog-files"></a>archivos. el archivo de transacciones

Hay tres tipos de archivos. el archivo de transacciones: *lectura*, *escritura* y *línea de comandos*. Los archivos de lectura y escritura. el registro de transacciones se usan en las compilaciones incrementales y en la comprobación actualizada en el IDE. Los archivos de línea de comandos. el archivo de transacciones solo se usan en compilaciones incrementales.

MSBuild proporciona estas clases auxiliares para leer y escribir archivos. el archivo de transacciones:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

La clase [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) se puede usar para tener acceso a los archivos de lectura y escritura. el archivo de transacciones, e identificar las entradas que son más recientes que las salidas, o si falta una salida. Se usa en la comprobación de actualización.

Los archivos. de la línea de comandos contienen información sobre las líneas de comandos que se usan en la compilación. Solo se usan para compilaciones incrementales, no para comprobaciones actualizadas, por lo que el formato interno viene determinado por la tarea de MSBuild que los genera.

### <a name="read-tlog-format"></a>Formato de lectura. el modo de transacciones

*Leer* archivos. el archivo de transacciones ( \* . Read. \* . el archivo de transacciones) contienen información sobre los archivos de origen y sus dependencias.

Un símbolo de intercalación ( **^** ) al principio de una línea indica uno o más orígenes. Los orígenes que comparten las mismas dependencias se separan mediante una barra vertical ( **\|** ).

Los archivos de dependencia se enumeran después de los orígenes, cada uno en su propia línea. Todos los nombres de archivo son rutas de acceso completas.

Por ejemplo, suponga que los orígenes del proyecto se encuentran en *F: \\ Test \\ ConsoleApplication1 \\ ConsoleApplication1*. Si el archivo de código fuente, *Class1. cpp*, incluye,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

después, el archivo *cl. Read. 1.* el archivo de transacciones contiene el archivo de código fuente seguido de sus dos dependencias:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

No es necesario escribir los nombres de archivo en mayúsculas, pero es una comodidad para algunas herramientas.

### <a name="write-tlog-format"></a>Write. el formato de transacciones

*Write* . el valor de transacciones ( \* . Write. \* . el archivo de transacciones) Conecte los orígenes y las salidas.

Un símbolo de intercalación ( **^** ) al principio de una línea indica uno o más orígenes. Varios orígenes se separan mediante una barra vertical ( **\|** ).

Los archivos de salida generados a partir de los orígenes deben aparecer después de los orígenes, cada uno en su propia línea. Todos los nombres de archivo deben ser rutas de acceso completas.

Por ejemplo, para un proyecto de definimos simple que tenga un archivo de origen adicional *Class1. cpp*, el archivo *Link. Write. 1.* el archivo de transacciones puede contener:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Compilación en tiempo de diseño

En el IDE, los proyectos. vcxproj usan un conjunto de destinos de MSBuild para obtener información adicional del proyecto y volver a generar los archivos de salida. Algunos de estos destinos solo se usan en compilaciones en tiempo de diseño, pero muchos de ellos se usan en compilaciones regulares y compilaciones en tiempo de diseño.

Para obtener información general sobre las compilaciones en tiempo de diseño, vea la documentación de CPS para [compilaciones en tiempo de diseño](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Esta documentación solo se aplica en parte a proyectos de Visual C++.

Los `CompileDesignTime` `Compile` destinos y mencionados en la documentación de las compilaciones en tiempo de diseño nunca se ejecutan para proyectos. vcxproj. Visual C++ los proyectos. vcxproj usan distintos destinos en tiempo de diseño para obtener información de IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Destinos en tiempo de diseño para la información de IntelliSense

Los destinos en tiempo de diseño utilizados en proyectos. vcxproj se definen en `$(VCTargetsPath)` \\ *Microsoft. cpp. DesignTime. targets*.

El `GetClCommandLines` destino recopila las opciones del compilador para IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – destinos solo en tiempo de diseño, necesarios para la inicialización de compilación en tiempo de diseño. Entre otras cosas, estos destinos deshabilitan parte de la funcionalidad de compilación normal para mejorar el rendimiento.

- `ComputeCompileInputsTargets` : un conjunto de destinos que modifica opciones y elementos del compilador. Estos destinos se ejecutan en las compilaciones regulares y en tiempo de diseño.

El destino llama a la `CLCommandLine` tarea para crear la línea de comandos que se va a usar para IntelliSense. De nuevo, a pesar de su nombre, no solo puede controlar las opciones de CL, sino también las opciones Clang y GCC. La propiedad controla el tipo de los modificadores del compilador `ClangMode` .

Actualmente, la línea de comandos generada por la `CLCommandLine` tarea siempre utiliza los modificadores de cl (incluso en modo Clang) porque son más fáciles de analizar para el motor de IntelliSense.

Si va a agregar un destino que se ejecuta antes de la compilación, ya sea normal o en tiempo de diseño, asegúrese de que no interrumpa las compilaciones en tiempo de diseño ni afecte al rendimiento. La manera más sencilla de probar el destino es abrir un símbolo del sistema para desarrolladores y ejecutar este comando:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Este comando genera un registro de compilación detallado, *MSBuild. log*, que tiene un resumen de rendimiento para los destinos y las tareas al final.

Asegúrese de usar `Condition ="'$(DesignTimeBuild)' != 'true'"` en todas las operaciones que solo tienen sentido para las compilaciones normales y no para las compilaciones en tiempo de diseño.

### <a name="design-time-targets-that-generate-sources"></a>Destinos en tiempo de diseño que generan orígenes

*Esta característica está deshabilitada de forma predeterminada para los proyectos nativos de escritorio y no se admite actualmente en proyectos almacenados en caché*.

Si `GeneratorTarget` se definen metadatos para un elemento de proyecto, el destino se ejecuta automáticamente cuando se carga el proyecto y cuando se cambia el archivo de código fuente.

::: moniker range="vs-2017"

Por ejemplo, para generar automáticamente archivos. cpp o. h a partir de archivos. XAML, los `$(VSInstallDir)` \\ archivos *msbuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 15.0* \\ \* \\ *Microsoft. Windows. UI. Xaml. cpp. targets* definen estas entidades:

::: moniker-end

::: moniker range=">=vs-2019"

Por ejemplo, para generar automáticamente archivos. cpp o. h a partir de archivos. XAML, los `$(VSInstallDir)` \\ archivos *msbuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 16,0* \\ \* \\ *Microsoft. Windows. UI. Xaml. cpp. targets* definen estas entidades:

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

Para usar `Task.HostObject` para obtener el contenido no guardado de los archivos de código fuente, los destinos y las tareas deben registrarse como [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) para los proyectos especificados en un archivo pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ la extensibilidad del proyecto en el IDE de Visual Studio

El sistema de proyectos de Visual C++ se basa en el [sistema de proyectos de vs](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)y utiliza sus puntos de extensibilidad. Sin embargo, la implementación de la jerarquía del proyecto es específica de Visual C++ y no basada en CPS, por lo que la extensibilidad de la jerarquía se limita a los elementos del proyecto.

### <a name="project-property-pages"></a>Páginas de propiedades del proyecto

Para obtener información general sobre el diseño, vea [compatibilidad con múltiples versiones de .NET Framework para proyectos de VC + +](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

En términos sencillos, las páginas de propiedades que se ven en el cuadro de diálogo de **propiedades del proyecto** para un proyecto de C++ se definen mediante archivos de *reglas* . Un archivo de reglas especifica un conjunto de propiedades para mostrar en una página de propiedades y cómo y dónde se deben guardar en el archivo de proyecto. Los archivos de reglas son archivos. XML que usan el formato XAML. Los tipos que se usan para serializarlos se describen en [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Para obtener más información sobre el uso de archivos de reglas en proyectos, vea [archivos de reglas XML de página de propiedades](/cpp/build/reference/property-page-xml-files).

Los archivos de reglas se deben agregar al `PropertyPageSchema` grupo de elementos:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` la visibilidad de la regla de límites de metadatos, que también se controla mediante el tipo de regla, y puede tener uno de estos valores:

`Project` | `File` | `PropertySheet`

CPS admite otros valores para el tipo de contexto, pero no se usan en proyectos de Visual C++.

Si la regla debe estar visible en más de un contexto, use punto y coma (**;**) para separar los valores de contexto, como se muestra aquí:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Formato de regla y tipos principales

El formato de la regla es sencillo, por lo que en esta sección solo se describen los atributos que afectan a la apariencia de la regla en la interfaz de usuario.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

El `PageTemplate` atributo define cómo se muestra la regla en el cuadro de diálogo **páginas de propiedades** . El atributo puede tener uno de estos valores:

| Atributo | Descripción |
|------------| - |
| `generic` | Todas las propiedades se muestran en una página en encabezados de categoría.<br/>La regla puede ser visible para `Project` los `PropertySheet` contextos y, pero no para `File` .<br/><br/> Ejemplo: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Las categorías se muestran como subpáginas.<br/>La regla puede ser visible en todos los contextos `Project` : `PropertySheet` y `File` .<br/>La regla solo está visible en las propiedades del proyecto si el proyecto tiene elementos con el `ItemType` definido en `Rule.DataSource` , a menos que el nombre de la regla esté incluido en el `ProjectTools` grupo de elementos.<br/><br/>Ejemplo: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | La página se muestra como parte de la página de depuración.<br/>Las categorías se omiten actualmente.<br/>El nombre de la regla debe coincidir con el atributo del objeto MEF del iniciador de depuración `ExportDebugger` .<br/><br/>Ejemplo: `$(VCTargetsPath)` \\ *1033* \\ *\_ \_windows.xmllocal del depurador* |
| *personal* | Plantilla personalizada. El nombre de la plantilla debe coincidir con el `ExportPropertyPageUIFactoryProvider` atributo del `PropertyPageUIFactoryProvider` objeto MEF. Vea **Microsoft. VisualStudio. Project System. Designers. properties. IPropertyPageUIFactoryProvider**.<br/><br/> Ejemplo: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Si la regla usa una de las plantillas basadas en cuadrícula de propiedades, puede usar estos puntos de extensibilidad para sus propiedades:

- [Editores de valores de propiedad](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Proveedor de valores de enumeración dinámica](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Extender una regla

Si desea usar una regla existente, pero necesita agregar o quitar (es decir, ocultar) unas pocas propiedades, puede crear una [regla de extensión](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Invalidar una regla

Quizás desee que el conjunto de herramientas Use la mayoría de las reglas predeterminadas del proyecto, pero para reemplazar solo una o algunas de ellas. Por ejemplo, suponga que solo desea cambiar la regla de C/C++ para mostrar distintos modificadores de compilador. Puede proporcionar una nueva regla con el mismo nombre y el mismo nombre para mostrar que la regla existente, e incluirla en el `PropertyPageSchema` grupo de elementos después de la importación de destinos de CPP predeterminados. En el proyecto solo se usa una regla con un nombre determinado y el último que se incluye en el `PropertyPageSchema` grupo de elementos gana.

#### <a name="project-items"></a>elementos de proyecto

El archivo *ProjectItemsSchema.xml* define los `ContentType` `ItemType` valores y para los elementos que se tratan como elementos de proyecto y define los `FileExtension` elementos para determinar a qué grupo de elementos se agrega un nuevo archivo.

El archivo ProjectItemsSchema predeterminado se encuentra en `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Para ampliarla, debe crear un archivo de esquema con un nombre nuevo, como *MyProjectItemsSchema.xml*:

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

Después, en el archivo de destinos, agregue:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Ejemplo: `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Depuradores

El servicio de depuración de Visual Studio admite la extensibilidad para el motor de depuración. Para obtener más información, consulte estos ejemplos:

- [MIEngine, proyecto de código abierto que admite la depuración lldb](https://github.com/Microsoft/MIEngine)

- [Ejemplo de motor de depuración de Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Para especificar los motores de depuración y otras propiedades para la sesión de depuración, debe implementar un componente MEF del [iniciador de depuración](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) y agregar una `debugger` regla. Para obtener un ejemplo, vea el `$(VCTargetsPath)` \\ \\ \_ archivowindows.xml local del depurador de 1033 \_ .

### <a name="deploy"></a>Implementación

los proyectos. vcxproj usan la extensibilidad del sistema de proyectos de Visual Studio para [implementar proveedores](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Compilar comprobación actualizada

De forma predeterminada, la comprobación de compilación actualizada requiere que los archivos Read. registration y Write. registration se creen en la `$(TlogLocation)` carpeta durante la compilación para todas las entradas y salidas de compilación.

Para usar una comprobación de actualización personalizada:

1. Deshabilite la comprobación de actualización predeterminada agregando la `NoVCDefaultBuildUpToDateCheckProvider` funcionalidad en el archivo *Toolset. targets* :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implemente su propio [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Actualización de proyecto

### <a name="default-vcxproj-project-upgrader"></a>Actualizador de proyecto. vcxproj predeterminado

El actualizador de proyecto. vcxproj predeterminado cambia la `PlatformToolset` `ApplicationTypeRevision` versión del conjunto de herramientas de MSBuild y .NET Framework. Los dos últimos se cambian siempre a los valores predeterminados de la versión de Visual Studio, pero `PlatformToolset` y `ApplicationTypeRevision` se pueden controlar mediante propiedades especiales de MSBuild.

El actualizador utiliza estos criterios para decidir si un proyecto se puede actualizar o no:

1. En el caso de los proyectos que definen `ApplicationType` y `ApplicationTypeRevision` , hay una carpeta con un número de revisión mayor que el actual.

1. La propiedad `_UpgradePlatformToolsetFor_<safe_toolset_name>` se define para el conjunto de herramientas actual y su valor no es igual que el conjunto de herramientas actual.

   En estos nombres de propiedad, *\<safe_toolset_name>* representa el nombre del conjunto de herramientas con todos los caracteres no alfanuméricos reemplazados por un carácter de subrayado ( **\_** ).

Cuando un proyecto se puede actualizar, participa en la *redestinación* de la solución. Para obtener más información, vea [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Si desea adornar los nombres de proyecto en **Explorador de soluciones** cuando los proyectos usan un conjunto de herramientas concreto, defina una `_PlatformToolsetShortNameFor_<safe_toolset_name>` propiedad.

Para obtener ejemplos `_UpgradePlatformToolsetFor_<safe_toolset_name>` de `_PlatformToolsetShortNameFor_<safe_toolset_name>` definiciones de propiedades y, vea el archivo *Microsoft. cpp. default. props* . Para obtener ejemplos de uso, vea el `$(VCTargetPath)` \\ archivo *Microsoft. cpp. Platform. targets* .

### <a name="custom-project-upgrader"></a>Actualizador de proyecto personalizado

Para usar un objeto de actualizador de proyecto personalizado, implemente un componente MEF, como se muestra aquí:

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

El código puede importar y llamar al objeto actualizador. vcxproj predeterminado:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` se define en *Microsoft.VisualStudio.ProjectSystem.VS.dll* y es similar a `IVsRetargetProjectAsync` .

Defina la `VCProjectUpgraderObjectName` propiedad para indicar al sistema del proyecto que use el objeto actualizador personalizado:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Deshabilitar la actualización del proyecto

Para deshabilitar las actualizaciones de proyectos, use un `NoUpgrade` valor:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Extensibilidad y caché del proyecto

Para mejorar el rendimiento cuando se trabaja con soluciones de C++ de gran tamaño en Visual Studio 2017, se presentó la [memoria caché del proyecto](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) . Se implementa como una base de datos de SQLite rellenada con los datos del proyecto y, a continuación, se usa para cargar proyectos sin cargar proyectos de MSBuild o CPS en la memoria.

Dado que no hay objetos CPS presentes para los proyectos. vcxproj cargados desde la memoria caché, los componentes de MEF de la extensión que se importan `UnconfiguredProject` o `ConfiguredProject` no se pueden crear. Para admitir la extensibilidad, la caché del proyecto no se usa cuando Visual Studio detecta si un proyecto usa (o es probable que use) extensiones de MEF.

Estos tipos de proyecto siempre se cargan por completo y tienen objetos CPS en memoria, por lo que se crean todas las extensiones MEF para ellos:

- Proyectos de inicio

- Proyectos que tienen un actualizador de proyecto personalizado, es decir, definen una `VCProjectUpgraderObjectName` propiedad

- Proyectos que no tienen como destino ventanas de escritorio, es decir, definen una `ApplicationType` propiedad

- Proyectos de elementos compartidos (. vcxitems) y cualquier proyecto que haga referencia a ellos mediante la importación de proyectos de. vcxitems.

Si no se detecta ninguna de estas condiciones, se crea una caché del proyecto. La memoria caché incluye todos los datos del proyecto de MSBuild necesarios para responder a `get` las consultas en las `VCProjectEngine` interfaces. Esto significa que todas las modificaciones en el nivel de archivo de los destinos y propiedades de MSBuild realizadas por una extensión solo deben funcionar en los proyectos cargados desde la memoria caché.

## <a name="shipping-your-extension"></a>Envío de la extensión

Para obtener información sobre cómo crear archivos VSIX, vea [envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Para obtener información sobre cómo agregar archivos a ubicaciones de instalación especiales, por ejemplo, para agregar archivos en `$(VCTargetsPath)` , consulte [instalación fuera de la carpeta extensiones](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Recursos adicionales

El sistema de compilación de Microsoft ([msbuild](../msbuild/msbuild.md)) proporciona el motor de compilación y el formato basado en XML extensible para los archivos de proyecto. Debe estar familiarizado con los [conceptos](../msbuild/msbuild-concepts.md) básicos de MSBuild y con cómo funciona [MSBuild para Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) con el fin de extender el sistema de proyectos de Visual C++.

El Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) proporciona las API de extensión que se usan en CPS y en el sistema de proyectos de Visual C++. Para obtener información general sobre cómo se usa MEF en CPS, consulte [CPS y MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) en la [información general de VSProjectSystem de MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Puede personalizar el sistema de compilación existente para agregar pasos de compilación o nuevos tipos de archivo. Para obtener más información, vea [información general sobre MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) y [trabajar con propiedades del proyecto](/cpp/build/working-with-project-properties).
