---
title: Vincular tarea | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0aaf4d5f6862e2b5ef40b88e8041aa9ccc5a317
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592944"
---
# <a name="link-task"></a>Vincular tarea
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Vincular tarea](https://docs.microsoft.com/visualstudio/msbuild/link-task).  
  
  
Encapsula la herramienta del vinculador de Visual C++, link.exe. La herramienta del vinculador vincula bibliotecas y archivos de objeto de formato de archivo de objeto común (COFF) para crear un archivo ejecutable (.exe) o una biblioteca de vínculos dinámicos (DLL). Para obtener más información, consulte [Opciones del enlazador](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **Link**. La mayoría de los parámetros de tareas, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
-   **AdditionalDependencies**  
  
     Parámetro **String[]** opcional.  
  
     Especifica una lista de archivos de entrada para agregar al comando.  
  
     Para obtener más información, consulte [Archivos de entrada de LINK](http://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
-   **AdditionalLibraryDirectories**  
  
     Parámetro **String[]** opcional.  
  
     Reemplaza la ruta de acceso a la biblioteca de entorno. Especifique un nombre de directorio.  
  
     Para obtener más información, consulte [/LIBPATH (Directorios de bibliotecas adicionales)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
-   **AdditionalManifestDependencies**  
  
     Parámetro **String[]** opcional.  
  
     Especifica los atributos que se colocarán en la sección `dependency` del archivo de manifiesto.  
  
     Para obtener más información, consulte [/MANIFESTDEPENDENCY (Especificar las dependencias de manifiesto)](http://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Consulte también "Archivos de configuración del publicador" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
-   **AdditionalOptions**  
  
     Parámetro **String** opcional.  
  
     Una lista de opciones del enlazador especificada en la línea de comandos. Por ejemplo, **"**_/option1 /option2 /option#_". Utilice este parámetro para especificar opciones del enlazador que no están representadas por ningún otro parámetro de la tarea **Link**.  
  
     Para obtener más información, consulte [Opciones del enlazador](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
-   **AddModuleNamesToAssembly**  
  
     Parámetro **String[]** opcional.  
  
     Agrega una referencia de módulo en un ensamblado.  
  
     Para obtener más información, consulte [/ASSEMBLYMODULE (Agregar un módulo MSIL al ensamblado)](http://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
-   **AllowIsolation**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, hace que el sistema operativo realice cargas y búsquedas de manifiestos. Si `false`, indica que los archivos DLL se cargan como si no hubiera ningún manifiesto.  
  
     Para obtener más información, consulte [/ALLOWISOLATION (Búsqueda de manifiestos)](http://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
-   **AssemblyDebug**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, emite el atributo **DebuggableAttribute**, junto con el seguimiento de la información de depuración, y desactiva las optimizaciones JIT. Si `false`, emite el atributo **DebuggableAttribute**, pero desactiva el seguimiento de la información de depuración y activa las optimizaciones JIT.  
  
     Para obtener más información, consulte [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
-   **AssemblyLinkResource**  
  
     Parámetro **String[]** opcional.  
  
     Crea un vínculo a un recurso de .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida. Especifique el nombre del recurso.  
  
     Para obtener más información, consulte [/ASSEMBLYLINKRESOURCE (vincular a recursos de .NET Framework)](http://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
-   **AttributeFileTracking**  
  
     Parámetro **Boolean** implícito.  
  
     Permite un seguimiento más a fondo de los archivos para capturar el comportamiento incremental del vínculo. Siempre devuelve `true`.  
  
-   **BaseAddress**  
  
     Parámetro **String** opcional.  
  
     Establece una dirección base para el programa o el archivo DLL que se compila. Especifique `{address[,size] | @filename,key}`.  
  
     Para obtener más información, consulte [/BASE (dirección base)](http://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
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
  
     Para obtener más información, consulte [/CLRIMAGETYPE (especificar tipo de imagen de CLR)](http://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
-   **CLRSupportLastError**  
  
     Parámetro **String** opcional.  
  
     Conserva el último código de error de las funciones llamadas a través del mecanismo P/Invoke.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **Enabled** - **/CLRSupportLastError**  
  
    -   **Disabled** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
     Para obtener más información, consulte [/CLRSUPPORTLASTERROR (conservar el último código de error para las llamadas a PInvoke)](http://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
-   **CLRThreadAttribute**  
  
     Parámetro **String** opcional.  
  
     Especifica explícitamente el atributo de subprocesamiento del punto de entrada del programa CLR.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**  
  
    -   **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
     Para obtener más información, consulte [/CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR)](http://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Parámetro **Boolean** opcional.  
  
     Especifica si el enlazador aplicará **SuppressUnmanagedCodeSecurityAttribute** a las llamadas P/Invoke generadas por enlazador a partir de código administrado en archivos DLL nativos.  
  
     Para obtener más información, consulte [/CLRUNMANAGEDCODECHECK (Agregar SupressUnmanagedCodeSecurityAttribute)](http://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
-   **CreateHotpatchableImage**  
  
     Parámetro **String** opcional.  
  
     Prepara una imagen para aplicar una revisión activa.  
  
     Especifique uno de los valores siguientes, que corresponde a una opción del enlazador.  
  
    -   **Enabled** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
     Para obtener más información, consulte [/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)](http://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
-   **DataExecutionPrevention**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica que se ha probado si un ejecutable es compatible con la característica Prevención de ejecución de datos de Windows.  
  
     Para obtener más información, consulte [/NXCOMPAT (Compatible con Prevención de ejecución de datos)](http://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
-   **DelayLoadDLLs**  
  
     Parámetro **String[]** opcional.  
  
     Este parámetro causa la *carga retrasada* de archivos DLL. Especifique el nombre de un archivo DLL cuya carga se desea retrasar.  
  
     Para obtener más información, consulte [/DELAYLOAD (Retrasar importación de carga)](http://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
-   **DelaySign**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, firma parcialmente un ensamblado. De forma predeterminada, el valor es `false`.  
  
     Para obtener más información, consulte [/DELAYSIGN (Firmar parcialmente un ensamblado)](http://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
-   **Driver**  
  
     Parámetro **String** opcional.  
  
     Especifique este parámetro para compilar un controlador de modo kernel de Windows NT.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción del enlazador.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Driver** - **/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** -   **/DRIVER: WDM**  
  
     Para obtener más información, consulte [/DRIVER (Controlador de modo kernel de Windows NT)](http://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
-   **EmbedManagedResourceFile**  
  
     Parámetro **String[]** opcional.  
  
     Inserta un archivo de recursos en un ensamblado. Especifique el nombre de archivo de recursos necesario. Opcionalmente, especifique el nombre lógico (usado para cargar el recurso) y la opción **PRIVATE** (que indica en el manifiesto del ensamblado que el archivo de recursos es privado).  
  
     Para obtener más información, consulte [/ASSEMBLYRESOURCE (Insertar un recurso administrado)](http://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
-   **EnableCOMDATFolding**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, permite un plegamiento idéntico de COMDAT.  
  
     Para obtener más información, consulte el argumento `ICF[= iterations]` de [/OPT (Optimizaciones)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
-   **EnableUAC**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica si la información de Control de cuentas de usuario (UAC) debe insertarse en el manifiesto del programa.  
  
     Para obtener más información, consulte [/MANIFESTUAC (Insertar información de UAC en el manifiesto)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
-   **EntryPointSymbol**  
  
     Parámetro **String** opcional.  
  
     Especifica una función de punto de entrada como dirección inicial para un archivo .exe o DLL. Especifique un nombre de función como el valor del parámetro.  
  
     Para obtener más información, consulte [/ENTRY (Símbolo de punto de entrada)](http://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
-   **FixedBaseAddress**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea un programa o un archivo DLL que solo se puede cargar en su dirección base preferida.  
  
     Para obtener más información, consulte [/FIXED (Dirección base fija)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
-   **ForceFileOutput**  
  
     Parámetro **String** opcional.  
  
     Indica al enlazador que cree un archivo .exe o DLL válido aunque se haga referencia a un símbolo, pero no se defina o bien se defina varias veces.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Enabled** - **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
    -   **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**  
  
     Para obtener más información, consulte [/FORCE (Forzar resultados de archivo)](http://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
-   **ForceSymbolReferences**  
  
     Parámetro **String[]** opcional.  
  
     Este parámetro indica al enlazador que agregue un símbolo especificado a la tabla de símbolos.  
  
     Para obtener más información, consulte [/INCLUDE (Forzar referencias de símbolos)](http://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
-   **FunctionOrder**  
  
     Parámetro **String** opcional.  
  
     Este parámetro optimiza su programa colocando las funciones empaquetadas especificadas (COMDAT) en la imagen en un orden predeterminado.  
  
     Para obtener más información, consulte [/ORDER (Colocar funciones en orden)](http://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
-   **GenerateDebugInformation**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea información de depuración para el archivo .exe o DLL.  
  
     Para obtener más información, consulte [/DEBUG (generar información de depuración)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
-   **GenerateManifest**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea un archivo de manifiesto en paralelo.  
  
     Para obtener más información, consulte [/MANIFEST (Crear el manifiesto del ensamblado en paralelo)](http://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
-   **GenerateMapFile**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea un *archivo de asignación*. La extensión de nombre de archivo del archivo de asignación es .map.  
  
     Para obtener más información, consulte [/MAP (generar archivo de asignaciones)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
-   **HeapCommitSize**  
  
     Parámetro **String** opcional.  
  
     Especifica la cantidad de memoria física en el montón que se debe asignar de una sola vez.  
  
     Para obtener más información, consulte el argumento `commit` en [/HEAP (Establecer el tamaño del montón)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Consulte también el parámetro **HeapReserveSize**.  
  
-   **HeapReserveSize**  
  
     Parámetro **String** opcional.  
  
     Especifica el tamaño total asignado al montón en la memoria virtual.  
  
     Para obtener más información, consulte el argumento `reserve` en [/HEAP (Establecer el tamaño del montón)](http://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Consulte también el parámetro **HeapCommitSize** en esta tabla.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al enlazador que quite una o varias bibliotecas predeterminadas de la lista de bibliotecas en la que realiza búsquedas cuando resuelve referencias externas.  
  
     Para obtener más información, consulte [/NODEFAULTLIB (Omitir bibliotecas)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
-   **IgnoreEmbeddedIDL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica que no se debe procesar ningún atributo IDL del código fuente en un archivo .idl.  
  
     Para obtener más información, consulte [/IGNOREIDL (No procesar atributos en MIDL)](http://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
-   **IgnoreImportLibrary**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica que la biblioteca de importación generada por esta configuración no se importará en los proyectos dependientes.  
  
     Este parámetro no se corresponde con ninguna opción del enlazador.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Parámetro **String[]** opcional.  
  
     Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán. Separe varias bibliotecas mediante punto y coma.  
  
     Para obtener más información, consulte [/NODEFAULTLIB (Omitir bibliotecas)](http://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, el enlazador genera una imagen solo si también puede generar una tabla de los controladores de excepciones seguros de la imagen.  
  
     Para obtener más información, consulte [/SAFESEH (la imagen tiene controladores de excepciones seguros)](http://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
-   **ImportLibrary**  
  
     Nombre de la biblioteca de importación especificada por el usuario que reemplaza el nombre de biblioteca predeterminado.  
  
     Para obtener más información, consulte [/IMPLIB (Asignar nombre a la biblioteca de importación)](http://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
-   **KeyContainer**  
  
     Parámetro **String** opcional.  
  
     Contenedor que contiene la clave de un ensamblado firmado.  
  
     Para obtener más información, consulte [/KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Consulte también el parámetro **KeyFile** en esta tabla.  
  
-   **KeyFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un archivo que contiene la clave de un ensamblado firmado.  
  
     Para obtener más información, consulte [/KEYFILE (Especificar una clave o un par de claves para firmar un ensamblado)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Consulte también el parámetro **KeyContainer**.  
  
-   **LargeAddressAware**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, la aplicación puede controlar direcciones mayores de 2 gigabytes.  
  
     Para obtener más información, consulte [/LARGEADDRESSAWARE (controlar direcciones largas)](http://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
-   **LinkDLL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, compila un archivo DLL como el archivo de salida principal.  
  
     Para obtener más información, consulte [/DLL (compilar un archivo DLL)](http://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
-   **LinkErrorReporting**  
  
     Parámetro **String** opcional.  
  
     Permite proporcionar directamente a Microsoft información sobre los errores internos del compilador (ICE).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NoErrorReport** - **/ERRORREPORT:NONE**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** - **/ERRORREPORT:SEND**  
  
     Para obtener más información, consulte [/ERRORREPORT (Informar de errores internos del enlazador)](http://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
-   **LinkIncremental**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, controla la vinculación incremental.  
  
     Para obtener más información, consulte [/INCREMENTAL (Vincular de forma incremental)](http://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
-   **LinkLibraryDependencies**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, especifica que los resultados de la biblioteca de las dependencias del proyecto se vinculan automáticamente.  
  
     Este parámetro no se corresponde con ninguna opción del enlazador.  
  
-   **LinkStatus**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica que el enlazador debe mostrar un indicador de progreso que muestra qué porcentaje del vínculo está completado.  
  
     Para obtener más información, consulte el argumento `STATUS` de [/LTCG (Generación de código en tiempo de vínculo)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
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
  
     Para obtener más información, consulte [/LTCG (generación de código en tiempo de vínculo)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
-   **ManifestFile**  
  
     Parámetro **String** opcional.  
  
     Cambia el nombre de archivo de manifiesto predeterminado por el nombre de archivo especificado.  
  
     Para obtener más información, consulte [/MANIFESTFILE (Nombre de archivo de manifiesto)](http://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
-   **MapExports**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al enlazador que incluya funciones exportadas en un archivo de asignación.  
  
     Para obtener más información, consulte el argumento `EXPORTS` de [/MAPINFO (Incluir información en el archivo de asignaciones)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
-   **MapFileName**  
  
     Parámetro **String** opcional.  
  
     Cambia el nombre de archivo de asignación predeterminado por el nombre de archivo especificado.  
  
-   **MergedIDLBaseFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de archivo y la extensión de nombre de archivo del archivo .idl.  
  
     Para obtener más información, consulte [/IDLOUT (Dar nombre a los archivos de salida de MIDL)](http://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
-   **MergeSections**  
  
     Parámetro **String** opcional.  
  
     Combina secciones en una imagen. Especifique `from-section=to-section`.  
  
     Para obtener más información, consulte [/MERGE (Combinar secciones)](http://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
-   **MidlCommandFile**  
  
     Parámetro **String** opcional.  
  
     Especifique el nombre de un archivo que contiene las opciones de línea de comandos de MIDL.  
  
     Para obtener más información, consulte [/MIDL (Especificar las opciones de línea de comandos de MIDL)](http://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
-   **MinimumRequiredVersion**  
  
     Parámetro **String** opcional.  
  
     Especifica la versión mínima requerida del subsistema. Los argumentos son números decimales comprendidos en el intervalo de 0 a 65535.  
  
-   **ModuleDefinitionFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de un [archivo de definición de módulos](http://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
     Para obtener más información, consulte [/DEF (Especificar un archivo de definición de módulos)](http://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
-   **MSDOSStubFileName**  
  
     Parámetro **String** opcional.  
  
     Adjunta el programa de código auxiliar de MS-DOS especificado a un programa Win32.  
  
     Para obtener más información, consulte [/STUB (nombre del archivo de código auxiliar de MS-DOS)](http://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
-   **NoEntryPoint**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, especifica un archivo DLL solo de recursos.  
  
     Para obtener más información, consulte [/NOENTRY (sin punto de entrada)](http://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
-   **ObjectFiles**  
  
     Parámetro **String[]** implícito.  
  
     Especifica los archivos objeto vinculados.  
  
-   **OptimizeReferences**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, elimina las funciones o los datos a los que nunca se hace referencia.  
  
     Para obtener más información, consulte el argumento `REF` en [/OPT (Optimizaciones)](http://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
-   **OutputFile**  
  
     Parámetro **String** opcional.  
  
     Invalida el nombre y la ubicación predeterminados del programa que crea el enlazador.  
  
     Para obtener más información, consulte [/OUT (Nombre del archivo de salida)](http://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
-   **PerUserRedirection**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, y la opción Registrar resultados está activada, hace que las escrituras en la clave del registro **HKEY_CLASSES_ROOT** se redirijan a **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     Parámetro `ITaskItem[]` opcional.  
  
     Define una matriz de elementos de elementos de salida del preprocesador que las tareas pueden consumir y emitir.  
  
-   **PreventDllBinding**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica a Bind.exe que la imagen vinculada no se debe enlazar.  
  
     Para obtener más información, consulte [/ALLOWBIND (Evitar el enlace de archivos DLL)](http://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
-   **Profile**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, produce un archivo de salida que se puede utilizar con el generador de perfiles de **Herramientas de rendimiento**.  
  
     Para obtener más información, consulte [/PROFILE (Generador de perfiles de Herramientas de rendimiento)](http://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
-   **ProfileGuidedDatabase**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre del archivo .pgd que se utilizará para almacenar información sobre el programa en ejecución  
  
     Para obtener más información, consulte [/PGD (especificar la base de datos para las optimizaciones guiadas por perfiles)](http://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
-   **ProgramDatabaseFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre para la base de datos de programa (PDB) que crea el enlazador.  
  
     Para obtener más información, consulte [/PDB (Utilizar la base de datos de programa)](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
-   **RandomizedBaseAddress**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, genera una imagen ejecutable que se puede reorganizar aleatoriamente en el momento de la carga mediante la característica de *selección aleatoria del diseño del espacio de direcciones* (ASLR) de Windows.  
  
     Para obtener más información, consulte [/DYNAMICBASE (utilizar selección aleatoria del diseño del espacio de direcciones)](http://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
-   **RegisterOutput**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, registra la salida principal de esta compilación.  
  
-   **SectionAlignment**  
  
     Parámetro **Integer** opcional.  
  
     Especifica la alineación de cada sección en el espacio de direcciones lineales del programa. El valor del parámetro es un número de unidad de bytes y una potencia de dos.  
  
     Para obtener más información, consulte [/ALIGN (Alineación de sección)](http://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
-   **SetChecksum**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, establece la suma de comprobación en el encabezado de un archivo .exe.  
  
     Para obtener más información, consulte [/RELEASE (Establecer la suma de comprobación)](http://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
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
  
     Para obtener más información, consulte [/VERBOSE (Mostrar mensajes de progreso)](http://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
-   **Sources**  
  
     Parámetro `ITaskItem[]` requerido.  
  
     Define una matriz de elementos de archivo origen de MSBuild que las tareas pueden consumir y emitir.  
  
-   **SpecifySectionAttributes**  
  
     Parámetro **String** opcional.  
  
     Especifica los atributos de una sección. Esto invalida los atributos que se establecieron cuando se compiló el archivo .obj para la sección.  
  
     Para obtener más información, consulte [/SECTION (Especificar los atributos de la sección)](http://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
-   **StackCommitSize**  
  
     Parámetro **String** opcional.  
  
     Especifica la cantidad de memoria física de cada asignación cuando se asigna memoria adicional.  
  
     Para obtener más información, consulte el argumento `commit` de [/STACK (Asignaciones de pila)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
-   **StackReserveSize**  
  
     Parámetro **String** opcional.  
  
     Especifica el tamaño total asignado a la pila en la memoria virtual.  
  
     Para obtener más información, consulte el argumento `reserve` de [/STACK (Asignaciones de pila)](http://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
-   **StripPrivateSymbols**  
  
     Parámetro **String** opcional.  
  
     Crea un segundo archivo de base de datos (PDB) de programa que omite los símbolos que no quiere distribuir a sus clientes. Especifique el nombre del segundo archivo PDB.  
  
     Para obtener más información, consulte [/PDBSTRIPPED (quitar símbolos privados)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
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
  
     Para obtener más información, consulte [/SUBSYSTEM (especificar subsistema)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al enlazador que no incluya una tabla de direcciones de importación (IAT) enlazable en la imagen final.  
  
     Para obtener más información, consulte el argumento `NOBIND` de [/DELAY (Configuración de las importaciones de carga retrasada)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica a la función del asistente de carga retrasada que admita la descarga explícita del archivo DLL.  
  
     Para obtener más información, consulte el argumento `UNLOAD` de [/DELAY (Configuración de las importaciones de carga retrasada)](http://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
-   **SuppressStartupBanner**  
  
     Parámetro **Boolean** opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
     Para obtener más información, consulte [/NOLOGO (Suprimir el titular de inicio) (enlazador)](http://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
-   **SwapRunFromCD**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al sistema operativo que copie primero la salida del enlazador a un archivo de intercambio y ejecute después la imagen desde allí.  
  
     Para obtener más información, consulte el argumento `CD` de [/SWAPRUN (cargar los resultados del enlazador en el archivo de intercambio)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Consulte también el parámetro **SwapRunFromNET**.  
  
-   **SwapRunFromNET**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, indica al sistema operativo que copie primero la salida del enlazador a un archivo de intercambio y ejecute después la imagen desde allí.  
  
     Para obtener más información, consulte el argumento `NET` de [/SWAPRUN (Cargar los resultados del enlazador en el archivo de intercambio)](http://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Consulte también el parámetro **SwapRunFromCD** en esta tabla.  
  
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
  
     Para obtener más información, consulte [/MACHINE (especificar la plataforma de destino)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
-   **TerminalServerAware**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, establece una marca en el campo IMAGE_OPTIONAL_HEADER DllCharacteristics del encabezado opcional de la imagen del programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.  
  
     Para obtener más información, consulte [/TSAWARE (Crear una aplicación que reconozca Terminal Server)](http://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
-   **TrackerLogDirectory**  
  
     Parámetro **String** opcional.  
  
     Especifica el directorio del registro de seguimiento.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, hace que no se genere ningún archivo de salida si el enlazador genera una advertencia.  
  
     Para obtener más información, consulte [/WX (Tratar advertencias del enlazador como errores)](http://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
-   **TurnOffAssemblyGeneration**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, crea una imagen para el archivo de salida actual sin un ensamblado de .NET Framework.  
  
     Para obtener más información, consulte [/NOASSEMBLY (Crear un módulo MSIL)](http://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
-   **TypeLibraryFile**  
  
     Parámetro **String** opcional.  
  
     Especifica el nombre de archivo y la extensión de nombre de archivo del archivo .tlb. Especifique un nombre de archivo o una ruta de acceso y un nombre de archivo.  
  
     Para obtener más información, consulte [/TLBOUT (Dar nombre a un archivo .TLB)](http://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
-   **TypeLibraryResourceID**  
  
     Parámetro **Integer** opcional.  
  
     Designa un valor especificado por el usuario para una biblioteca de tipos creada por el enlazador. Especifique un valor entre 1 y 65535.  
  
     Para obtener más información, consulte [/TLBID (Especificar un identificador de recursos para una biblioteca de tipos)](http://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
-   **UACExecutionLevel**  
  
     Parámetro **String** opcional.  
  
     Especifica el nivel de ejecución solicitado para la aplicación cuando se ejecuta con Control de cuentas de usuario.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator** - `level='requireAdministrator'`  
  
     Para obtener más información, consulte el argumento `level` de [/MANIFESTUAC (insertar información de UAC en el manifiesto)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
-   **UACUIAccess**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, la aplicación omite los niveles de protección de la interfaz de usuario y dirige las entradas de datos a ventanas con un nivel de permisos superior en el escritorio; de lo contrario, `false`.  
  
     Para obtener más información, consulte el argumento `uiAccess` de [/MANIFESTUAC (insertar información de UAC en el manifiesto)](http://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
-   **UseLibraryDependencyInputs**  
  
     Parámetro **Boolean** opcional.  
  
     Si `true`, se utilizan las entradas a la herramienta bibliotecario en lugar del propio archivo de biblioteca cuando se vinculan resultados de biblioteca de dependencias del proyecto.  
  
-   **Versión**  
  
     Parámetro **String** opcional.  
  
     Ponga un número de versión en el encabezado del archivo .exe o .dll. Especifique "`major[.minor]`". Los argumentos `major` y `minor` son números decimales comprendidos entre 0 y 65535.  
  
     Para obtener más información, consulte [/VERSION (Información sobre la versión)](http://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



