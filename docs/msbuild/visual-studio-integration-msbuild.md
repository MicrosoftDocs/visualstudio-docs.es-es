---
title: Integración de Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631203"
---
# <a name="visual-studio-integration-msbuild"></a>Integración de Visual Studio (MSBuild)

Visual Studio hospeda MSBuild para cargar y compilar proyectos administrados. Puesto que MSBuild es responsable del proyecto, prácticamente cualquier proyecto con el formato de MSBuild puede utilizarse correctamente en Visual Studio, aunque el proyecto lo haya creado una herramienta diferente y tenga un proceso de compilación personalizado.

 En este tema se describen los aspectos específicos del hospedaje de MSBuild en Visual Studio que deben tenerse en cuenta al personalizar los proyectos y los archivos *.targets* que se carguen y se compilen en Visual Studio. Le ayudarán a garantizar que las características de Visual Studio como IntelliSense y la depuración funcionan para el proyecto personalizado.

 Para información sobre proyectos de C++, consulte [Archivos de proyecto](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Extensiones de nombre de archivo de proyecto

 *MSBuild.exe* reconoce cualquier extensión de nombre de archivo de proyecto que coincida con el patrón *.\*proj*. Sin embargo, Visual Studio solamente reconoce un subconjunto de estas extensiones de nombre de archivo de proyecto, que determinan el sistema de proyectos específico del lenguaje que cargará el proyecto. Visual Studio no dispone de ningún sistema de proyectos independiente del lenguaje basado en MSBuild.

 Por ejemplo, el sistema de proyectos de C# carga archivos *.csproj*, pero Visual Studio no puede cargar ningún archivo *.xxproj*. Un archivo de proyecto para archivos de origen en un lenguaje arbitrario debe utilizar la misma extensión que los archivos de proyecto de Visual Basic o C# que se van a cargar en Visual Studio.

## <a name="well-known-target-names"></a>Nombres de destino conocidos

 Al hacer clic en el comando **Compilar** en Visual Studio, se ejecutará el destino predeterminado del proyecto. A menudo, este destino también se denomina `Build`. Al elegir el comando **Recompilar** o **Limpiar** , se intentará ejecutar un destino del mismo nombre en el proyecto. Al hacer clic en **Publicar** , se ejecutará un destino denominado `PublishOnly` en el proyecto.

## <a name="configurations-and-platforms"></a>Configuraciones y plataformas

 Las configuraciones se representan en los proyectos de MSBuild mediante propiedades agrupadas en un elemento `PropertyGroup` que contiene un atributo `Condition`. Visual Studio examina estas condiciones para crear una lista de las configuraciones y plataformas del proyecto que se van a mostrar. Para extraer correctamente esta lista, las condiciones deben tener un formato similar al siguiente:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Con este fin,Visual Studio examina las condiciones en `PropertyGroup`, `ItemGroup`, `Import`, la propiedad y los elementos.

## <a name="additional-build-actions"></a>Acciones de compilación adicionales

 Visual Studio permite cambiar el nombre de los tipos de elemento de un archivo de un proyecto con la propiedad **Acción de compilación** de la ventana **Propiedades de archivo**. Los nombres de tipos de elementos **Compile**, **EmbeddedResource**, **Content** y **None** siempre se muestran en este menú, junto con otros nombres de tipos de elementos que ya tenga en su proyecto. Para garantizar que los nombres de los tipos de elemento personalizados siempre estén disponibles en este menú, puede agregarlos a un tipo de elemento denominado `AvailableItemName`. Por ejemplo, al agregar lo siguiente al archivo de proyecto, se agrega el tipo personalizado **JScript** a este menú para todos los proyectos que lo importen:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Algunos nombres de tipo de elemento son específicos de Visual Studio, pero no se muestran en esta lista desplegable.

## <a name="in-process-compilers"></a>Compiladores activos

 Cuando sea posible, Visual Studio intentará utilizar la versión activa del compilador de Visual Basic con el fin de mejorar el rendimiento. (No es aplicable a C#). Para que esto funcione correctamente, se deben cumplir las condiciones siguientes:

- En un destino del proyecto, debe haber una tarea denominada `Vbc` para los proyectos de Visual Basic.

- El parámetro `UseHostCompilerIfAvailable` de la tarea debe tener el valor true.

## <a name="design-time-intellisense"></a>IntelliSense en tiempo de diseño

 Para obtener compatibilidad con IntelliSense en Visual Studio antes de que una compilación haya generado un ensamblado de salida, se deben cumplir las condiciones siguientes:

- Debe haber un destino denominado `Compile`.

- El destino `Compile` o alguna de sus dependencias deben llamar a la tarea de compilador para el proyecto, como `Csc` o `Vbc`.

- El destino `Compile` o alguna de sus dependencias debe hacer que el compilador reciba todos los parámetros necesarios para IntelliSense, en particular todas las referencias.

- Se deben cumplir las condiciones que aparecen en la sección [Compiladores activos](#in-process-compilers).

## <a name="build-solutions"></a>Soluciones de compilación

 En Visual Studio, la propia aplicación de Visual Studio controla el archivo de solución y el orden de compilación de los proyectos. Al compilar una solución con *msbuild.exe* en la línea de comandos, MSBuild analiza el archivo de solución y ordena las compilaciones del proyecto. En ambos casos, los proyectos se compilan individualmente en orden de dependencia y no se recorren las referencias entre proyectos. Por el contrario, cuando los proyectos individuales se compilan con *msbuild.exe*, se recorren las referencias entre proyectos.

 Para compilar en Visual Studio, la propiedad `$(BuildingInsideVisualStudio)` se establece en `true`. Esto se puede utilizar en el proyecto o en archivos *.targets* para que la compilación se comporte de manera diferente.

## <a name="display-properties-and-items"></a>Visualización de propiedades y elementos

 Visual Studio reconoce algunos nombres y valores de propiedad. Por ejemplo, la propiedad siguiente de un proyecto hará que aparezca **Aplicación Windows** en el cuadro **Tipo de aplicación** del **Diseñador de proyectos**.

```xml
<OutputType>WinExe</OutputType>
```

 El valor de propiedad se puede editar en el **Diseñador de proyectos** y guardar en el archivo del proyecto. Si al editar la propiedad manualmente se le da un valor no válido, Visual Studio mostrará una advertencia cuando se cargue el proyecto y reemplazará el valor no válido por un valor predeterminado.

 Visual Studio puede aplicar valores predeterminados a algunas propiedades. Estas propiedades no se conservarán en el archivo del proyecto a menos que tengan valores no predeterminados.

 Las propiedades con nombres arbitrarios no se muestran en Visual Studio. Para modificar las propiedades arbitrarias en Visual Studio, debe abrir el archivo del proyecto en el editor XML y editarlas a mano. Para más información, consulte la sección [Edición de archivos de proyecto en Visual Studio](#edit-project-files-in-visual-studio) más adelante en este tema.

 Los elementos definidos en el proyecto con nombres de tipo de elemento arbitrarios se muestran de forma predeterminada en el **Explorador de soluciones** bajo su nodo de proyecto. Para ocultar un elemento, establezca los metadatos `Visible` en `false`. Por ejemplo, el elemento siguiente participará en el proceso de compilación pero no se mostrará en el **Explorador de soluciones**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> El **Explorador de soluciones** para proyectos de C++ ignora los metadatos de `Visible`. Los elementos se mostrarán siempre aunque `Visible` esté establecido en "false".

 De forma predeterminada, no se muestran los elementos declarados en archivos importados al proyecto. Los elementos creados durante el proceso de compilación nunca se muestran en el **Explorador de soluciones**.

## <a name="conditions-on-items-and-properties"></a>Condiciones en elementos y propiedades

 Durante una compilación, se respetan totalmente todas las condiciones.

 Al determinar los valores de propiedad que se van a mostrar, las propiedades que Visual Studio considera dependientes de la configuración se evalúan de manera diferente que las que considera independientes. Para las propiedades que considera dependientes de la configuración, Visual Studio establece las propiedades `Configuration` y `Platform` de manera apropiada e indica a MSBuild que vuelva a evaluar el proyecto. En el caso de las propiedades que considera como independientes de la configuración, no importa cómo se evalúen las condiciones.

 Las expresiones condicionales en los elementos siempre se omiten al decidir si el elemento debe mostrarse en el **Explorador de soluciones**.

## <a name="debugging"></a>Depuración

 Para buscar e iniciar el ensamblado de salida y asociar el depurador, Visual Studio necesita que las propiedades `OutputPath`, `AssemblyName` y `OutputType` estén definidas correctamente. El depurador no podrá realizar la asociación si el proceso de compilación no hiciera que el compilador generase un archivo *.pdb*.

## <a name="design-time-target-execution"></a>Ejecución del destino en tiempo de diseño

 Visual Studio intenta ejecutar los destinos con algunos nombres cuando carga un proyecto. Estos destinos incluyen `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` y `CopyRunEnvironmentFiles`. Visual Studio ejecuta estos destinos para que el compilador pueda inicializarse con el fin de proporcionar IntelliSense, el depurador pueda inicializarse y las referencias mostradas en el Explorador de soluciones puedan resolverse. Si estos destinos no están presentes, el proyecto se cargará y se compilará correctamente pero la experiencia en tiempo de diseño de Visual Studio no será totalmente funcional.

## <a name="edit-project-files-in-visual-studio"></a>Edición de archivos de proyecto en Visual Studio

 Para editar directamente un proyecto de MSBuild, puede abrir el archivo del proyecto en el editor XML de Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Para descargar y editar un archivo de proyecto en Visual Studio

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Descargar el proyecto**.

     El proyecto aparecerá marcado como **(no disponible)** .

2. En el **Explorador de soluciones**, abra el menú contextual del proyecto no disponible y seleccione **Editar\<Archivo de proyecto>** .

     El archivo de proyecto se abrirá en el Editor XML de Visual Studio.

3. Edite, guarde y, a continuación, cierre el archivo de proyecto.

4. En el **Explorador de soluciones**, abra el menú contextual del proyecto no disponible y, a continuación, elija **Volver a cargar el proyecto**.

## <a name="intellisense-and-validation"></a>IntelliSense y validación

 Al utilizar el editor XML para modificar archivos de proyecto, los archivos de esquema de MSBuild administran la validación e IntelliSense. Estos archivos se instalan en la caché del esquema, que se encuentra en *\<directorio de instalación de Visual Studio>\Xml\Schemas\1033\MSBuild*.

 Los tipos básicos de MSBuild se definen en *Microsoft.Build.Core.xsd* y los tipos comunes utilizados por Visual Studio se definen en *Microsoft.Build.CommonTypes.xsd*. Para personalizar los esquemas con el fin de disponer de IntelliSense y de la validación para los nombres de tipo de elemento, propiedades y tareas personalizados, puede editar *Microsoft.Build.xsd* o crear su propio esquema que incluya los esquemas CommonTypes o básico. Si crea su propio esquema, tendrá que dirigir el editor XML para que lo busque mediante la ventana **Propiedades** .

## <a name="edit-loaded-project-files"></a>Edición de archivos de proyecto cargados

 Visual Studio almacena en memoria caché el contenido de los archivos de proyecto y de los archivos importados por los archivos de proyecto. Si edita un archivo de proyecto cargado, Visual Studio pedirá automáticamente que recargue el proyecto para que se apliquen los cambios. Sin embargo, si edita un archivo importado por un proyecto cargado, no habrá ninguna solicitud y deberá descargar y recargar el proyecto manualmente para que se apliquen los cambios.

## <a name="output-groups"></a>Grupos de resultados

 Algunos destinos definidos en *Microsoft.Common.targets* tienen nombres acabados en `OutputGroups` o `OutputGroupDependencies`. Visual Studio llama a estos destinos para obtener listas específicas de las salidas del proyecto. Por ejemplo, el destino `SatelliteDllsProjectOutputGroup` crea una lista de todos los ensamblados satélite que creará una compilación. Características como la publicación, la implementación y las referencias entre proyectos utilizan estos grupos de resultados. Los proyectos que no los definen se cargarán y compilarán en Visual Studio, pero es posible que algunas características no funcionen correctamente.

## <a name="reference-resolution"></a>Resolución de referencias

 La resolución de referencias es el proceso de utilizar los elementos de referencia almacenados en un archivo del proyecto para buscar los ensamblados reales. Visual Studio debe desencadenar una resolución de referencias para que se muestren las propiedades detalladas de cada referencia en la ventana **Propiedades**. En la lista siguiente se describen los tres tipos de referencias y cómo se resuelven.

- Referencias de ensamblado:

   El sistema de proyectos llama a un destino con el nombre conocido `ResolveAssemblyReferences`. Este destino debe generar elementos con el nombre de tipo `ReferencePath`. Cada uno de estos elementos debe tener una especificación de elemento (el valor del atributo `Include` de un elemento) que contenga la ruta completa a la referencia. Los elementos deben tener todos los metadatos de los elementos de entrada recorridos, además de los nuevos metadatos siguientes:

  - `CopyLocal`, que indica si el ensamblado debe copiarse en la carpeta de salida, establecida en true o en false.

  - `OriginalItemSpec`, que contiene la especificación del elemento original de la referencia.

  - `ResolvedFrom`, establecido en "{TargetFrameworkDirectory}" si se ha resuelto desde el directorio de .NET Framework.

- Referencias COM:

   El sistema de proyectos llama a un destino con el nombre conocido `ResolveCOMReferences`. Este destino debe generar elementos con el nombre de tipo `ComReferenceWrappers`. Cada uno de estos elementos debe tener una especificación del elemento que contiene la ruta de acceso completa al ensamblado de interoperabilidad para obtener la referencia COM. Los elementos deben tener todos los metadatos de los elementos de entrada recorridos, además de los nuevos metadatos con el nombre `CopyLocal`, que indica si el ensamblado se debe copiar en la carpeta de salida, establecido en true o false.

- Referencias nativas

   El sistema de proyectos llama a un destino con el nombre conocido `ResolveNativeReferences`. Este destino debe generar elementos con el nombre de tipo `NativeReferenceFile`. Los elementos deben tener todos los metadatos de los elementos de entrada recorridos, además de un nuevo fragmento de metadatos denominado `OriginalItemSpec`, que contiene la especificación del elemento original de la referencia.

## <a name="performance-shortcuts"></a>Métodos abreviados de rendimiento

 Si usa el IDE de Visual Studio para iniciar la depuración (con la tecla F5 o la opción **Depurar** > **Iniciar depuración** en la barra de menús), o para compilar el proyecto (por ejemplo, **Compilar** > **Compilar solución**), el proceso de compilación utiliza una comprobación de actualización rápida para mejorar el rendimiento. En algunos casos en los que las compilaciones personalizadas crean archivos que, a su vez, se compilan, la comprobación de actualización rápida no identifica correctamente los archivos modificados. Los proyectos que necesitan otras comprobaciones de actualización más completas pueden desactivar la comprobación rápida estableciendo la variable de entorno `DISABLEFASTUPTODATECHECK=1`. O bien, los proyectos pueden establecerla como una propiedad de MSBuild en el proyecto o en un archivo que el proyecto importe.

 Para las compilaciones periódicas en Visual Studio, no se aplica la comprobación de actualización rápida y el proyecto se compilará como si se invocara la compilación en un símbolo del sistema.

## <a name="see-also"></a>Vea también

- [Cómo: Extender el proceso de compilación de Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Iniciar una compilación desde el IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrar las extensiones de .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)
- [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Tarea Csc](../msbuild/csc-task.md)
- [Vbc (Tarea)](../msbuild/vbc-task.md)
