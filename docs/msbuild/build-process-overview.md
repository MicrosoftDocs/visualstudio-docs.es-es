---
title: Cómo MSBuild compila proyectos
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65e386b71c0b7ece3aee8185574d53955b7326a1
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136867"
---
# <a name="how-msbuild-builds-projects"></a>Cómo MSBuild compila proyectos

¿Cómo funciona MSBuild realmente? En este artículo, aprenderá cómo MSBuild procesa los archivos del proyecto, independientemente de que se invoquen desde Visual Studio o desde una línea de comandos o un script. Saber cómo funciona MSBuild puede ayudarlo a diagnosticar mejor los problemas y a personalizar de forma más eficaz el proceso de compilación. En este artículo se describe el proceso de compilación y, en gran medida, se aplica a todos los tipos de proyecto.

El proceso de compilación completo consta de las fases de [inicio](#startup), [evaluación](#evaluation-phase) y [ejecución](#execution-phase) de los destinos y las tareas que compilan el proyecto. Además de estas entradas, las importaciones externas definen los detalles del proceso de compilación, incluidas las [importaciones estándar](#standard-imports), como *Microsoft.Common.targets* y [user-configurable imports](#user-configurable-imports), en el nivel de solución o proyecto.

## <a name="startup"></a>Inicio

MSBuild se puede invocar desde Visual Studio a través del modelo de objetos de MSBuild en *Microsoft. Build.dll* . También se puede hacer invocando el archivo ejecutable directamente en la línea de comandos o en un script, como en los sistemas de CI. En cualquier caso, las entradas que afectan al proceso de compilación incluyen el archivo de proyecto (o el objeto de proyecto interno de Visual Studio), posiblemente un archivo de solución, variables de entorno y modificadores de la línea de comandos o sus equivalentes del modelo de objetos. Durante la fase de inicio, las opciones de la línea de comandos o los equivalentes del modelo de objetos se usan para configurar las opciones de MSBuild; por ejemplo, los registradores. Las propiedades establecidas en la línea de comandos mediante el modificador `-property` o `-p` se establecen como propiedades globales, que invalidan cualquier valor que se establezca en los archivos del proyecto, aunque los archivos de proyecto se lean más adelante.

Las secciones siguientes tratan sobre los archivos de entrada, como los de solución o los de proyecto.

### <a name="solutions-and-projects"></a>Soluciones y proyectos

Las instancias de MSBuild pueden constar de un proyecto o de muchos como parte de una solución. El archivo de solución no es un archivo XML de MSBuild, pero MSBuild lo interpreta para que reconozca todos los proyectos que son necesarios para que se compilen para la configuración y la plataforma especificadas. Cuando MSBuild procesa esta entrada XML, se hace referencia a ella como la compilación de la solución. Tiene algunos puntos extensibles que permiten ejecutar algo en cada compilación de la solución. Sin embargo, como esta compilación es una ejecución independiente de las compilaciones de proyecto individuales, no hay opciones de propiedades ni definiciones de destino de la compilación de la solución que sean pertinentes para cada compilación de proyecto.

Puede averiguar cómo extender la compilación de la solución en [Personalizar una compilación](customize-your-build.md#customize-the-solution-build).

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Diferencias entre compilaciones de Visual Studio y de MSBuild.exe

Hay algunas diferencias importantes entre el momento en que se compilan los proyectos en Visual Studio y en que se invoca MSBuild directamente, ya sea a través del ejecutable de MSBuild o al utilizar el modelo de objetos de MSBuild para iniciar una compilación. Visual Studio administra el orden de compilación del proyecto para las compilaciones de Visual Studio; solo llama a MSBuild en el nivel de proyecto individual y, cuando lo hace, se establecen un par de propiedades booleanas (`BuildingInsideVisualStudio` y `BuildProjectReferences`) que afectan significativamente al trabajo de MSBuild. Dentro de cada proyecto, la ejecución se realiza de la misma forma que cuando se invoca a través de MSBuild, pero la diferencia radica en los proyectos a los que se hace referencia. En MSBuild, cuando se necesitan proyectos a los que hacer referencia, se crea realmente una compilación; es decir, ejecuta tareas y herramientas y genera la salida. Cuando una compilación de Visual Studio encuentra un proyecto al que se hace referencia, MSBuild solo devuelve las salidas esperadas del proyecto al que se hace referencia; permite que Visual Studio controle la compilación de los demás proyectos. Visual Studio determina el orden de compilación y llama a MSBuild por separado (según sea necesario), todo ello bajo el control de Visual Studio.

Otra diferencia se produce cuando se invoca MSBuild con un archivo de solución: MSBuild analiza el archivo de solución, crea un archivo de entrada XML estándar, lo evalúa y lo ejecuta como un proyecto. La compilación de la solución se ejecuta antes que cualquier proyecto. Al realizar la compilación desde Visual Studio, no sucede nada de esto. MSBuild nunca "ve" el archivo de solución. Como consecuencia, la personalización de la compilación de la solución (con *before.SolutionName.sln.targets* y *after.SolutionName.sln.targets* ) solo se aplica a MSBuild.exe o a las compilaciones basadas en el modelo de objetos, pero no a las de Visual Studio.

### <a name="project-sdks"></a>SDK de proyecto

La característica de SDK para los archivos de proyecto de MSBuild es relativamente nueva. Antes de este cambio, los archivos de proyecto importaban explícitamente los archivos *.targets* y *.props* que definían el proceso de compilación para un tipo de proyecto determinado.

Los proyectos de .NET Core importan la versión del SDK de .NET adecuada. Vea el artículo de información general, [SDK de proyectos de .NET Core](/dotnet/core/project-sdk/overview), y la referencia a las [propiedades](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Fase de evaluación

En esta sección se describe cómo se procesan y analizan estos archivos de entrada para generar objetos en memoria que determinan lo que se va a compilar.

El propósito de la fase de evaluación es crear las estructuras de objeto en memoria en función de los archivos XML de entrada y el entorno local. La fase de evaluación consta de seis pasos que procesan los archivos de entrada, como los archivos XML del proyecto y los archivos XML importados, normalmente denominados *.props* o *.targets* , en función de si principalmente establecen propiedades o definen destinos de compilación. Cada paso genera una parte de los objetos en memoria que se usan posteriormente en la fase de ejecución para compilar los proyectos, pero no se realizan acciones de compilación reales durante la fase de evaluación. En cada paso, los elementos se procesan en el orden en que aparecen.

Los pasos de la fase de evaluación son los siguientes:

- Evaluar variables de entorno
- Evaluar importaciones y propiedades
- Evaluar definiciones de elementos
- Evaluar elementos
- Evaluar elementos [UsingTask](usingtask-element-msbuild.md)
- Evaluar destinos

El orden de estos pasos tiene implicaciones significativas, y es importante saber cuándo personalizar el archivo del proyecto. Consulte la sección [Orden de evaluación de propiedades y elementos](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Evaluar variables de entorno

En esta fase, las variables de entorno se usan para establecer propiedades equivalentes. Por ejemplo, la variable de entorno PATH está disponible como propiedad `$(PATH)`. Cuando se ejecuta desde la línea de comandos o un script, el entorno de comandos se usa de la forma habitual y, cuando se ejecuta desde Visual Studio, se utiliza el entorno activo cuando se inicia Visual Studio.

### <a name="evaluate-imports-and-properties"></a>Evaluar importaciones y propiedades

En esta fase, se lee el código XML de entrada completo, incluidos los archivos de proyecto y la cadena completa de importaciones. MSBuild crea una estructura XML en memoria que representa el archivo XML del proyecto y todos los archivos importados. En este momento, se evalúan y establecen las propiedades que no están en los destinos.

Como consecuencia de que MSBuild lea todos los archivos de entrada XML en un momento anterior de su proceso, los cambios en esas entradas durante el proceso de compilación no afectan a la compilación actual.

Las propiedades fuera de cualquier destino se administran de forma diferente a las propiedades de los destinos. En esta fase, solo se evalúan las propiedades definidas fuera de cualquier destino.

Dado que las propiedades se procesan en orden en el paso de las propiedades, una propiedad en cualquier punto de la entrada puede acceder a los valores de propiedad que se mostraban anteriormente en la entrada, pero no a las propiedades que aparecen más adelante.

Dado que las propiedades se procesan antes de que se evalúen los elementos, no se puede tener acceso al valor de ningún elemento durante ninguna parte del paso de propiedades. 

### <a name="evaluate-item-definitions"></a>Evaluar definiciones de elementos

En esta fase, se interpretan las [definiciones de elementos](item-definitions.md) y se crea una representación en memoria de esas definiciones.

### <a name="evaluate-items"></a>Evaluar elementos

Los elementos definidos dentro de un destino se administran de forma diferente a aquellos que están fuera de cualquier destino. En esta fase, se procesan los elementos fuera de cualquier destino y sus metadatos asociados.  Los metadatos establecidos por definiciones de elementos se reemplazan por el valor de metadatos en los elementos. Dado que los elementos se procesan en el orden en que aparecen, puede hacer referencia a los que se definieron anteriormente, pero no a los que aparecen más adelante. Y como el paso de elementos va después del paso de propiedades, los elementos pueden acceder a cualquier propiedad si se definen fuera de los destinos, independientemente de si la definición de propiedad aparece más adelante.

### <a name="evaluate-usingtask-elements"></a>Evaluar elementos `UsingTask`

En esta fase, se leen elementos [UsingTask](usingtask-element-msbuild.md) y las tareas se declaran para su uso posterior durante la fase de ejecución.

### <a name="evaluate-targets"></a>Evaluar destinos

En esta fase, todas las estructuras de objetos de destino se crean en memoria, como preparación para la ejecución. No se produce ninguna ejecución real. 

## <a name="execution-phase"></a>Fase de ejecución

En la fase de ejecución, los destinos se ordenan y ejecutan, y todas las tareas se ejecutan. Pero primero, las propiedades y los elementos que se definen dentro de los destinos se evalúan conjuntamente en el orden en que aparecen. El orden de procesamiento es especialmente diferente del modo en que se procesan las propiedades y los elementos que no están en un destino: todas las propiedades primero y, a continuación, todos los elementos, en pasos independientes. Los cambios en las propiedades y los elementos dentro de un destino se pueden observar después del destino en el que se cambiaron.

### <a name="target-build-order"></a>Orden de compilación de destinos

En un único proyecto, los destinos se ejecutan en serie. El principal problema es cómo determinar en qué orden se debe compilar todo con el fin de que las dependencias se usen para compilar los destinos en el orden correcto.  

El orden de compilación de los destinos viene determinado por el uso de los atributos `BeforeTargets`, `DependsOnTargets` y `AfterTargets` en cada destino. El orden de los destinos posteriores puede verse afectado durante la ejecución de un destino anterior si este modifica una propiedad a la que se hace referencia en estos atributos.

Las reglas de ordenación se describen en [Determinación del orden de compilación de destino](target-build-order.md#determine-the-target-build-order). El proceso viene determinado por una estructura de pila que contiene los destinos que se van a compilar. El destino de la parte superior de esta tarea inicia la ejecución y, si depende de cualquier otro, los destinos se insertan en la parte superior de la pila y se inicia la ejecución.  Cuando hay un destino sin dependencias, se ejecuta hasta su finalización y se reanuda su destino primario.

### <a name="project-references"></a>Referencias del proyecto

Hay dos rutas de código que MSBuild puede realizar, la normal, que se describe aquí, y la opción de grafo que se describe en la sección siguiente.

Los proyectos individuales especifican su dependencia de otros proyectos a través de elementos `ProjectReference`. Cuando se empieza a compilar un proyecto en la parte superior de la pila, alcanza el punto en el que se ejecuta el destino `ResolveProjectReferences`, un destino estándar definido en los archivos de destino comunes.

`ResolveProjectReferences` invoca la tarea de MSBuild con entradas de los elementos `ProjectReference` para obtener las salidas. Los elementos `ProjectReference` se transforman en elementos locales, como `Reference`. La fase de ejecución de MSBuild para el proyecto actual se pausa mientras la fase de ejecución comienza a procesar el proyecto al que se hace referencia (la fase de evaluación se realiza primero según sea necesario). El proyecto al que se hace referencia solo se compila después de empezar a compilar el proyecto dependiente, por lo que se crea un árbol de compilación de proyectos.

Visual Studio permite crear dependencias del proyecto en archivos de solución (.sln). Las dependencias se especifican en el archivo de solución y solo se respetan al compilar una solución, o al compilarse en Visual Studio. Si compila un solo proyecto, se omite este tipo de dependencia. MSBuild transforma las referencias de soluciones en elementos `ProjectReference` y, a partir de ese momento, se tratan de la misma manera.

### <a name="graph-option"></a>Opción de grafo

Si especifica el modificador de compilación del grafo (`-graphBuild` o `-graph`), `ProjectReference` se convierte en un concepto de primera clase que usa MSBuild. MSBuild analizará todos los proyectos y creará el grafo de orden de compilación, un grafo de dependencias real de proyectos, que se recorre a continuación para determinar el orden de compilación. Al igual que con los destinos de proyectos individuales, MSBuild se asegura de que los proyectos a los que se hace referencia se compilen después de los proyectos de los que dependen.

## <a name="parallel-execution"></a>Ejecución en paralelo

Al usar la compatibilidad multiprocesador (modificadores `-maxCpuCount` o `-m`), MSBuild creará nodos, que son procesos de MSBuild que usan los núcleos de CPU disponibles. Cada proyecto se envía a un nodo disponible. Dentro de un nodo, las compilaciones de proyecto individuales se ejecutan en serie.

Es posible que las tareas estén habilitadas para la ejecución en paralelo mediante el establecimiento de una variable booleana <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>, que se establece según el valor de la propiedad `$(BuildInParallel)` en MSBuild. En el caso de las tareas que están habilitadas para la ejecución en paralelo, un programador de trabajo administra los nodos y asigna trabajo a los nodos.

Consulte [Compilación de varios proyectos en paralelo con MSBuild](building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="standard-imports"></a>Importaciones estándar

Los archivos de proyecto de .NET importan *Microsoft.Common.props* y *Microsoft.Common.targets* , explícita o implícitamente en proyectos de estilo SDK, y se pueden encontrar en la carpeta *MSBuild\Current\bin* de una instalación de Visual Studio. Los proyectos de C++ tienen su propia jerarquía de importaciones. Consulte [Parámetros internos de MSBuild para proyectos de C++](/cpp/build/reference/msbuild-visual-cpp-overview).

El archivo *Microsoft.Common.props* establece valores predeterminados que pueden invalidarse. Se importa (explícita o implícitamente) al principio de un archivo de proyecto. Así, la configuración del proyecto aparece después de los valores predeterminados, de modo que se invalidan.

Los archivos *Microsoft.Common.targets* y los archivos de destino que se importan definen el proceso de compilación estándar para los proyectos de .NET. También se proporcionan puntos de extensión que puede usar para personalizar la compilación.

En la implementación, *Microsoft.Common.targets* es un contenedor fino que importa *Microsoft.Common.CurrentVersion.targets* . Este archivo contiene la configuración de las propiedades estándar y define los destinos reales que definen el proceso de compilación. El destino `Build` se define aquí, pero en realidad está vacío. Sin embargo, el destino `Build` contiene el atributo `DependsOn` que especifica los destinos individuales que componen los pasos de compilación reales, que son `BeforeBuild`, `CoreBuild` y `AfterBuild`. El destino `Build` se define de la manera siguiente:

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild` y `AfterBuild` son puntos de extensión. Están vacíos en el archivo *Microsoft.Common.CurrentVersion.targets* , pero los proyectos pueden proporcionar sus propios destinos `BeforeBuild` y `AfterBuild` con las tareas que deben realizarse antes o después del proceso de compilación principal. `AfterBuild` se ejecuta antes que el destino no operativo, `Build`, porque `AfterBuild` aparece en el atributo `DependsOn` del destino `Build`, pero se realiza después de `CoreBuild`.

El destino `CoreBuild` contiene las llamadas a las herramientas de compilación, como se indica a continuación:

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

En la tabla siguiente se describen estos destinos: algunos destinos solo se pueden aplicar a determinados tipos de proyecto.

| Destino | Descripción |
|--------|-------------|
| BuildOnlySettings | Configuración solo para compilaciones reales, no para cuando se invoca MSBuild en la carga del proyecto mediante Visual Studio. |
| PrepareForBuild | Prepara los requisitos previos para la compilación. |
| PreBuildEvent | Punto de extensión de los proyectos para definir las tareas que se van a ejecutar antes de la compilación. |
| ResolveProjectReferences | Analiza las dependencias del proyecto y compila proyectos a los que se hace referencia. |
| ResolveAssemblyReferences| Encuentra los ensamblados a los que se hace referencia. |
| ResolveReferences | Consta de `ResolveProjectReferences` y `ResolveAssemblyReferences` para buscar todas las dependencias. |
| PrepareResources | Procesa archivos de recursos. |
| ResolveKeySource| Resuelve la clave de nombre seguro utilizada para firmar el ensamblado y el certificado usado para firmar los manifiestos [ClickOnce](../deployment/clickonce-security-and-deployment.md). |
| Compile | Invoca el compilador. |
| ExportWindowsMDFile | Genera un archivo [WinMD](/uwp/winrt-cref/winmd-files) a partir de los archivos WinMDModule generados por el compilador. |
| UnmanagedUnregistration | Quita o limpia las entradas del registro de [interoperabilidad COM](/dotnet/standard/native-interop/cominterop) de una compilación anterior. |
| GenerateSerializationAssemblies | Genera un ensamblado de serialización XML mediante [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Crea un ensamblado satélite para cada referencia cultural única en los recursos. |
| Generate Manifests | Genera manifiestos de aplicación y de implementación [ClickOnce](../deployment/clickonce-security-and-deployment.md) o un manifiesto nativo. |
| GetTargetPath | Devuelve un elemento que contiene el producto de compilación (ejecutable o ensamblado) de este proyecto, con metadatos. |
| PrepareForRun | Copia las salidas de la compilación en el directorio final si han cambiado. |
| UnmanagedRegistration | Establece entradas del registro para la [interoperabilidad COM](/dotnet/standard/native-interop/cominterop). |
| IncrementalClean | Quita archivos que se generaron en una compilación anterior, pero que no se generaron en la compilación actual. Esto es necesario para que `Clean` funcione en compilaciones incrementales. |
| PostBuildEvent | Punto de extensión de los proyectos para definir las tareas que se van a ejecutar después de la compilación. |

Muchos de los destinos de la tabla anterior se encuentran en importaciones específicas de lenguajes, como *Microsoft.CSharp.targets* . Este archivo define los pasos en el proceso de compilación estándar específico para proyectos de C# .NET. Por ejemplo, contiene el destino `Compile` que realmente llama al compilador de C#.

## <a name="user-configurable-imports"></a>Importaciones configurables por el usuario

Además de las importaciones estándar, hay varias importaciones que se pueden agregar para personalizar el proceso de compilación.

- *Directory.Build.props*
- *Directory.Build.targets*

Las importaciones estándar leen estos archivos para cualquier proyecto que se encuentre un nivel por debajo. Por lo general, en el nivel de solución de la configuración para controlar todos los proyectos de la solución, pero también podría estar en niveles superiores del sistema de archivos, hasta la raíz de la unidad.

*Microsoft.Common.props* importa el archivo *Directory.Build.props* , por lo que las propiedades definidas ahí están disponibles en el archivo del proyecto. Se pueden redefinir en el archivo del proyecto para personalizar los valores en cada proyecto. El archivo *Directory.Build.targets* se lee después del archivo del proyecto. Normalmente, contiene destinos, pero aquí también puede definir propiedades que no desea que los proyectos individuales redefinan.

## <a name="customizations-in-a-project-file"></a>Personalizaciones en un archivo del proyecto

Visual Studio actualiza los archivos del proyecto a medida que realiza cambios en el **Explorador de soluciones** , la ventana **Propiedades** o en **Propiedades del proyecto** , pero el usuario también puede realizar sus propios cambios editando directamente el archivo del proyecto.

Muchos comportamientos de compilación se pueden configurar estableciendo las propiedades de MSBuild, ya sea en el archivo del proyecto de la configuración local de un proyecto, o como se mencionó en la sección anterior, creando un archivo *Directory.Build.props* para establecer las propiedades globalmente para todas las carpetas de proyectos y soluciones. En el caso de las compilaciones ad hoc en la línea de comandos, o scripts, también puede usar la opción `/p` en la línea de comandos para establecer las propiedades de una invocación determinada de MSBuild. Vea [Propiedades comunes de proyectos de MSBuild](common-msbuild-project-properties.md) para obtener información sobre las propiedades que se pueden establecer.

## <a name="next-steps"></a>Pasos siguientes

El proceso de MSBuild tiene varios puntos de extensión distintos de los que se describen aquí. Consulte [Personalizar una compilación](customize-your-build.md) y [Ampliación del proceso de compilación](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Vea también

[MSBuild](msbuild.md)
