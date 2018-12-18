---
title: Propiedades comunes de proyectos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30371d20e240e5679664a687c5ca098519cac9c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300058"
---
# <a name="common-msbuild-project-properties"></a>Propiedades comunes de proyectos de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En la tabla siguiente se enumeran las propiedades utilizadas con frecuencia definidas en los archivos de proyecto de Visual Studio o incluidas en los archivos .targets que proporciona MSBuild.  
  
 Los archivos de proyecto de Visual Studio (.csproj, .vbproj, vcxproj, etc.) contienen código XML de MSBuild que se ejecuta cuando se compila un proyecto mediante el IDE. Normalmente, los proyectos importan uno o más archivos .targets para definir su proceso de compilación. Para obtener más información, vea [Archivos .Targets](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Lista de propiedades y parámetros comunes  
  
|Nombre de la propiedad o parámetro|Descripción|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|Especifica carpetas adicionales en las que los compiladores deben buscar ensamblados de referencia.|  
|AddModules|Hace que el compilador facilite toda la información de tipos presente en los archivos especificados al proyecto que se está compilando. Esta propiedad es equivalente al modificador `/addModules` del compilador.|  
|ALToolPath|Ruta de acceso donde se puede encontrar AL.exe. Esta propiedad invalida la versión actual de AL.exe para permitir el uso de una versión diferente.|  
|ApplicationIcon|Archivo de icono .ico que se va a pasar al compilador para incrustarlo como un icono de Win32. Esta propiedad es equivalente al modificador `/win32icon` de compilador.|  
|ApplicationManifest|Especifica la ruta de acceso del archivo que se utiliza para generar la información externa del manifiesto del Control de cuentas de usuario (UAC). Solo se aplica a los proyectos de Visual Studio que tienen como destino [!INCLUDE[windowsver](../includes/windowsver-md.md)].<br /><br /> En la mayoría de los casos, el manifiesto está incrustado. En cambio, si usa una implementación de COM sin registro o de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], el manifiesto puede ser un archivo externo que se instala junto con los ensamblados de la aplicación. Para obtener más información, vea la propiedad NoWin32Manifest en este tema.|  
|AssemblyOriginatorKeyFile|Especifica el archivo que se ha usado para firmar el ensamblado (.snk o .pfx) y se ha pasado a la [tarea ResolveKeySource](../msbuild/resolvekeysource-task.md) para generar la clave real con la que se ha firmado dicho ensamblado.|  
|AssemblySearchPaths|Lista de ubicaciones donde se realizarán las búsquedas durante la resolución de ensamblados de referencia en tiempo de compilación. El orden en que aparecen las rutas de acceso en esta lista es importante porque las rutas de acceso situadas antes en la lista tienen prioridad sobre las entradas posteriores.|  
|AssemblyName|Nombre del ensamblado resultante final una vez compilado el proyecto.|  
|BaseAddress|Especifica la dirección base del ensamblado resultante principal. Esta propiedad es equivalente al modificador `/baseaddress` del compilador.|  
|BaseOutputPath|Especifica la ruta de acceso base del archivo de salida. Si se establece, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] usará `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Ejemplo de sintaxis: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|Carpeta de nivel superior donde se crean todas las carpetas de resultados intermedios específicas de la configuración. El valor predeterminado es `obj\`. El siguiente código muestra un ejemplo: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Valor booleano que indica si las referencias del proyecto se compilan o limpian en paralelo cuando se utiliza [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] con varios procesadores. El valor predeterminado es `true`, que indica que los proyectos se compilarán en paralelo si el sistema tiene varios núcleos o procesadores.|  
|BuildProjectReferences|Valor booleano que indica si [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] compilará las referencias de proyecto. Establezca su valor en `false` si va a compilar su proyecto en el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; en caso contrario, use `true`.|  
|CleanFile|Nombre del archivo que se utilizará como "caché limpia". La memoria caché limpia es una lista de archivos generados que se eliminarán durante la operación de limpieza. El proceso de compilación coloca el archivo en la ruta de acceso de los resultados intermedios.<br /><br /> Esta propiedad solo especifica nombres de archivo sin información sobre su ruta de acceso.|  
|CodePage|Especifica la página de códigos que se va a utilizar para todos los archivos de código fuente en la compilación. Esta propiedad es equivalente al modificador `/codepage` del compilador.|  
|CompilerResponseFile|Archivo de respuesta opcional que se puede pasar a las tareas del compilador.|  
|Configuración|Configuración que está compilando, "Debug" o "Release".|  
|CscToolPath|Ruta de acceso de csc.exe, el compilador de [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|CustomBeforeMicrosoftCommonTargets|Nombre de un archivo de proyecto o archivo de destinos que se importará automáticamente antes de importar los destinos comunes.|  
|DebugSymbols|Valor booleano que indica si la compilación genera símbolos.<br /><br /> Si se establece **/p:DebugSymbols=false** en la línea de comandos, se deshabilita la generación de archivos de símbolos (.pdb) de la base de datos del programa.|  
|DefineConstants|Permite definir constantes condicionales para el compilador. Los pares símbolo-valor van separados por punto y coma, y se especifican con la siguiente sintaxis:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> Esta propiedad es equivalente al modificador `/define` de compilador.|  
|DefineDebug|Valor booleano que indica si desea definir la constante DEBUG.|  
|DefineTrace|Valor booleano que indica si desea definir la constante TRACE.|  
|DebugType|Define el nivel de información de depuración que desea generar. Los valores válidos son "full", "pdbonly" y "none".|  
|DelaySign|Valor booleano que indica si desea retrasar la firma del ensamblado en lugar de firmarlo completamente.|  
|DisabledWarnings|Suprime las advertencias especificadas. Solo debe especificarse la parte numérica del identificador de advertencia. Las advertencias múltiples se separan con punto y coma. Este parámetro corresponde al modificador `/nowarn` del compilador de vbc.exe.|  
|DisableFastUpToDateCheck|Valor booleano que solo se aplica a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. El administrador de compilación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utiliza un proceso denominado FastUpToDateCheck para determinar si es necesario recompilar un proyecto para actualizarlo. Este proceso es más rápido que utilizar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Al establecer la propiedad DisableFastUpToDateCheck en `true`, puede omitir el administrador de compilación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y obligarlo a usar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] para determinar si el proyecto está actualizado.|  
|DocumentationFile|Nombre del archivo que se genera como archivo de documentación XML. Este nombre solo incluye el nombre de archivo sin información sobre la ruta de acceso.|  
|ErrorReport|Especifica cómo debe el compilador documentar los errores internos del compilador. Los valores válidos son "prompt", "send" o "none". Esta propiedad es equivalente al modificador `/errorreport` del compilador.|  
|ExcludeDeploymentUrl|La [tarea GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) agrega una etiqueta deploymentProvider al manifiesto de implementación si el archivo de proyecto incluye alguno de los elementos siguientes:<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> Sin embargo, mediante ExcludeDeploymentUrl, puede evitar que la etiqueta deploymentProvider se agregue al manifiesto de implementación aunque se especifique alguna de las direcciones URL anteriores. Para ello, agregue la siguiente propiedad al archivo de proyecto:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` **Nota:** ExcludeDeploymentUrl no se expone en el IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y solo se puede establecer manualmente editando el archivo de proyecto. Al establecer esta propiedad, la publicación desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no resulta afectada; es decir, la etiqueta deploymentProvider se agregará de igual modo a la dirección URL especificada por PublishUrl.|  
|FileAlignment|Especifica, en bytes, dónde se alinean las secciones del archivo de salida. Los valores válidos son 512, 1024, 2048, 4096, 8192. Esta propiedad es equivalente al modificador `/filealignment` del compilador.|  
|FrameworkPathOverride|Especifica la ubicación de mscorlib.dll y microsoft.visualbasic.dll. Este parámetro es equivalente al modificador `/sdkpath` del compilador de vbc.exe.|  
|GenerateDocumentation|Parámetro booleano que indica si la compilación generará la documentación. Si es `true`, la compilación genera la información de documentación y la coloca en un archivo .xml junto con el nombre del archivo ejecutable o la biblioteca creada por la tarea de compilación.|  
|IntermediateOutputPath|Ruta de acceso intermedia completa de los resultados derivada de `BaseIntermediateOutputPath`, si no se especificó ninguna ruta de acceso. Por ejemplo, \obj\debug\\. Si se invalida esta propiedad, el valor de `BaseIntermediateOutputPath` no tiene ningún efecto.|  
|KeyContainerName|Nombre del contenedor de claves de nombre seguro.|  
|KeyOriginatorFile|Nombre del archivo de claves de nombre seguro.|  
|NoWin32Manifest|Determina si el compilador genera el manifiesto predeterminado de Win32 en el ensamblado resultante. El valor predeterminado `false` indica que el manifiesto de Win32 predeterminado se genera para todas las aplicaciones. Esta propiedad es equivalente al modificador `/nowin32manifest` del compilador de vbc.exe.|  
|ModuleAssemblyName|Nombre del ensamblado al que se incorporará el módulo compilado. Esta propiedad es equivalente al modificador `/moduleassemblyname` de compilador.|  
|NoLogo|Valor booleano que indica si se va a desactivar el logotipo del compilador. Esta propiedad es equivalente al modificador `/nologo` del compilador.|  
|NoStdLib|Valor booleano que indica si se debe evitar hacer referencia a la biblioteca estándar (mscorlib.dll). El valor predeterminado es `false`.|  
|NoVBRuntimeReference|Valor booleano que indica si el motor en tiempo de ejecución de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] (Microsoft.VisualBasic.dll) debe incluirse como una referencia en el proyecto.|  
|NoWin32Manifest|Valor booleano que indica si la información del manifiesto de Control de cuentas de usuario (UAC) se incrustará en el archivo ejecutable de la aplicación. Solo se aplica a los proyectos de Visual Studio que tienen como destino [!INCLUDE[windowsver](../includes/windowsver-md.md)]. En los proyectos que se implementan con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] y COM sin registro, se omite esta elemento. `False` (valor predeterminado) especifica que la información de manifiesto del Control de cuentas de usuario (UAC) se incrusta en el ejecutable de la aplicación. `True` especifica que la información de manifiesto de UAC no debe incrustarse.<br /><br /> Esta propiedad solo se aplica a los proyectos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que tienen como destino [!INCLUDE[windowsver](../includes/windowsver-md.md)]. En los proyectos que se implementan con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] y COM sin registro, se omite esta propiedad.<br /><br /> Solo debe agregar NoWin32Manifest si no quiere que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inserte información del manifiesto en el archivo ejecutable de la aplicación; este proceso se denomina *virtualización*. Para utilizar la virtualización, establezca `<ApplicationManifest>` junto con `<NoWin32Manifest>` del modo siguiente:<br /><br /> -   En los proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], quite el nodo `<ApplicationManifest>`. (En los proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `<NoWin32Manifest>` se omite cuando existe un nodo `<ApplicationManifest>`).<br />-   En los proyectos de [!INCLUDE[csprcs](../includes/csprcs-md.md)], establezca `<ApplicationManifest>` en `False` y `<NoWin32Manifest>` en `True`. (En los proyectos de [!INCLUDE[csprcs](../includes/csprcs-md.md)], `<ApplicationManifest>` invalida `<NoWin32Manifest>`).|  
|Optimize|Valor booleano que, cuando se establece en `true`, permite la optimización del compilador. Esta propiedad es equivalente al modificador `/optimize` del compilador.|  
|OptionCompare|Especifica la forma en que se realizan las comparaciones de cadenas. Los valores válidos son "binary" o "text". Esta propiedad es equivalente al modificador `/optioncompare` del compilador de vbc.exe.|  
|OptionExplicit|Valor booleano que, cuando se establece en `true`, requiere la declaración explícita de variables en el código fuente. Esta propiedad es equivalente al modificador `/optionexplicit` del compilador.|  
|OptionInfer|Valor booleano que, cuando se establece en `true`, permite la inferencia de tipos de variables. Esta propiedad es equivalente al modificador `/optioninfer` del compilador.|  
|OptionStrict|Valor booleano que, cuando se establece en `true`, hace que la tarea de compilación exija una semántica de tipos estricta para restringir las conversiones de tipos implícitas. Esta propiedad es equivalente al modificador `/optionstrict` del compilador de vbc.exe.|  
|OutputPath|Especifica la ruta de acceso del directorio de salida con respecto al directorio del proyecto, por ejemplo "bin\Debug".|  
|OutputType|Especifica el formato del archivo de salida. Este parámetro puede tener uno de los valores siguientes:<br /><br /> -   Library. Crea una biblioteca de códigos. (Valor predeterminado).<br />-   Exe. Crea una aplicación de consola.<br />-   Module. Crea un módulo.<br />-   Winexe. Crea un programa de Windows.<br /><br /> Esta propiedad es equivalente al modificador `/target` del compilador de vbc.exe.|  
|OverwriteReadOnlyFiles|Valor booleano que indica si desea que la compilación sobrescriba los archivos de solo lectura o produzca un error.|  
|PdbFile|Nombre del archivo .pdb que va a emitir. Esta propiedad es equivalente al modificador `/pdb` del compilador de csc.exe.|  
|Plataforma|Sistema operativo para el que se está compilando. Los valores válidos son "Any CPU", "x 86" y "x 64".|  
|RemoveIntegerChecks|Valor booleano que indica si se van a deshabilitar las comprobaciones de los errores de desbordamiento de enteros. El valor predeterminado es `false`. Esta propiedad es equivalente al modificador `/removeintchecks` del compilador de vbc.exe.|  
|SGenUseProxyTypes|Valor booleano que indica si SGen.exe debe generar los tipos de proxy.<br /><br /> El destino de SGen usa esta propiedad para establecer la marca UseProxyTypes. Esta propiedad tiene el valor predeterminado true y no hay ninguna interfaz de usuario para cambiarlo. Para generar el ensamblado de serialización para tipos que no son de servicio web, agregue esta propiedad al archivo de proyecto y establézcalo en false antes de importar Microsoft.Common.Targets o C#/VB.targets.|  
|SGenToolPath|Ruta de acceso opcional de la herramienta que indica dónde obtener SGen.exe cuando se invalida la versión actual de SGen.exe.|  
|StartupObject|Especifica la clase o módulo que contiene el método Main o el procedimiento Main Sub. Esta propiedad es equivalente al modificador `/main` del compilador.|  
|ProcessorArchitecture|Arquitectura de procesador utilizada cuando se resuelven las referencias de ensamblado. Los valores válidos son "msil", "x86", "amd64" o "ia64".|  
|RootNamespace|Espacio de nombres raíz que se utilizará al asignar nombre a un recurso incrustado. Este espacio de nombres forma parte del nombre de manifiesto del recurso incrustado.|  
|Satellite_AlgorithmId|Id. del algoritmo hash de AL.exe que se utilizará al crear los ensamblados satélite.|  
|Satellite_BaseAddress|Dirección base que se utilizará al compilar los ensamblados satélite específicos de la referencia cultural mediante el destino `CreateSatelliteAssemblies`.|  
|Satellite_CompanyName|Nombre de la compañía que se pasará a AL.exe durante la generación del ensamblado satélite.|  
|Satellite_Configuration|Nombre de la configuración que se pasará a AL.exe durante la generación del ensamblado satélite.|  
|Satellite_Description|Texto de descripción que se pasará a AL.exe durante la generación del ensamblado satélite.|  
|Satellite_EvidenceFile|Incrusta el archivo especificado en el ensamblado satélite con el nombre de recurso "Security.Evidence".|  
|Satellite_FileVersion|Especifica una cadena para el campo File Version del ensamblado satélite.|  
|Satellite_Flags|Especifica un valor para el campo Flags del ensamblado satélite.|  
|Satellite_GenerateFullPaths|Hace que la tarea de compilación use rutas de acceso absolutas para los archivos indicados en un mensaje de error.|  
|Satellite_LinkResource|Vincula los archivos de recursos especificados a un ensamblado satélite.|  
|Satellite_MainEntryPoint|Especifica el nombre completo (es decir, class.method) del método que se usará como punto de entrada cuando un módulo se convierte en un archivo ejecutable durante la generación del ensamblado satélite.|  
|Satellite_ProductName|Especifica una cadena para el campo Product del ensamblado satélite.|  
|Satellite_ProductVersion|Especifica una cadena para el campo ProductVersion del ensamblado satélite.|  
|Satellite_TargetType|Especifica el formato del archivo de salida del ensamblado satélite como "library", "exe" o "win". El valor predeterminado es "library".|  
|Satellite_Title|Especifica una cadena para el campo Title del ensamblado satélite.|  
|Satellite_Trademark|Especifica una cadena para el campo Trademark del ensamblado satélite.|  
|Satellite_Version|Especifica la información de versión del ensamblado satélite.|  
|Satellite_Win32Icon|Inserta un archivo de icono .ico en el ensamblado satélite.|  
|Satellite_Win32Resource|Inserta un archivo de recursos (.res) de Win32 en el ensamblado satélite.|  
|SubsystemVersion|Especifica la versión mínima del subsistema que el archivo ejecutable generado puede utilizar. Esta propiedad es equivalente al modificador `/subsystemversion` del compilador. Para obtener más información sobre el valor predeterminado de esta propiedad, vea [/subsystemversion (Visual Basic)](http://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) o [/subsystemversion (Opciones del compilador de C#)](http://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445).|  
|TargetCompactFramework|Versión de .NET Compact Framework necesaria para ejecutar la aplicación que se está compilando. Puede especificar esta propiedad para hacer referencia a ensamblados de .NET Framework concretos a los que no se pueda hacer referencia de ningún otro modo.|  
|TargetFrameworkVersion|Versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] necesaria para ejecutar la aplicación que se está compilando. Puede especificar esta propiedad para hacer referencia a ensamblados de .NET Framework concretos a los que no se pueda hacer referencia de ningún otro modo.|  
|TreatWarningsAsErrors|Parámetro booleano que, si es `true`, hace que todas las advertencias se traten como errores. Este parámetro es equivalente al modificador `/nowarn` del compilador.|  
|UseHostCompilerIfAvailable|Parámetro booleano que, si es `true`, hace que la tarea de compilación utilice el objeto de compilador en proceso, si está disponible. Solo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utiliza este parámetro.|  
|Utf8Output|Parámetro booleano que, si es `true`, registra el resultado del compilador utilizando la codificación UTF-8. Este parámetro es equivalente al modificador `/utf8Output` del compilador.|  
|VbcToolPath|Ruta de acceso opcional que indica otra ubicación para vbc.exe cuando se invalida la versión actual de vbc.exe.|  
|VbcVerbosity|Especifica el nivel de detalle de los resultados del compilador de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Los valores válidos son "Quiet", "Normal" (valor predeterminado) o "Verbose".|  
|VisualStudioVersion|Especifica la versión de Visual Studio en la que se debe ejecutar este proyecto. Si no se especifica esta propiedad, MSBuild la establece en un valor predeterminado razonable.<br /><br /> Esta propiedad se utiliza en varios tipos de proyecto para especificar el conjunto de destinos que se utilizan para la compilación. Si `ToolsVersion` se establece en 4.0 o superior para un proyecto, se usa `VisualStudioVersion` para especificar el subconjunto de herramientas que se va a utilizar. Para obtener más información, vea [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Especifica una lista de advertencias que se tratarán como errores. Este parámetro es equivalente al modificador `/warnaserror` del compilador.|  
|WarningsNotAsErrors|Especifica una lista de advertencias que no se tratarán como errores. Este parámetro es equivalente al modificador `/warnaserror` del compilador.|  
|Win32Manifest|Nombre del archivo manifiesto que se debe incrustar en el ensamblado final. Este parámetro es equivalente al modificador `/win32Manifest` del compilador.|  
|Win32Resource|Nombre del archivo del recurso de Win32 que se va a incrustar en el ensamblado final. Este parámetro es equivalente al modificador `/win32resource` del compilador.|  
  
## <a name="see-also"></a>Vea también  
 [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)



