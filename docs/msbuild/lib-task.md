---
title: Tarea LIB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c9d80da9fea46ddcc2afe2f935fa66a892d90c1
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254532"
---
# <a name="lib-task"></a>LIB (tarea)
Incluye la herramienta de Microsoft Administrador de bibliotecas de 32 bits, *lib.exe*. El Administrador de bibliotecas crea y administra una biblioteca de archivos objeto con formato de archivo de objeto común (COFF). El Administrador de bibliotecas también puede crear archivos de exportación y bibliotecas de importación para hacer referencia a las definiciones que se exportan. Para obtener más información, vea [Referencia de LIB](/cpp/build/reference/lib-reference) y [Ejecutar LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea **LIB**. La mayoría de los parámetros de tarea corresponden a una opción de línea de comandos.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**AdditionalDependencies**|Parámetro **String[]** opcional.<br /><br /> Especifica elementos adicionales que se agregarán a la línea de comandos del vínculo.|
|**AdditionalLibraryDirectories**|Parámetro **String[]** opcional.<br /><br /> Reemplaza la ruta de acceso a la biblioteca de entorno. Especifique un nombre de directorio.<br /><br /> Para obtener más información, consulte [/LIBPATH (Directorios de bibliotecas adicionales)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones de *lib.exe* según lo especificado en la línea de comandos. Por ejemplo, /\<option1> /\<option2> /\<option#>. Use este parámetro para especificar opciones de *lib.exe* que no estén representadas por ningún otro parámetro de tarea **LIB**.<br /><br /> Para más información, vea [Ejecutar LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Parámetro **String** opcional.<br /><br /> Muestra información sobre la biblioteca de salida. Especifique un nombre de archivo para redirigir la información a un archivo. Especifique "CON" o nada para redirigir la información a la consola.<br /><br /> Este parámetro corresponde a la opción **/LIST** de *lib.exe*.|
|**ErrorReporting**|Parámetro **String** opcional.<br /><br /> Especifica cómo enviar información de error interna a Microsoft si *lib.exe* genera un error en tiempo de ejecución.<br /><br /> Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.<br /><br /> -   **NoErrorReport** -  **/ERRORREPORT:NONE**<br />-   **PromptImmediately** -  **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** -  **/ERRORREPORT:SEND**<br /><br /> Para más información, vea la opción de línea de comandos **/ERRORREPORT** en [Ejecutar LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Parámetro **String[]** opcional.<br /><br /> Especifica una o más funciones que se van a exportar.<br /><br /> Este parámetro corresponde a la opción **/EXPORT:** de *lib.exe*.|
|**ForceSymbolReferences**|Parámetro **String** opcional.<br /><br /> Obliga a que *lib.exe* incluya una referencia al símbolo especificado.<br /><br /> Este parámetro corresponde a la opción **/INCLUDE:** de *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, quita todas las bibliotecas predeterminadas de la lista de bibliotecas en la que busca *lib.exe* cuando resuelve referencias externas.<br /><br /> Este parámetro corresponde a la forma sin parámetros de la opción **/NODEFAULTLIB** de *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Parámetro **String[]** opcional.<br /><br /> Quita las bibliotecas especificadas de la lista de bibliotecas en la que busca *lib.exe* cuando resuelve referencias externas.<br /><br /> Este parámetro corresponde a la opción **/NODEFAULTLIB** de *lib.exe* que toma un argumento `library`.|
|**LinkLibraryDependencies**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, especifica que los resultados de la biblioteca de las dependencias del proyecto se vinculan automáticamente.|
|**LinkTimeCodeGeneration**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, especifica la generación de código en tiempo de vínculo.<br /><br /> Este parámetro corresponde a la opción **/LCTG** de *lib.exe*.|
|**MinimumRequiredVersion**|Parámetro **String** opcional.<br /><br /> Especifica la versión mínima requerida del subsistema. Especifique una lista delimitada por comas de números decimales comprendidos entre 0 y 65535.|
|**ModuleDefinitionFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de definición de módulos ( *.def*).<br /><br /> Este parámetro corresponde a la opción **/DEF** de *lib.exe* que toma un argumento `filename`.|
|**Name**|Parámetro **String** opcional.<br /><br /> Cuando se compila una biblioteca de importación, especifica el nombre del archivo DLL para el que se va a compilar dicha biblioteca.<br /><br /> Este parámetro corresponde a la opción **/NAME** de *lib.exe* que toma un argumento `filename`.|
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Reemplaza el nombre y la ubicación predeterminados del programa que crea *lib.exe*.<br /><br /> Este parámetro corresponde a la opción **/OUT** de *lib.exe* que toma un argumento `filename`.|
|**RemoveObjects**|Parámetro **String[]** opcional.<br /><br /> Omite el objeto especificado de la biblioteca de salida. *Lib.exe* crea una biblioteca de salida al combinar todos los objetos (independientemente de que estén en archivos objeto o bibliotecas) y luego eliminar los objetos especificados por esta opción.<br /><br /> Este parámetro corresponde a la opción **/REMOVE** de *lib.exe* que toma un argumento `membername`.|
|**Sources**|Parámetro `ITaskItem[]` requerido.<br /><br /> Especifica una lista de archivos de código fuente, separados por espacios.|
|**SubSystem**|Parámetro **String** opcional.<br /><br /> Especifica el entorno del ejecutable. La opción de subsistema afecta al símbolo de punto de entrada o función de punto de entrada.<br /><br /> Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.<br /><br /> -   **Console** -  **/SUBSYSTEM:CONSOLE**<br />-   **Windows** -  **/SUBSYSTEM:WINDOWS**<br />-   **Native** -  **/SUBSYSTEM:NATIVE**<br />-   **EFI Application** -  **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI Boot Service Driver** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** -  **/SUBSYSTEM:EFI_ROM**<br />-   **EFI Runtime** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** -  **/SUBSYSTEM:POSIX**<br /><br /> Para obtener más información, vea [/SUBSYSTEM (Especificar subsistema)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para más información, vea la opción **/NOLOGO** en [Ejecutar LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Parámetro **String** opcional.<br /><br /> Especifica la plataforma de destino para el programa o DLL.<br /><br /> Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.<br /><br /> -   **MachineARM** -  **/MACHINE:ARM**<br />-   **MachineEBC** -  **/MACHINE:EBC**<br />-   **MachineIA64** -  **/MACHINE:IA64**<br />-   **MachineMIPS** -  **/MACHINE:MIPS**<br />-   **MachineMIPS16** -  **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** -  **/MACHINE:SH4**<br />-   **MachineTHUMB** -  **/MACHINE:THUMB**<br />-   **MachineX64** -  **/MACHINE:X64**<br />-   **MachineX86** -  **/MACHINE:X86**<br /><br /> Para obtener más información, vea [/MACHINE (Especificar la plataforma de destino)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio del registro de seguimiento.|
|**TreatLibWarningAsErrors**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, hace que la tarea **LIB** no genere un archivo de salida si *lib.exe* genera una advertencia. Si es `false`, se genera un archivo de salida.<br /><br /> Para más información, vea la opción **/WX** en [Ejecutar LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, indica al sistema del proyecto que genere archivos de respuesta UNICODE al generar el bibliotecario. Especifique `true` cuando los archivos del proyecto tengan rutas de acceso UNICODE.|
|**Verbose**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, muestra detalles sobre el progreso de la sesión; esto incluye los nombres de los archivos *.obj* que se van a agregar. La información se envía a la salida estándar y puede redirigirse a un archivo.<br /><br /> Para más información, vea la opción **/VERBOSE** en [Ejecutar LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Vea también
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)