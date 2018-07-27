---
title: Vincular tarea | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c06e9a92eb6b6df82e4f45790b877286e6c52725
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081714"
---
# <a name="link-task"></a>Vincular tarea
Incluye la herramienta del enlazador de Visual C++, *link.exe*. La herramienta del enlazador vincula bibliotecas y archivos de objeto de formato de archivo de objeto común (COFF) para crear un archivo ejecutable (*.exe*) o una biblioteca de vínculos dinámicos (DLL). Para obtener más información, vea [Opciones del enlazador](/cpp/build/reference/linker-options).  
  
## <a name="parameters"></a>Parámetros  
 A continuación se describen los parámetros de la tarea **Link**. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
-   **AdditionalDependencies**  
  
     Parámetro **String[]** opcional.  
  
     Especifica una lista de archivos de entrada para agregar al comando.  
  
     Para obtener más información, vea [Archivos de entrada de LINK](/cpp/build/reference/link-input-files).  
  
-   **AdditionalLibraryDirectories**  
  
     Parámetro **String[]** opcional.  
  
     Reemplaza la ruta de acceso a la biblioteca de entorno. Especifique un nombre de directorio.  
  
     Para obtener más información, consulte [/LIBPATH (Directorios de bibliotecas adicionales)](/cpp/build/reference/libpath-additional-libpath).  
  
-   **AdditionalManifestDependencies**  
  
     Parámetro **String[]** opcional.  
  
     Especifica los atributos que se colocarán en la sección `dependency` del archivo de manifiesto.  
  
     Para obtener más información, vea [/MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Vea también [Publisher configuration files](https://docs.microsoft.com/en-us/windows/desktop/SbsCs/publisher-configuration-files) (Archivos de configuración del publicador).  
  
-   **AdditionalOptions**  
  
     Parámetro **String** opcional.  
  
     Una lista de opciones del enlazador especificada en la línea de comandos. Por ejemplo, /\<option1> /\<option2> /\<option#>. Utilice este parámetro para especificar opciones del enlazador que no están representadas por ningún otro parámetro de la tarea **Link**.  
  
     Para obtener más información, vea [Opciones del enlazador](/cpp/build/reference/linker-options).  
  
-   **AddModuleNamesToAssembly**  
  
     Parámetro **String[]** opcional.  
  
     Agrega una referencia de módulo en un ensamblado.  
  
     Para obtener más información, vea [/ASSEMBLYMODULE (Agregar un módulo MSIL al ensamblado)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).  
  
-   **AllowIsolation**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, hace que el sistema operativo realice cargas y búsquedas de manifiestos. Si `false`, indica que los archivos DLL se cargan como si no hubiera ningún manifiesto.  
  
     Para obtener más información, vea [/ALLOWISOLATION (Manifestar bucle)](/cpp/build/reference/allowisolation-manifest-lookup).  
  
-   **AssemblyDebug**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, emite el atributo **DebuggableAttribute**, junto con el seguimiento de la información de depuración, y desactiva las optimizaciones JIT. Si `false`, emite el atributo **DebuggableAttribute**, pero desactiva el seguimiento de la información de depuración y activa las optimizaciones JIT.  
  
     Para obtener más información, consulte [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
-   **AssemblyLinkResource**  
  
     Parámetro **String[]** opcional.  
  
     Crea un vínculo a un recurso de .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida. Especifique el nombre del recurso.  
  
     Para obtener más información, vea [/ASSEMBLYLINKRESOURCE (Vincular a recursos de .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).  
  
-   **AttributeFileTracking**  
  
     Parámetro **Boolean** implícito.  
  
     Permite un seguimiento más a fondo de los archivos para capturar el comportamiento incremental del vínculo. Siempre devuelve `true`.  
  
-   **BaseAddress**  
  
     Parámetro **String** opcional.  
  
     Establece una dirección base para el programa o el archivo DLL que se compila. Especifique `{address[,size] | @filename,key}`.  
  
     Para obtener más información, vea [/BASE (Dirección base)](/cpp/build/reference/base-base-address).  
  
-   **BuildingInIDE**  
  
     Parámetro **Boolean** opcional.  
  
     Si es verdadero, indica que el IDE invoca MSBuild. De lo contrario, indica que MSBuild se invoca desde la línea de comandos.  
  
     Este parámetro no tiene ninguna opción del enlazador equivalente.  
  
-   **CLRImageType**  
  
     Parámetro **String** opcional.  
  
     Establece el tipo de una imagen de Common Language Runtime (CLR).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **Default** - *\<none>*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
    -   **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
    Para obtener más información, vea [/CLRIMAGETYPE (Especificar tipo de imagen CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).  
  
-   **CLRSupportLastError**  
  
     Parámetro **String** opcional.  
  
     Conserva el último código de error de las funciones llamadas a través del mecanismo P/Invoke.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **Enabled** - **/CLRSupportLastError**  
  
    -   **Disabled** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Para obtener más información, vea [/CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).  
  
-   **CLRThreadAttribute**  
  
     Parámetro **String** opcional.  
  
     Especifica explícitamente el atributo de subprocesamiento del punto de entrada del programa CLR.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
    -   **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Para obtener más información, vea [/CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Parámetro **Boolean** opcional.  
  
     Especifica si el enlazador aplicará **SuppressUnmanagedCodeSecurityAttribute** a las llamadas P/Invoke generadas por enlazador a partir de código administrado en archivos DLL nativos.  
  
    Para obtener más información, consulte [/CLRUNMANAGEDCODECHECK (Agregar SupressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute).  
  
-   **CreateHotpatchableImage**  
  
     Parámetro **String** opcional.  
  
     Prepara una imagen para aplicar una revisión activa.  
  
     Especifique uno de los valores siguientes, que corresponde a una opción del enlazador.  
  
    -   **Enabled** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Para obtener más información, vea [/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).  
  
-   **DataExecutionPrevention**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica que se ha probado si un ejecutable es compatible con la característica Prevención de ejecución de datos de Windows.  
  
     Para obtener más información, consulte [/NXCOMPAT (Compatible con Prevención de ejecución de datos)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).  
  
-   **DelayLoadDLLs**  
  
     Parámetro **String[]** opcional.  
  
     Este parámetro causa la *carga retrasada* de archivos DLL. Especifique el nombre de un archivo DLL cuya carga se desea retrasar.  
  
     Para obtener más información, vea [/DELAYLOAD (Retrasar importación de carga)](/cpp/build/reference/delayload-delay-load-import).  
  
-   **DelaySign**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, firma parcialmente un ensamblado. De forma predeterminada, el valor es `false`.  
  
     Para obtener más información, vea [/DELAYSIGN (Firmar parcialmente un ensamblado)](/cpp/build/reference/delaysign-partially-sign-an-assembly).  
  
-   **Driver**  
  
     Parámetro **String** opcional.  
  
     Especifique este parámetro para compilar un controlador de modo kernel de Windows NT.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Driver** - **/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** -   **/DRIVER: WDM**  
  
    Para obtener más información, vea [/DRIVER (Controlador de modo kernel de Windows NT)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).  
  
-   **EmbedManagedResourceFile**  
  
     Parámetro **String[]** opcional.  
  
     Inserta un archivo de recursos en un ensamblado. Especifique el nombre de archivo de recursos necesario. Opcionalmente, especifique el nombre lógico (usado para cargar el recurso) y la opción **PRIVATE** (que indica en el manifiesto del ensamblado que el archivo de recursos es privado).  
  
     Para obtener más información, vea [/ASSEMBLYRESOURCE (Incrustar un recurso administrado)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).  
  
-   **EnableCOMDATFolding**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, permite un plegamiento idéntico de COMDAT.  
  
     Para obtener más información, consulte el argumento `ICF[= iterations]` de [/OPT (Optimizaciones)](/cpp/build/reference/opt-optimizations).  
  
-   **EnableUAC**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica si la información de Control de cuentas de usuario (UAC) debe insertarse en el manifiesto del programa.  
  
     Para obtener más información, consulte [/MANIFESTUAC (Insertar información de UAC en el manifiesto)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **EntryPointSymbol**  
  
     Parámetro **String** opcional.  
  
     Especifica una función de punto de entrada como dirección inicial de un archivo *.exe* o DLL. Especifique un nombre de función como el valor del parámetro.  
  
     Para obtener más información, vea [/ENTRY (Símbolo de punto de entrada)](/cpp/build/reference/entry-entry-point-symbol).  
  
-   **FixedBaseAddress**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea un programa o un archivo DLL que solo se puede cargar en su dirección base preferida.  
  
     Para obtener más información, vea [/FIXED (Dirección base fija)](/cpp/build/reference/fixed-fixed-base-address).  
  
-   **ForceFileOutput**  
  
     Parámetro **String** opcional.  
  
     Indica al enlazador que cree un archivo *.exe* o DLL válido aunque se haga referencia a un símbolo pero no esté definido, o bien esté definido varias veces.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Enabled** - **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
    -   **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
    Para obtener más información, vea [/FORCE (Forzar resultados de archivo)](/cpp/build/reference/force-force-file-output).  
  
-   **ForceSymbolReferences**  
  
     Parámetro **String[]** opcional.  
  
     Este parámetro indica al enlazador que agregue un símbolo especificado a la tabla de símbolos.  
  
     Para obtener más información, vea [/INCLUDE (Forzar referencias de símbolos)](/cpp/build/reference/include-force-symbol-references).  
  
-   **FunctionOrder**  
  
     Parámetro **String** opcional.  
  
     Este parámetro optimiza su programa colocando las funciones empaquetadas especificadas (COMDAT) en la imagen en un orden predeterminado.  
  
     Para obtener más información, vea [/ORDER (Colocar las funciones en orden)](/cpp/build/reference/order-put-functions-in-order).  
  
-   **GenerateDebugInformation**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, crea información de depuración para el archivo *.exe* o DLL.  
  
     Para obtener más información, vea [/DEBUG (Generar información de depuración)](/cpp/build/reference/debug-generate-debug-info).  
  
-   **GenerateManifest**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea un archivo de manifiesto en paralelo.  
  
     Para obtener más información, vea [/MANIFEST (Crear el manifiesto del ensamblado simultáneo)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).  
  
-   **GenerateMapFile**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea un *archivo de asignación*. La extensión de nombre de archivo del archivo de asignación es *.map*.  
  
     Para obtener más información, vea [/MAP (Generar archivo de asignaciones)](/cpp/build/reference/map-generate-mapfile).  
  
-   **HeapCommitSize**  
  
     Parámetro **String** opcional.  
  
     Especifica la cantidad de memoria física en el montón que se debe asignar de una sola vez.  
  
     Para obtener más información, vea el argumento `commit` en [/HEAP (Establecer el tamaño del montón)](/cpp/build/reference/heap-set-heap-size). Consulte también el parámetro **HeapReserveSize**.  
  
-   **HeapReserveSize**  
  
     Parámetro **String** opcional.  
  
     Especifica el tamaño total asignado al montón en la memoria virtual.  
  
     Para obtener más información, vea el argumento `reserve` en [/HEAP (Establecer el tamaño del montón)](/cpp/build/reference/heap-set-heap-size). Consulte también el parámetro **HeapCommitSize** en esta tabla.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al enlazador que quite una o varias bibliotecas predeterminadas de la lista de bibliotecas en la que realiza búsquedas cuando resuelve referencias externas.  
  
     Para obtener más información, vea [/NODEFAULTLIB (Omitir bibliotecas)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **IgnoreEmbeddedIDL**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, especifica que no se debe procesar ningún atributo IDL del código fuente en un archivo *.idl*.  
  
     Para obtener más información, vea [/IGNOREIDL (No procesar atributos en MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).  
  
-   **IgnoreImportLibrary**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica que la biblioteca de importación generada por esta configuración no se importará en los proyectos dependientes.  
  
     Este parámetro no se corresponde con ninguna opción del enlazador.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Parámetro **String[]** opcional.  
  
     Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán. Separe varias bibliotecas mediante punto y coma.  
  
     Para obtener más información, vea [/NODEFAULTLIB (Omitir bibliotecas)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, el enlazador genera una imagen solo si también puede generar una tabla de los controladores de excepciones seguros de la imagen.  
  
     Para obtener más información, vea [/SAFESEH (La imagen tiene controladores de excepciones seguros)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).  
  
-   **ImportLibrary**  
  
     Nombre de la biblioteca de importación especificada por el usuario que reemplaza el nombre de biblioteca predeterminado.  
  
     Para obtener más información, vea [/IMPLIB (Asignar nombre a la biblioteca de importación)](/cpp/build/reference/implib-name-import-library).  
  
-   **KeyContainer**  
  
     Parámetro **String** opcional.  
  
     Contenedor que contiene la clave de un ensamblado firmado.  
  
     Para obtener más información, vea [/KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Consulte también el parámetro **KeyFile** en esta tabla.  
  
-   **KeyFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un archivo que contiene la clave de un ensamblado firmado.  
  
     Para obtener más información, vea [/KEYFILE (Especificar una clave o un par de claves para firmar un ensamblado)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Consulte también el parámetro **KeyContainer**.  
  
-   **LargeAddressAware**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, la aplicación puede controlar direcciones mayores de 2 gigabytes.  
  
     Para obtener más información, vea [/LARGEADDRESSAWARE (Procesar direcciones largas)](/cpp/build/reference/largeaddressaware-handle-large-addresses).  
  
-   **LinkDLL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, compila un archivo DLL como el archivo de salida principal.  
  
     Para obtener más información, consulte [/DLL (compilar un archivo DLL)](/cpp/build/reference/dll-build-a-dll).  
  
-   **LinkErrorReporting**  
  
     Parámetro **String** opcional.  
  
     Permite proporcionar directamente a Microsoft información sobre los errores internos del compilador (ICE).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NoErrorReport** - **/ERRORREPORT:NONE**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** - **/ERRORREPORT:SEND**  
  
    Para obtener más información, vea [/ERRORREPORT (Informar de los errores del compilador)](/cpp/build/reference/errorreport-report-internal-linker-errors).  
  
-   **LinkIncremental**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, controla la vinculación incremental.  
  
     Para obtener más información, vea [/INCREMENTAL (Vincular de forma incremental)](/cpp/build/reference/incremental-link-incrementally).  
  
-   **LinkLibraryDependencies**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, especifica que los resultados de la biblioteca de las dependencias del proyecto se vinculan automáticamente.  
  
     Este parámetro no se corresponde con ninguna opción del enlazador.  
  
-   **LinkStatus**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica que el enlazador debe mostrar un indicador de progreso que muestra qué porcentaje del vínculo está completado.  
  
     Para obtener más información, vea el argumento `STATUS` de [/LTCG (Generación de código en tiempo de enlace)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **LinkTimeCodeGeneration**  
  
     Parámetro **String** opcional.  
  
     Especifica opciones para la optimización guiada por perfiles.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** - *\<none>*  
  
    -   **UseLinkTimeCodeGeneration** - **LTCG**  
  
    -   **PGInstrument** - **/LTCG:PGInstrument**  
  
    -   **PGOptimization** - **/LTCG:PGOptimize**  
  
    -   **PGUpdate**  
  
         \- **/LTCG:PGUpdate**  
  
    Para obtener más información, vea [/LTCG (Generación de código en tiempo de enlace)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **ManifestFile**  
  
     Parámetro **String** opcional.  
  
     Cambia el nombre de archivo de manifiesto predeterminado por el nombre de archivo especificado.  
  
     Para obtener más información, vea [/MANIFESTFILE (Nombre del archivo de manifiesto)](/cpp/build/reference/manifestfile-name-manifest-file).  
  
-   **MapExports**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al enlazador que incluya funciones exportadas en un archivo de asignación.  
  
     Para obtener más información, vea el argumento `EXPORTS` de [/MAPINFO (Incluir información en el archivo de asignaciones)](/cpp/build/reference/mapinfo-include-information-in-mapfile).  
  
-   **MapFileName**  
  
     Parámetro **String** opcional.  
  
     Cambia el nombre de archivo de asignación predeterminado por el nombre de archivo especificado.  
  
-   **MergedIDLBaseFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de archivo y la extensión de nombre de archivo del archivo *.idl*.  
  
     Para obtener más información, vea [/IDLOUT (Dar nombre a los archivos de resultados de MIDL)](/cpp/build/reference/idlout-name-midl-output-files).  
  
-   **MergeSections**  
  
     Parámetro **String** opcional.  
  
     Combina secciones en una imagen. Especifique `from-section=to-section`.  
  
     Para obtener más información, vea [/MERGE (Combinar secciones)](/cpp/build/reference/merge-combine-sections).  
  
-   **MidlCommandFile**  
  
     Parámetro **String** opcional.  
  
     Especifique el nombre de un archivo que contiene las opciones de línea de comandos de MIDL.  
  
     Para obtener más información, vea [/MIDL (Especificar las opciones de la línea de comandos de MIDL)](/cpp/build/reference/midl-specify-midl-command-line-options).  
  
-   **MinimumRequiredVersion**  
  
     Parámetro **String** opcional.  
  
     Especifica la versión mínima requerida del subsistema. Los argumentos son números decimales comprendidos en el intervalo de 0 a 65535.  
  
-   **ModuleDefinitionFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de un [archivo de definición de módulos](/cpp/build/reference/module-definition-dot-def-files).  
  
     Para obtener más información, vea [/DEF (Especificar un archivo de definición de módulos)](/cpp/build/reference/def-specify-module-definition-file).  
  
-   **MSDOSStubFileName**  
  
     Parámetro **String** opcional.  
  
     Adjunta el programa de código auxiliar de MS-DOS especificado a un programa Win32.  
  
     Para obtener más información, vea [/STUB (Nombre del archivo de código auxiliar de MS-DOS)](/cpp/build/reference/stub-ms-dos-stub-file-name).  
  
-   **NoEntryPoint**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica un archivo DLL solo de recursos.  
  
     Para obtener más información, vea [/NOENTRY (Sin punto de entrada)](/cpp/build/reference/noentry-no-entry-point).  
  
-   **ObjectFiles**  
  
     Parámetro **String[]** implícito.  
  
     Especifica los archivos objeto vinculados.  
  
-   **OptimizeReferences**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, elimina las funciones o los datos a los que nunca se hace referencia.  
  
     Para obtener más información, consulte el argumento `REF` en [/OPT (Optimizaciones)](/cpp/build/reference/opt-optimizations).  
  
-   **OutputFile**  
  
     Parámetro **String** opcional.  
  
     Invalida el nombre y la ubicación predeterminados del programa que crea el enlazador.  
  
     Para obtener más información, vea [/OUT (Nombre del archivo de resultados)](/cpp/build/reference/out-output-file-name).  
  
-   **PerUserRedirection**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, y la opción Registrar resultados está activada, hace que las escrituras en la clave del registro **HKEY_CLASSES_ROOT** se redirijan a **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     Parámetro `ITaskItem[]` opcional.  
  
     Define una matriz de elementos de elementos de salida del preprocesador que las tareas pueden consumir y emitir.  
  
-   **PreventDllBinding**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, indica a *Bind.exe* que la imagen vinculada no se debe enlazar.  
  
     Para obtener más información, vea [/ALLOWBIND (Evitar el enlace de archivos DLL)](/cpp/build/reference/allowbind-prevent-dll-binding).  
  
-   **Profile**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, produce un archivo de salida que se puede utilizar con el generador de perfiles de **Herramientas de rendimiento**.  
  
     Para obtener más información, vea [/PROFILE (Generador de perfiles de Herramientas de rendimiento)](/cpp/build/reference/profile-performance-tools-profiler).  
  
-   **ProfileGuidedDatabase**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo *.pgd* que se va a usar para almacenar información sobre el programa en ejecución  
  
     Para obtener más información, vea [/PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).  
  
-   **ProgramDatabaseFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre para la base de datos de programa (PDB) que crea el enlazador.  
  
     Para obtener más información, vea [/PDB (Utilizar la base de datos de programa)](/cpp/build/reference/pdb-use-program-database).  
  
-   **RandomizedBaseAddress**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, genera una imagen ejecutable que se puede reorganizar aleatoriamente en el momento de la carga mediante la característica de *selección aleatoria del diseño del espacio de direcciones* (ASLR) de Windows.  
  
     Para obtener más información, consulte [/DYNAMICBASE (utilizar selección aleatoria del diseño del espacio de direcciones)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).  
  
-   **RegisterOutput**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, registra la salida principal de esta compilación.  
  
-   **SectionAlignment**  
  
     Parámetro **Integer** opcional.  
  
     Especifica la alineación de cada sección en el espacio de direcciones lineales del programa. El valor del parámetro es un número de unidad de bytes y una potencia de dos.  
  
     Para obtener más información, vea [/ALIGN (Alineación de sección)](/cpp/build/reference/align-section-alignment).  
  
-   **SetChecksum**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, establece la suma de comprobación en el encabezado de un archivo *.exe*.  
  
     Para obtener más información, vea [/RELEASE (Establecer la suma de comprobación)](/cpp/build/reference/release-set-the-checksum).  
  
-   **ShowProgress**  
  
     Parámetro **String** opcional.  
  
     Especifica el nivel de detalle de los informes de progreso de la operación de vinculación.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NotSet** - *\<none>*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/VERBOSE:Lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Para obtener más información, vea [/VERBOSE (Mostrar mensajes de progreso)](/cpp/build/reference/verbose-print-progress-messages).  
  
-   **Sources**  
  
     Parámetro `ITaskItem[]` requerido.  
  
     Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.  
  
-   **SpecifySectionAttributes**  
  
     Parámetro **String** opcional.  
  
     Especifica los atributos de una sección. Esto reemplaza los atributos que se establecieron cuando se compiló el archivo *.obj* para la sección.  
  
     Para obtener más información, vea [/SECTION (Especificar los atributos de la sección)](/cpp/build/reference/section-specify-section-attributes).  
  
-   **StackCommitSize**  
  
     Parámetro **String** opcional.  
  
     Especifica la cantidad de memoria física de cada asignación cuando se asigna memoria adicional.  
  
     Para obtener más información, vea el argumento `commit` de [/STACK (Asignaciones de la pila)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StackReserveSize**  
  
     Parámetro **String** opcional.  
  
     Especifica el tamaño total asignado a la pila en la memoria virtual.  
  
     Para obtener más información, vea el argumento `reserve` de [/STACK (Asignaciones de la pila)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StripPrivateSymbols**  
  
     Parámetro **String** opcional.  
  
     Crea un segundo archivo de base de datos (PDB) de programa que omite los símbolos que no quiere distribuir a sus clientes. Especifique el nombre del segundo archivo PDB.  
  
     Para obtener más información, vea [/PDBSTRIPPED (Quitar símbolos privados)](/cpp/build/reference/pdbstripped-strip-private-symbols).  
  
-   **SubSystem**  
  
     Parámetro **String** opcional.  
  
     Especifica el entorno del ejecutable.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Console** - **/SUBSYSTEM:CONSOLE**  
  
    -   **Windows** - **/SUBSYSTEM:WINDOWS**  
  
    -   **Native** - **/SUBSYSTEM:NATIVE**  
  
    -   **EFI Application** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **EFI Boot Service Driver** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Para obtener más información, vea [/SUBSYSTEM (Especificar subsistema)](/cpp/build/reference/subsystem-specify-subsystem).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al enlazador que no incluya una tabla de direcciones de importación (IAT) enlazable en la imagen final.  
  
     Para obtener más información, vea el argumento `NOBIND` de [/DELAY (Configuración de las importaciones de carga retrasada)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica a la función de aplicación auxiliar de carga retrasada que admita la descarga explícita del archivo DLL.  
  
     Para obtener más información, vea el argumento `UNLOAD` de [/DELAY (Configuración de las importaciones de carga retrasada)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SuppressStartupBanner**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
     Para obtener más información, vea [/NOLOGO (Suprimir el titular de inicio) (Enlazador)](/cpp/build/reference/nologo-suppress-startup-banner-linker).  
  
-   **SwapRunFromCD**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al sistema operativo que copie primero la salida del enlazador a un archivo de intercambio y ejecute después la imagen desde allí.  
  
     Para obtener más información, vea el argumento `CD` de [/SWAPRUN (Cargar resultados del enlazador en el archivo de intercambio)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Consulte también el parámetro **SwapRunFromNET**.  
  
-   **SwapRunFromNET**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al sistema operativo que copie primero la salida del enlazador a un archivo de intercambio y ejecute después la imagen desde allí.  
  
     Para obtener más información, vea el argumento `NET` de [/SWAPRUN (Cargar resultados del enlazador en el archivo de intercambio)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Consulte también el parámetro **SwapRunFromCD** en esta tabla.  
  
-   **TargetMachine**  
  
     Parámetro **String** opcional.  
  
     Especifica la plataforma de destino para el programa o DLL.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NotSet** - *\<none>*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X64**  
  
    -   **MachineX86** - **/MACHINE:X86**  
  
    Para obtener más información, vea [/MACHINE (Especificar la plataforma de destino)](/cpp/build/reference/machine-specify-target-platform).  
  
-   **TerminalServerAware**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, establece una marca en el campo IMAGE_OPTIONAL_HEADER DllCharacteristics del encabezado opcional de la imagen del programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.  
  
     Para obtener más información, vea [/TSAWARE (Crear una aplicación que reconozca Terminal Server)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).  
  
-   **TrackerLogDirectory**  
  
     Parámetro **String** opcional.  
  
     Especifica el directorio del registro de seguimiento.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, hace que no se genere ningún archivo de salida si el enlazador genera una advertencia.  
  
     Para obtener más información, vea [/WX (Tratar advertencias del enlazador como errores)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).  
  
-   **TurnOffAssemblyGeneration**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea una imagen para el archivo de salida actual sin un ensamblado de .NET Framework.  
  
     Para obtener más información, vea [/NOASSEMBLY (Crear un módulo MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).  
  
-   **TypeLibraryFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de archivo y la extensión de nombre de archivo del archivo *.tlb*. Especifique un nombre de archivo o una ruta de acceso y un nombre de archivo.  
  
     Para obtener más información, vea [/TLBOUT (Dar nombre a un archivo .TLB)](/cpp/build/reference/tlbout-name-dot-tlb-file).  
  
-   **TypeLibraryResourceID**  
  
     Parámetro **Integer** opcional.  
  
     Designa un valor especificado por el usuario para una biblioteca de tipos creada por el enlazador. Especifique un valor entre 1 y 65535.  
  
     Para obtener más información, vea [/TLBID (Especificar un identificador de recursos para una biblioteca de tipos)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).  
  
-   **UACExecutionLevel**  
  
     Parámetro **String** opcional.  
  
     Especifica el nivel de ejecución solicitado para la aplicación cuando se ejecuta con Control de cuentas de usuario.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator** - `level='requireAdministrator'`  
  
    Para obtener más información, consulte el argumento `level` de [/MANIFESTUAC (insertar información de UAC en el manifiesto)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UACUIAccess**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, la aplicación omite los niveles de protección de la interfaz de usuario y dirige las entradas de datos a ventanas con un nivel de permisos superior en el escritorio; de lo contrario, `false`.  
  
     Para obtener más información, consulte el argumento `uiAccess` de [/MANIFESTUAC (insertar información de UAC en el manifiesto)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UseLibraryDependencyInputs**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, se utilizan las entradas a la herramienta bibliotecario en lugar del propio archivo de biblioteca cuando se vinculan resultados de biblioteca de dependencias del proyecto.  
  
-   **Versión**  
  
     Parámetro **String** opcional.  
  
     Ponga un número de versión en el encabezado del archivo *.exe* o *.dll*. Especifique "`major[.minor]`". Los argumentos `major` y `minor` son números decimales comprendidos entre 0 y 65535.  
  
     Para obtener más información, vea [/VERSION (Información de versión)](/cpp/build/reference/version-version-information).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
