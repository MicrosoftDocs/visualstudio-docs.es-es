---
title: Propiedades comunes de proyectos de MSBuild | Microsoft Docs
description: Obtenga información sobre las propiedades comunes de proyectos de MSBuild que se pueden definir o usar en archivos de proyectos o que pueden incluirse en archivos .targets que proporciona MSBuild.
ms.custom: SEO-VS-2020
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 548116fc3c9b360a866f14e32074111dfdc872d9
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533880"
---
# <a name="common-msbuild-project-properties"></a>Propiedades comunes de proyectos de MSBuild

En la tabla siguiente se enumeran las propiedades usadas con frecuencia definidas en los archivos de proyecto de Visual Studio o incluidas en archivos *.targets* que proporciona MSBuild.

 Los archivos de proyecto de Visual Studio ( *.csproj*, *.vbproj*, *.vcxproj* y otros) contienen código XML de MSBuild que se ejecuta cuando se compila un proyecto mediante el IDE. Normalmente, los proyectos importan uno o más archivos *.targets* para definir su proceso de compilación. Para obtener más información, vea [Archivos .targets de MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Lista de propiedades y parámetros comunes

| Nombre de propiedad o parámetro | Tipos de proyecto | Descripción |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Especifica carpetas adicionales en las que los compiladores deben buscar ensamblados de referencia. |
| AddModules | .NET | Hace que el compilador facilite toda la información de tipos presente en los archivos especificados al proyecto que se está compilando. Esta propiedad es equivalente al modificador `/addModules` del compilador. |
| ALToolPath | .NET | Ruta de acceso donde se puede encontrar *AL.exe*. Esta propiedad reemplaza a la versión actual de *AL.exe* para permitir el uso de otra versión. |
| ApplicationIcon | .NET | Archivo de icono *.ico* que se va a pasar al compilador para incrustarlo como un icono de Win32. Esta propiedad es equivalente al modificador `/win32icon` de compilador. |
| ApplicationManifest | Todas | Especifica la ruta de acceso del archivo que se utiliza para generar la información externa del manifiesto del Control de cuentas de usuario (UAC). Solo se aplica a los proyectos de Visual Studio que tienen como destino Windows Vista.<br /><br /> En la mayoría de los casos, el manifiesto está incrustado. En cambio, si usa una implementación de COM sin registro o de ClickOnce, el manifiesto puede ser un archivo externo que se instala junto con los ensamblados de la aplicación. Para obtener más información, vea la propiedad NoWin32Manifest en este tema. |
| AssemblyOriginatorKeyFile | .NET | Especifica el archivo que se ha usado para firmar el ensamblado ( *.snk* o *.pfx*) y que se ha pasado a [ResolveKeySource (Tarea)](../msbuild/resolvekeysource-task.md) para generar la clave real empleada para firmar el ensamblado. |
| AssemblySearchPaths | .NET | Lista de ubicaciones donde se realizarán las búsquedas durante la resolución de ensamblados de referencia en tiempo de compilación. El orden en que aparecen las rutas de acceso en esta lista es importante porque las rutas de acceso situadas antes en la lista tienen prioridad sobre las entradas posteriores. |
| AssemblyName | .NET | Nombre del ensamblado resultante final una vez compilado el proyecto. |
| BaseAddress | .NET | Especifica la dirección base del ensamblado resultante principal. Esta propiedad es equivalente al modificador `/baseaddress` del compilador. |
| BaseIntermediateOutputPath | Todas | Carpeta de nivel superior donde se crean todas las carpetas de resultados intermedios específicas de la configuración. El valor predeterminado es `obj\`. El siguiente código muestra un ejemplo: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Todas | Especifica la ruta de acceso base del archivo de salida. Si se establece, MSBuild usará `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Ejemplo de sintaxis: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Todas | Valor booleano que indica si las referencias del proyecto se compilan o limpian en paralelo cuando se utiliza MSBuild con varios procesadores. El valor predeterminado es `true`, que indica que los proyectos se compilarán en paralelo si el sistema tiene varios núcleos o procesadores. |
| BuildProjectReferences | Todas | Valor booleano que indica si MSBuild compilará las referencias de proyecto. Establezca el valor automáticamente en `false` si va a compilar el proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio; en caso contrario, use `true`. Puede especificarse `-p:BuildProjectReferences=false` en la línea de comandos para evitar la comprobación de que los proyectos a los que se hace referencia están actualizados. |
| CleanFile | Todas | Nombre del archivo que se utilizará como "caché limpia". La memoria caché limpia es una lista de archivos generados que se eliminarán durante la operación de limpieza. El proceso de compilación coloca el archivo en la ruta de acceso de los resultados intermedios.<br /><br /> Esta propiedad solo especifica nombres de archivo sin información sobre su ruta de acceso. |
| CodePage | .NET | Especifica la página de códigos que se va a utilizar para todos los archivos de código fuente en la compilación. Esta propiedad es equivalente al modificador `/codepage` del compilador. |
| CompilerResponseFile | .NET | Archivo de respuesta opcional que se puede pasar a las tareas del compilador. |
| Configuración | Todas | La configuración que está compilando, generalmente `Debug` o `Release`, pero configurable con respecto a la solución y el proyecto. |
| CscToolPath | C# | Ruta de acceso de *csc.exe*, el compilador de C#. |
| CustomBeforeMicrosoftCommonTargets | Todas | Nombre de un archivo de proyecto o archivo de destinos que se importará automáticamente antes de importar los destinos comunes. |
| DebugSymbols | Todas | Valor booleano que indica si la compilación genera símbolos.<br /><br /> Si se establece **-p:DebugSymbols=false** en la línea de comandos, se deshabilita la generación de archivos de símbolos ( *.pdb*) de la base de datos del programa. |
| DebugType | Todas | Define el nivel de información de depuración que desea generar. Los valores válidos son "full," "pdbonly," "portable", "embedded" y "none". |
| DefineConstants | .NET | Permite definir constantes condicionales para el compilador. Los pares símbolo-valor van separados por punto y coma, y se especifican con la siguiente sintaxis:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> Esta propiedad es equivalente al modificador `/define` de compilador. |
| DefineDebug | Todas |  Valor booleano que indica si desea definir la constante DEBUG. |
| DefineTrace | Todas | Valor booleano que indica si desea definir la constante TRACE. |
| DelaySign | .NET | Valor booleano que indica si desea retrasar la firma del ensamblado en lugar de firmarlo completamente. |
| Determinista | .NET | Se trata de un valor booleano que indica si el compilador debe producir ensamblados idénticos para entradas idénticas. Este parámetro corresponde al modificador `/deterministic` de los compiladores. |
| DisableFastUpToDateCheck | Todas | Valor booleano que solo se aplica a Visual Studio. El administrador de compilación de Visual Studio utiliza un proceso denominado FastUpToDateCheck para determinar si es necesario recompilar un proyecto para actualizarlo. Este proceso es más rápido que utilizar MSBuild. Al establecer la propiedad DisableFastUpToDateCheck en `true`, puede omitir el administrador de compilación de Visual Studio y obligarlo a usar MSBuild para determinar si el proyecto está actualizado. |
| DocumentationFile | .NET | Nombre del archivo que se genera como archivo de documentación XML. Este nombre solo incluye el nombre de archivo sin información sobre la ruta de acceso. |
| ErrorReport | .NET | Especifica cómo debe el compilador documentar los errores internos del compilador. Los valores válidos son "prompt", "send" o "none". Esta propiedad es equivalente al modificador `/errorreport` del compilador. |
| ExcludeDeploymentUrl | .NET | [GenerateDeploymentManifest (Tarea)](../msbuild/generatedeploymentmanifest-task.md) agrega una etiqueta deploymentProvider al manifiesto de implementación si el archivo de proyecto incluye alguno de los elementos siguientes:<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> Sin embargo, mediante ExcludeDeploymentUrl, puede evitar que la etiqueta deploymentProvider se agregue al manifiesto de implementación aunque se especifique alguna de las direcciones URL anteriores. Para ello, agregue la siguiente propiedad al archivo de proyecto:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Nota:**  ExcludeDeploymentUrl no se expone en el IDE de Visual Studio y solo se puede establecer manualmente editando el archivo de proyecto. Al establecer esta propiedad, la publicación desde Visual Studio no resulta afectada; es decir, la etiqueta deploymentProvider se agregará de igual modo a la dirección URL especificada por PublishUrl. |
| FileAlignment | .NET | Especifica, en bytes, dónde se alinean las secciones del archivo de salida. Los valores válidos son 512, 1024, 2048, 4096, 8192. Esta propiedad es equivalente al modificador `/filealignment` del compilador. |
| FrameworkPathOverride | Visual Basic | Especifica la ubicación de *mscorlib.dll* y *microsoft.visualbasic.dll*. Este parámetro es equivalente al modificador `/sdkpath` del compilador de *vbc.exe*. |
| GenerateDocumentation | .NET | Parámetro booleano que indica si la compilación generará la documentación. Si es `true`, la compilación genera información de documentación y la coloca en un archivo *.xml* junto con el nombre del archivo ejecutable o la biblioteca creada por la tarea de compilación. |
| GenerateFullPaths | C# | Genere rutas de acceso completas para los nombres de archivo de la salida mediante la opción del compilador [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| GenerateSerializationAssemblies | .NET | Indica si se deben generar ensamblados de serialización XML mediante *SGen.exe*, que puede establecerse en activado, automático o desactivado. Esta propiedad solo se usa para los ensamblados que tienen como destino .NET Framework. Para generar ensamblados de serialización XML para los ensamblados de .NET Standard o .NET Core, haga referencia al paquete NuGet *Microsoft.XmlSerializer.Generator*. |
| IntermediateOutputPath | Todas | Ruta de acceso intermedia completa de los resultados derivada de `BaseIntermediateOutputPath`, si no se especificó ninguna ruta de acceso. Por ejemplo, *\obj\debug\\* . |
| KeyContainerName | Todas | Nombre del contenedor de claves de nombre seguro. |
| KeyOriginatorFile | Todas | Nombre del archivo de claves de nombre seguro. |
| ModuleAssemblyName | .NET | Nombre del ensamblado al que se incorporará el módulo compilado. Esta propiedad es equivalente al modificador `/moduleassemblyname` de compilador. |
| MSBuildProjectExtensionsPath | Todas | Especifica la ruta de acceso donde se encuentran las extensiones de proyecto. De forma predeterminada, esto tiene el mismo valor que `BaseIntermediateOutputPath`. |
| NoLogo | Todas | Valor booleano que indica si se va a desactivar el logotipo del compilador. Esta propiedad es equivalente al modificador `/nologo` del compilador. |
| NoStdLib | .NET | Valor booleano que indica si se debe evitar hacer referencia a la biblioteca estándar (*mscorlib.dll*). El valor predeterminado es `false`. |
| NoVBRuntimeReference | Visual Basic | Valor booleano que indica si el entorno de ejecución de Visual Basic (*Microsoft.VisualBasic.dll*) debe incluirse como referencia en el proyecto. |
| NoWarn | .NET | Suprime las advertencias especificadas. Solo debe especificarse la parte numérica del identificador de advertencia. Las advertencias múltiples se separan con punto y coma. Este parámetro corresponde al modificador `/nowarn` de los compiladores. |
| NoWin32Manifest | .NET | Valor booleano que indica si la información del manifiesto de Control de cuentas de usuario (UAC) se incrustará en el archivo ejecutable de la aplicación. Solo se aplica a los proyectos de Visual Studio que tienen como destino Windows Vista. En los proyectos que se implementan con ClickOnce y COM sin registro, se omite este elemento. `False` (valor predeterminado) especifica que la información de manifiesto del Control de cuentas de usuario (UAC) se incrusta en el ejecutable de la aplicación. `True` especifica que la información de manifiesto de UAC no debe incrustarse.<br /><br /> Esta propiedad solo se aplica a los proyectos de Visual Studio que tienen como destino Windows Vista. En los proyectos que se implementan con ClickOnce y COM sin registro, se omite esta propiedad.<br /><br /> Solo debe agregar NoWin32Manifest si no quiere que Visual Studio inserte información del manifiesto en el archivo ejecutable de la aplicación; este proceso se denomina *virtualización*. Para utilizar la virtualización, establezca `<ApplicationManifest>` junto con `<NoWin32Manifest>` del modo siguiente:<br /><br /> - Para proyectos de Visual Basic, quite el nodo `<ApplicationManifest>`. (En los proyectos de Visual Basic, `<NoWin32Manifest>` se omite cuando existe un nodo `<ApplicationManifest>`).<br />- En los proyectos de C#, establezca `<ApplicationManifest>` en `False` y `<NoWin32Manifest>` en `True`. (En los proyectos de C#, `<ApplicationManifest>` invalida `<NoWin32Manifest>`).<br /> Esta propiedad es equivalente al modificador `/nowin32manifest` del compilador de *vbc.exe*. |
| Optimize | .NET | Valor booleano que, cuando se establece en `true`, permite la optimización del compilador. Esta propiedad es equivalente al modificador `/optimize` del compilador. |
| OptionCompare | VisualBasic | Especifica la forma en que se realizan las comparaciones de cadenas. Los valores válidos son "binary" o "text". Esta propiedad es equivalente al modificador `/optioncompare` del compilador de *vbc.exe*. |
| OptionExplicit | Visual Basic | Valor booleano que, cuando se establece en `true`, requiere la declaración explícita de variables en el código fuente. Esta propiedad es equivalente al modificador `/optionexplicit` del compilador. |
| OptionInfer | Visual Basic | Valor booleano que, cuando se establece en `true`, permite la inferencia de tipos de variables. Esta propiedad es equivalente al modificador `/optioninfer` del compilador. |
| OptionStrict | Visual Basic | Valor booleano que, cuando se establece en `true`, hace que la tarea de compilación exija una semántica de tipos estricta para restringir las conversiones de tipos implícitas. Esta propiedad es equivalente al modificador `/optionstrict` del compilador de *vbc.exe*. |
| OutDir | Todas | Indica la ubicación de salida final del proyecto o la solución. Al compilar una solución, OutDir se puede usar para recopilar varios resultados del proyecto en una ubicación. Además, OutDir se incluye en AssemblySearchPaths, que se usa para resolver referencias. Por ejemplo, *bin\Debug*. |
| OutputPath | Todas | Especifica la ruta de acceso al directorio de salida con respecto al directorio del proyecto, por ejemplo, *bin\Debug*. |
| OutputType | Todas |  Especifica el formato del archivo de salida. Este parámetro puede tener uno de los valores siguientes:<br /><br /> -   Library. Crea una biblioteca de códigos. (Valor predeterminado).<br />-   Exe. Crea una aplicación de consola.<br />-   Module. Crea un módulo.<br />-   Winexe. Crea un programa de Windows.<br /><br /> En C# y Visual Basic, esta propiedad es equivalente al modificador `/target`. |
| OverwriteReadOnlyFiles | Todas | Valor booleano que indica si desea que la compilación sobrescriba los archivos de solo lectura o produzca un error. |
| PathMap | .NET | Especifica cómo asignar rutas físicas a nombres de ruta de origen generados por el compilador. Esta propiedad es equivalente al modificador `/pathmap` de los compiladores. |
| PdbFile | .NET | Nombre de archivo del archivo *.pdb* que va a emitir. Esta propiedad es equivalente al modificador `/pdb` del compilador de *csc.exe*. |
| Plataforma | Todas | Sistema operativo para el que se está compilando. Algunos ejemplos de compilaciones de .NET Framework son "Cualquier CPU", "x86" y "x64". |
| ProcessorArchitecture | .NET | Arquitectura de procesador utilizada cuando se resuelven las referencias de ensamblado. Los valores válidos son "msil", "x86", "amd64" o "ia64". |
| ProduceOnlyReferenceAssembly | .NET | Valor booleano que instruye al compilador que emita solo un ensamblado de referencia, en lugar de código compilado. No se puede usar con `ProduceReferenceAssembly`.  Esta propiedad corresponde al modificador `/refonly` de los compiladores de *vbc.exe* y *csc.exe*. |
| ProduceReferenceAssembly | .NET | Se trata de un valor booleano que cuando se establece en `true` permite la producción de [ensamblados de referencia](/dotnet/standard/assembly/reference-assemblies) para el ensamblado actual. `Deterministic` debe ser `true` cuando use esta característica. Esta propiedad corresponde al modificador `/refout` de los compiladores de *vbc.exe* y *csc.exe*. |
| RemoveIntegerChecks | Visual Basic | Valor booleano que indica si se van a deshabilitar las comprobaciones de los errores de desbordamiento de enteros. El valor predeterminado es `false`. Esta propiedad es equivalente al modificador `/removeintchecks` del compilador de *vbc.exe*. |
| RootNamespace | Todas | Espacio de nombres raíz que se utilizará al asignar nombre a un recurso incrustado. Este espacio de nombres forma parte del nombre de manifiesto del recurso incrustado. |
| Satellite_AlgorithmId | .NET | Id. del algoritmo hash de *AL.exe* que se va a usar al crear los ensamblados satélite. |
| Satellite_BaseAddress | .NET | Dirección base que se utilizará al compilar los ensamblados satélite específicos de la referencia cultural mediante el destino `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | .NET | Nombre de compañía que se va a pasar a *AL.exe* durante la generación del ensamblado satélite. |
| Satellite_Configuration | .NET | Nombre de configuración que se va a pasar a *AL.exe* durante la generación del ensamblado satélite. |
| Satellite_Description | .NET | Texto de descripción que se va a pasar a *AL.exe* durante la generación del ensamblado satélite. |
| Satellite_EvidenceFile | .NET | Incrusta el archivo especificado en el ensamblado satélite con el nombre de recurso "Security.Evidence". |
| Satellite_FileVersion | .NET | Especifica una cadena para el campo File Version del ensamblado satélite. |
| Satellite_Flags | .NET | Especifica un valor para el campo Flags del ensamblado satélite. |
| Satellite_GenerateFullPaths | .NET | Hace que la tarea de compilación use rutas de acceso absolutas para los archivos indicados en un mensaje de error. |
| Satellite_LinkResource | .NET | Vincula los archivos de recursos especificados a un ensamblado satélite. |
| Satellite_MainEntryPoint | .NET | Especifica el nombre completo (es decir, class.method) del método que se usará como punto de entrada cuando un módulo se convierte en un archivo ejecutable durante la generación del ensamblado satélite. |
| Satellite_ProductName | .NET | Especifica una cadena para el campo Product del ensamblado satélite. |
| Satellite_ProductVersion | .NET | Especifica una cadena para el campo ProductVersion del ensamblado satélite. |
| Satellite_TargetType | .NET | Especifica el formato del archivo de salida del ensamblado satélite como "library", "exe" o "win". El valor predeterminado es "library". |
| Satellite_Title | .NET | Especifica una cadena para el campo Title del ensamblado satélite. |
| Satellite_Trademark | .NET | Especifica una cadena para el campo Trademark del ensamblado satélite. |
| Satellite_Version | .NET | Especifica la información de versión del ensamblado satélite. |
| Satellite_Win32Icon | .NET | Inserta un archivo de icono *.ico* en el ensamblado satélite. |
| Satellite_Win32Resource | .NET | Inserta un archivo de recursos ( *.res*) de Win32 en el ensamblado satélite. |
| SGenToolPath | .NET | Ruta de acceso opcional de la herramienta que indica dónde obtener *SGen.exe* si se reemplaza la versión actual de *SGen.exe*. |
| SGenUseProxyTypes | .NET | Valor booleano que indica si *SGen.exe* debe generar los tipos de proxy. Este valor solo se aplica si *GenerateSerializationAssemblies* está activado.<br /><br /> El destino de SGen usa esta propiedad para establecer la marca UseProxyTypes. Esta propiedad tiene el valor predeterminado true y no hay ninguna interfaz de usuario para cambiarlo. Para generar el ensamblado de serialización para tipos que no son de servicio web, agregue esta propiedad al archivo de proyecto y establézcala en false antes de importar *Microsoft.Common.Targets* o *C#/VB.targets*. |
| SkipInvalidConfigurations | Todas | Cuando es `true`, se genera una advertencia sobre las combinaciones de configuración y de plataforma no válidas, pero no interrumpe la compilación. Cuando es `false` o "undefined" (el valor predeterminado), se genera un error. |
| StartupObject | .NET | Especifica la clase o módulo que contiene el método Main o el procedimiento Main Sub. Esta propiedad es equivalente al modificador `/main` del compilador. |
| SubsystemVersion | .NET | Especifica la versión mínima del subsistema que el archivo ejecutable generado puede utilizar. Esta propiedad es equivalente al modificador `/subsystemversion` del compilador. Para obtener información sobre el valor predeterminado de esta propiedad, vea [-subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) o [-subsystemversion (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Versión de .NET Compact Framework necesaria para ejecutar la aplicación que se está compilando. Puede especificar esta propiedad para hacer referencia a ensamblados de .NET Framework concretos a los que no se pueda hacer referencia de ningún otro modo. |
| TargetFrameworkVersion | .NET | Versión de .NET Framework necesaria para ejecutar la aplicación que se está compilando. Puede especificar esta propiedad para hacer referencia a ensamblados de .NET Framework concretos a los que no se pueda hacer referencia de ningún otro modo. |
| TreatWarningsAsErrors | .NET | Parámetro booleano que, si es `true`, hace que todas las advertencias se traten como errores. Este parámetro es equivalente al modificador `/nowarn` del compilador. |
| UseHostCompilerIfAvailable | .NET | Parámetro booleano que, si es `true`, hace que la tarea de compilación utilice el objeto de compilador en proceso, si está disponible. Solo Visual Studio utiliza este parámetro. |
| Utf8Output | .NET | Parámetro booleano que, si es `true`, registra el resultado del compilador utilizando la codificación UTF-8. Este parámetro es equivalente al modificador `/utf8Output` del compilador. |
| VbcToolPath | Visual Basic | Ruta de acceso opcional que indica otra ubicación para *vbc.exe* si se reemplaza la versión actual de *vbc.exe*. |
| VbcVerbosity | Visual Basic | Especifica el nivel de detalle de los resultados del compilador de Visual Basic. Los valores válidos son "Quiet", "Normal" (valor predeterminado) o "Verbose". |
| VisualStudioVersion | Todas | Especifica la versión de Visual Studio en la que se debe ejecutar este proyecto. Si no se especifica esta propiedad, MSBuild la establece en un valor predeterminado razonable.<br /><br /> Esta propiedad se utiliza en varios tipos de proyecto para especificar el conjunto de destinos que se utilizan para la compilación. Si `ToolsVersion` se establece en 4.0 o superior para un proyecto, se usa `VisualStudioVersion` para especificar el subconjunto de herramientas que se va a utilizar. Para obtener más información, vea [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Especifica una lista de advertencias que se tratarán como errores. Este parámetro es equivalente al modificador `/warnaserror` del compilador. |
| WarningsNotAsErrors | .NET | Especifica una lista de advertencias que no se tratarán como errores. Este parámetro es equivalente al modificador `/warnaserror` del compilador. |
| Win32Manifest | .NET | Nombre del archivo manifiesto que se debe incrustar en el ensamblado final. Este parámetro es equivalente al modificador `/win32Manifest` del compilador. |
| Win32Resource | .NET | Nombre del archivo del recurso de Win32 que se va a incrustar en el ensamblado final. Este parámetro es equivalente al modificador `/win32resource` del compilador. |

## <a name="see-also"></a>Vea también

- [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)
- [Metadatos de elementos MSBuild comunes](common-msbuild-item-metadata.md)
- [Propiedades reservadas y conocidas de MSBuild](msbuild-reserved-and-well-known-properties.md)
- [Referencia de MSBuild para proyectos del SDK de .NET](/dotnet/core/project-sdk/msbuild-props)
