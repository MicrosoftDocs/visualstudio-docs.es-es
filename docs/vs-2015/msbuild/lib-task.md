---
title: Tarea LIB | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75e15c0230526fc7647144cbde566c693be58cbe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285511"
---
# <a name="lib-task"></a>LIB (tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Incluye la herramienta de Microsoft Administrador de bibliotecas de 32 bits, lib.exe. El Administrador de bibliotecas crea y administra una biblioteca de archivos objeto con formato de archivo de objeto común (COFF). El Administrador de bibliotecas también puede crear archivos de exportación y bibliotecas de importación para hacer referencia a las definiciones que se exportan. Para más información, vea [Referencia de LIB](http://msdn.microsoft.com/library/ecc7f643-bbd4-47a3-8dc6-b360f880db91) y [Ejecutar LIB](http://msdn.microsoft.com/library/d54f5c81-7147-4b2c-a8db-68ce6eb1eabd).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **LIB**. La mayoría de los parámetros de tarea corresponden a una opción de línea de comandos.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalDependencies**|Parámetro **String[]** opcional.<br /><br /> Especifica elementos adicionales que se agregarán a la línea de comandos del vínculo.|  
|**AdditionalLibraryDirectories**|Parámetro **String[]** opcional.<br /><br /> Reemplaza la ruta de acceso a la biblioteca de entorno. Especifique un nombre de directorio.<br /><br /> Para obtener más información, consulte [/LIBPATH (Directorios de bibliotecas adicionales)](http://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones de lib.exe especificada en la línea de comando. Por ejemplo, ** "_/option1 option2 /Option #_". Use este parámetro para especificar opciones de lib.exe que no están representadas por ningún otro parámetro de tarea **LIB**.<br /><br /> Para más información, vea [Ejecutar LIB](http://msdn.microsoft.com/library/d54f5c81-7147-4b2c-a8db-68ce6eb1eabd).|  
|**DisplayLibrary**|Parámetro **String** opcional.<br /><br /> Muestra información sobre la biblioteca de salida. Especifique un nombre de archivo para redirigir la información a un archivo. Especifique "CON" o nada para redirigir la información a la consola.<br /><br /> Este parámetro corresponde a la opción **/LIST** de lib.exe.|  
|**ErrorReporting**|Parámetro **String** opcional.<br /><br /> Especifica cómo enviar información de error interno a Microsoft si lib.exe genera un error en tiempo de ejecución.<br /><br /> Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Para más información, vea la opción de línea de comandos **/ERRORREPORT** en [Ejecutar LIB](http://msdn.microsoft.com/library/d54f5c81-7147-4b2c-a8db-68ce6eb1eabd).|  
|**ExportNamedFunctions**|Parámetro **String[]** opcional.<br /><br /> Especifica una o más funciones que se van a exportar.<br /><br /> Este parámetro corresponde a la opción **/EXPORT:** de lib.exe.|  
|**ForceSymbolReferences**|Parámetro **String** opcional.<br /><br /> Hace que lib.exe incluya una referencia al símbolo especificado.<br /><br /> Este parámetro corresponde a la opción **/INCLUDE:** de lib.exe.|  
|**IgnoreAllDefaultLibraries**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, quita todas las bibliotecas predeterminadas de la lista de bibliotecas en la que busca lib.exe cuando resuelve referencias externas.<br /><br /> Este parámetro corresponde a la forma sin parámetros de la opción **/NODEFAULTLIB** de lib.exe.|  
|**IgnoreSpecificDefaultLibraries**|Parámetro **String[]** opcional.<br /><br /> Quita las bibliotecas especificadas de la lista de bibliotecas en la que busca lib.exe cuando resuelve referencias externas.<br /><br /> Este parámetro corresponde a la opción **/NODEFAULTLIB** de lib.exe que toma un argumento `library`.|  
|**LinkLibraryDependencies**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, especifica que los resultados de la biblioteca de las dependencias del proyecto se vinculan automáticamente.|  
|**LinkTimeCodeGeneration**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, especifica la generación de código en tiempo de vínculo.<br /><br /> Este parámetro corresponde a la opción **/LCTG** de lib.exe.|  
|**MinimumRequiredVersion**|Parámetro **String** opcional.<br /><br /> Especifica la versión mínima requerida del subsistema. Especifique una lista delimitada por comas de números decimales comprendidos entre 0 y 65535.|  
|**ModuleDefinitionFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de definición de módulo (.def).<br /><br /> Este parámetro corresponde a la opción **/DEF** de lib.exe que toma un argumento `filename`.|  
|**Name**|Parámetro **String** opcional.<br /><br /> Cuando se compila una biblioteca de importación, especifica el nombre del archivo DLL para el que se va a compilar dicha biblioteca.<br /><br /> Este parámetro corresponde a la opción **/NAME** de lib.exe que toma un argumento `filename`.|  
|**OutputFile**|Parámetro **String** opcional.<br /><br /> Invalida el nombre y la ubicación predeterminados del programa que crea lib.exe.<br /><br /> Este parámetro corresponde a la opción **/OUT** de lib.exe que toma un argumento `filename`.|  
|**RemoveObjects**|Parámetro **String[]** opcional.<br /><br /> Omite el objeto especificado de la biblioteca de salida. Lib.exe crea una biblioteca de salida; para ello, combina todos los objetos (independientemente de que estén en archivos objeto o bibliotecas) y, a continuación, elimina los objetos que se especifican en esta opción.<br /><br /> Este parámetro corresponde a la opción **/REMOVE** de lib.exe que toma un argumento `membername`.|  
|**Sources**|Parámetro `ITaskItem[]` requerido.<br /><br /> Especifica una lista de archivos de código fuente, separados por espacios.|  
|**SubSystem**|Parámetro **String** opcional.<br /><br /> Especifica el entorno del ejecutable. La opción de subsistema afecta al símbolo de punto de entrada o función de punto de entrada.<br /><br /> Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.<br /><br /> -   **Console** - **/SUBSYSTEM:CONSOLE**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Native** - **/SUBSYSTEM:NATIVE**<br />-   **EFI Application** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI Boot Service Driver** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**ReplaceThisText<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Para obtener más información, consulte [/SUBSYSTEM (especificar subsistema)](http://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).|  
|**SuppressStartupBanner**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia. <br /><br /> Para más información, vea la opción **/NOLOGO** en [Ejecutar LIB](http://msdn.microsoft.com/library/d54f5c81-7147-4b2c-a8db-68ce6eb1eabd).|  
|**TargetMachine**|Parámetro **String** opcional.<br /><br /> Especifica la plataforma de destino para el programa o DLL.<br /><br /> Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Para obtener más información, consulte [/MACHINE (especificar la plataforma de destino)](http://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).|  
|**TrackerLogDirectory**|Parámetro **String** opcional.<br /><br /> Especifica el directorio del registro de seguimiento.|  
|**TreatLibWarningAsErrors**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, hace que la tarea **LIB** no genere un archivo de salida si lib.exe genera una advertencia. Si es `false`, se genera un archivo de salida.<br /><br /> Para más información, vea la opción **/WX** en [Ejecutar LIB](http://msdn.microsoft.com/library/d54f5c81-7147-4b2c-a8db-68ce6eb1eabd).|  
|**UseUnicodeResponseFiles**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, indica al sistema del proyecto que genere archivos de respuesta UNICODE al generar el bibliotecario. Especifique `true` cuando los archivos del proyecto tengan rutas de acceso UNICODE.|  
|**Verbose**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, muestra detalles sobre el progreso de la sesión; esto incluye los nombres de los archivos .obj que se van a agregar. La información se envía a la salida estándar y puede redirigirse a un archivo.<br /><br /> Para más información, vea la opción **/VERBOSE** en [Ejecutar LIB](http://msdn.microsoft.com/library/d54f5c81-7147-4b2c-a8db-68ce6eb1eabd).|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



