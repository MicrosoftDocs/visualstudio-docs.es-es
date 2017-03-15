---
title: MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
caps.latest.revision: 59
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d014b703c491603c86fcd6a89c1dc17f35b0deae
ms.openlocfilehash: 99850b840fbda9f7e7674d926822ff461e69da17
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] es una plataforma para compilar aplicaciones. Este motor, que también se conoce como MSBuild, proporciona un esquema XML para un archivo del proyecto que controla cómo la plataforma de compilación procesa y compila el software. Visual Studio utiliza MSBuild, pero no depende de Visual Studio. Al invocar msbuild.exe en el archivo de proyecto o de solución, puede orquestar y compilar productos en entornos donde no está instalado Visual Studio.  
  
 Visual Studio utiliza MSBuild para cargar y compilar proyectos administrados. Los archivos de proyecto de Visual Studio (.csproj, .vbproj, vcxproj, etc.) contienen código XML de MSBuild que se ejecuta cuando se compila un proyecto mediante el IDE. Los proyectos de Visual Studio importan todos los valores y procesos de compilación necesarios para realizar el trabajo de desarrollo típico, pero se pueden extender o modificar dentro de Visual Studio o mediante un editor XML.  
  
 Para obtener información sobre MSBuild para C++, consulte [MSBuild (Visual C++)](/visual-cpp/build/msbuild-visual-cpp).  
  
 En los ejemplos siguientes se muestra cuándo pueden ejecutarse las compilaciones mediante una línea de comandos de MSBuild en lugar de usar el IDE de Visual Studio.  
  
-   Visual Studio no está instalado.  
  
-   Desea utilizar la versión de 64 bits de MSBuild. Esta versión de MSBuild normalmente es innecesaria, pero permite que MSBuild tenga acceso a más memoria.  
  
-   Desea ejecutar una compilación en varios procesos. Sin embargo, puede utilizar el IDE para lograr el mismo resultado en proyectos de C++ y C#.  
  
-   Desea modificar el sistema de compilación. Por ejemplo, quizá desee habilitar las acciones siguientes:  
  
    -   Preprocesar los archivos antes de alcanzar el compilador.  
  
    -   Copiar los resultados de compilación en un lugar diferente.  
  
    -   Crear archivos comprimidos a partir de los resultados de la compilación.  
  
    -   Realizar un paso de procesamiento posterior. Por ejemplo, puede ser conveniente crear una marca de tiempo en un ensamblado con una versión diferente.  
  
 Puede escribir código en el IDE de Visual Studio, pero ejecutar las compilaciones con MSBuild. Otra alternativa consiste en compilar el código en el IDE en un equipo de desarrollo, pero usar una línea de comandos de MSBuild para compilar el código que está integrado de varios desarrolladores.  
  
> [!NOTE]
>  Puede utilizar Team Foundation Build para compilar, probar e implementar automáticamente la aplicación. El sistema de compilación puede ejecutar automáticamente las compilaciones cuando los desarrolladores protegen el código (por ejemplo, como parte de una estrategia de integración continua) o según una programación (por ejemplo, una prueba nocturna de comprobación de la compilación). Team Foundation Build compila el código con MSBuild. Para obtener más información, consulte [Compilar la aplicación](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
 En este tema se proporciona información general sobre MSBuild. Para obtener un tutorial de introducción, consulte [Tutorial: Utilizar MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **En este tema**  
  
-   [Utilizar MSBuild en el símbolo del sistema](#BKMK_CommandPrompt)  
  
-   [Archivo del proyecto](#BKMK_ProjectFile)  
  
    -   [Propiedades](#BKMK_Properties)  
  
    -   [Elementos](#BKMK_Items)  
  
    -   [Tareas](#BKMK_Tasks)  
  
    -   [Destinos](#BKMK_Targets)  
  
-   [Registros de compilación](#BKMK_BuildLogs)  
  
-   [Utilizar MSBuild en Visual Studio](#BKMK_VisualStudio)  
  
-   [Compatibilidad con múltiples versiones (multi-targeting)](#BKMK_Multitargeting)  
  
##  <a name="BKMK_CommandPrompt"></a> Utilizar MSBuild en el símbolo del sistema  
 Para ejecutar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en el símbolo del sistema, se ha de pasar un archivo del proyecto a MSBuild.exe junto con las opciones de la línea de comandos adecuadas. Las opciones de la línea de comandos permiten establecer propiedades, ejecutar destinos concretos y establecer otras opciones que controlan el proceso de compilación. Por ejemplo, para compilar el archivo `MyProj.proj` con la propiedad `Configuration` establecida en `Debug`, se usaría la sintaxis de línea de comandos siguiente:  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Para obtener más información sobre las opciones de la línea de comandos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
>  Antes de descargar un proyecto, asegúrese de que su código es de confianza.  
  
##  <a name="BKMK_ProjectFile"></a> Archivo del proyecto  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utiliza un formato de archivo del proyecto basado en XML que es sencillo y extensible. El formato de archivo del proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] permite a los desarrolladores describir los elementos que se van a compilar, y también cómo se van a compilar en diferentes sistemas operativos y configuraciones. Además, el formato del archivo de proyecto permite a los desarrolladores crear reglas de compilación reutilizables que se pueden factorizar en archivos independientes para que las compilaciones se ejecuten de forma coherente en los distintos proyectos del producto.  
  
 En las secciones siguientes se describen algunos de los elementos básicos del formato de archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Para obtener un tutorial sobre cómo crear un archivo del proyecto básico, consulte [Tutorial: Crear un archivo del proyecto desde cero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
###  <a name="BKMK_Properties"></a> Propiedades  
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
  
 Para hacer referencia a las propiedades en el archivo del proyecto, se utiliza la sintaxis $(*PropertyName*). Por ejemplo, se puede hacer referencia a las propiedades de los ejemplos anteriores mediante `$(BuildDir)` y `$(Configuration)`.  
  
 Para obtener más información sobre las propiedades, consulte [Propiedades de MSBuild](../msbuild/msbuild-properties.md).  
  
###  <a name="BKMK_Items"></a> Elementos  
 Los elementos son entradas del sistema de compilación y suelen representar archivos. Se agrupan en tipos de acuerdo con los nombres de elemento definidos por el usuario. Estos tipos de elemento se pueden utilizar como parámetros para tareas, que utilizan los elementos individuales para llevar a cabo los pasos del proceso de compilación.  
  
 Los elementos se declaran en el archivo del proyecto mediante la creación de un elemento con el nombre del tipo de elemento como elemento secundario de un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Por ejemplo, el código siguiente crea un tipo de elemento denominado `Compile` que incluye dos archivos.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Para hacer referencia a los tipos de elemento en el archivo del proyecto, se utiliza la sintaxis @(*ItemType*). Por ejemplo, para hacer referencia al tipo de elemento del ejemplo, se usaría `@(Compile)`.  
  
 En MSBuild, los nombres de elementos y atributos distinguen mayúsculas de minúsculas. Sin embargo, los nombres de propiedad, elemento y metadatos no las distinguen. El ejemplo siguiente crea el tipo de elemento `Compile`, `comPile` o cualquier otra variación de grafía, y asigna al tipo de elemento el valor "one.cs;two.cs".  
  
```xml  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Los elementos se pueden declarar utilizando caracteres comodín y pueden contener metadatos adicionales para escenarios de compilación más avanzados. Para obtener más información sobre los elementos, consulte [Elementos](../msbuild/msbuild-items.md).  
  
###  <a name="BKMK_Tasks"></a> Tareas  
 Las tareas son unidades de código ejecutable que se utilizan en proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para realizar operaciones de compilación. Por ejemplo, una tarea podría compilar archivos de entrada o ejecutar una herramienta externa. Las tareas se pueden reutilizar y las pueden compartir desarrolladores diferentes en distintos proyectos.  
  
 La lógica de ejecución de una tarea se escribe en código administrado y se asigna a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mediante el elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Puede escribir su propia tarea mediante la creación de un tipo administrado que implementa la interfaz <xref:Microsoft.Build.Framework.ITask>. Para obtener más información sobre cómo escribir tareas, consulte [Escribir tareas](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] incluye tareas comunes que puede modificar para que se ajusten a sus necesidades.  Algunos ejemplos son [Copy](../msbuild/copy-task.md), que copia archivos, [MakeDir](../msbuild/makedir-task.md), que crea directorios, y [Csc](../msbuild/csc-task.md), que compila archivos de código fuente de Visual C#. Para obtener una lista de las tareas disponibles junto con información de uso, consulte [Referencia de tareas](../msbuild/msbuild-task-reference.md).  
  
 Para ejecutar una tarea en un archivo del proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], se crea un elemento con el nombre de la tarea como elemento secundario de un elemento [Target](../msbuild/target-element-msbuild.md). Las tareas aceptan normalmente parámetros, que se pasan como atributos del elemento. Tanto las propiedades como los elementos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se pueden utilizar como parámetros. Por ejemplo, el código siguiente llama a la tarea [MakeDir](../msbuild/makedir-task.md) y le pasa el valor de la propiedad `BuildDir` que se declaró en el ejemplo anterior.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Para obtener más información sobre las tareas, consulte [Tareas](../msbuild/msbuild-tasks.md).  
  
###  <a name="BKMK_Targets"></a> Destinos  
 Los destinos agrupan tareas en un orden particular y exponen secciones del archivo de proyecto como puntos de entrada en el proceso de compilación. Los destinos suelen agruparse en secciones lógicas para aumentar la legibilidad y permitir la expansión. Dividir los pasos de compilación en destinos permite llamar a una parte del proceso de compilación desde otros destinos sin necesidad de copiar dicha sección de código en cada destino. Por ejemplo, si varios puntos de entrada del proceso de compilación necesitan que se compilen referencias, se puede crear un destino que compile referencias y, a continuación, ejecutar dicho destino desde cada punto de entrada que sea necesario.  
  
 Los destinos se declaran en el archivo del proyecto mediante el elemento [Target](../msbuild/target-element-msbuild.md). Por ejemplo, en el código siguiente se crea un destino denominado `Compile` que, a continuación, llama a la tarea [Csc](../msbuild/csc-task.md) que tiene la lista de elementos que se declaró en el ejemplo anterior.  
  
```xml  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 En escenarios más avanzados, los destinos se pueden usar para describir relaciones mutuas y llevar a cabo análisis de dependencia, de modo que se pueden omitir secciones completas del proceso de compilación si un destino concreto está actualizado. Para obtener más información sobre los destinos, consulte [Destinos](../msbuild/msbuild-targets.md).  
  
##  <a name="BKMK_BuildLogs"></a> Registros de compilación  
 Puede registrar errores de compilación, advertencias y mensajes en la consola o en otro dispositivo de salida. Para obtener más información, consulte [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md) y [Registro de MSBuild](../msbuild/logging-in-msbuild.md).  
  
##  <a name="BKMK_VisualStudio"></a> Utilizar MSBuild en Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza el formato de archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para almacenar información de compilación sobre proyectos administrados. La configuración del proyecto que se agrega o se modifica mediante la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se refleja en el archivo .*proj que se genera para cada proyecto. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza una instancia hospedada de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para compilar proyectos administrados. Esto significa que un proyecto administrado se puede compilar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o en el símbolo del sistema (aunque [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no esté instalado) y los resultados serán idénticos.  
  
 Para obtener un tutorial sobre cómo utilizar MSBuild en Visual Studio, consulte [Tutorial: Cómo utilizar MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
##  <a name="BKMK_Multitargeting"></a> Compatibilidad con múltiples versiones (multi-targeting)  
 Con Visual Studio, puede compilar una aplicación para que se ejecute en cualquiera de las versiones de .NET Framework. Por ejemplo, puede compilar una aplicación para que se ejecute en .NET Framework 2.0 en una plataforma de 32 bits y compilar esa misma aplicación para que se ejecute en .NET Framework 4.5 en una plataforma de 64 bits. La capacidad de compilar para más de una versión de Framework se denomina multitargeting.  
  
 Estas son algunas de las ventajas de la compatibilidad con múltiples versiones (multitargeting):  
  
-   Puede desarrollar aplicaciones que tienen como destino versiones anteriores de .NET Framework, por ejemplo, las versiones 2.0, 3.0 y 3.5.  
  
-   Puede usar como destino marcos distintos de .NET Framework, por ejemplo, Silverlight.  
  
-   Puede tener como destino un *perfil de Framework*, que es un subconjunto predefinido de un marco de trabajo de destino.  
  
-   Si se publica algún Service Pack para la versión actual de .NET Framework, podría utilizarlo como destino.  
  
-   La compatibilidad con múltiples versiones (multitargeting) garantiza que una aplicación utilice solo la funcionalidad que está disponible en el marco y plataforma de destino.  
  
 Para obtener más información, consulte [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Tutorial: Crear un archivo del proyecto de MSBuild desde el principio](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Muestra la forma de crear un archivo básico del proyecto de forma incremental, utilizando solo un editor de texto.|  
|[Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md)|Presenta los bloques de compilación de MSBuild y muestra la forma de escribir, manipular y depurar proyectos de MSBuild sin cerrar el IDE de Visual Studio.|  
|[Conceptos de MSBuild](../msbuild/msbuild-concepts.md)|Presenta los cuatro bloques de compilación de MSBuild: propiedades, elementos, destinos y tareas.|  
|[Elementos](../msbuild/msbuild-items.md)|Describe los conceptos generales en que se basa el formato de archivo de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] y la manera de encajar las piezas.|  
|[Propiedades de MSBuild](../msbuild/msbuild-properties.md)|Presenta las propiedades y las colecciones de propiedades. Las propiedades son pares clave/valor que se pueden utilizar para configurar compilaciones.|  
|[Destinos](../msbuild/msbuild-targets.md)|Explica cómo agrupar las tareas entre sí en un orden concreto y habilitar las secciones del proceso de compilación para que se las pueda llamar desde la línea de comandos.|  
|[Tareas](../msbuild/msbuild-tasks.md)|Muestra la forma de crear una unidad de código ejecutable que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede usar para realizar operaciones de compilación indivisibles.|  
|[Condiciones](../msbuild/msbuild-conditions.md)|Explica la forma de utilizar el atributo `Condition` en un elemento de MSBuild.|  
|[Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)|Presenta el procesamiento por lotes, la realización de transformaciones, la compatibilidad con múltiples versiones (multitargeting) y otras técnicas avanzadas.|  
|[Registro de MSBuild](../msbuild/logging-in-msbuild.md)|Describe cómo registrar los eventos, mensajes y errores de compilación.|  
|[Recursos adicionales](../msbuild/additional-msbuild-resources.md)|Enumera los recursos de compatibilidad y comunidad para obtener más información sobre MSBuild.|  
  
## <a name="reference"></a>Referencia  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)  
 Muestra vínculos a temas que contienen información de referencia.  
  
 Glosario  
 Define los términos comunes de MSBuild.
