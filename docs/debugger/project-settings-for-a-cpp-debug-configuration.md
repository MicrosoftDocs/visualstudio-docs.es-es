---
title: Configuración del proyecto para una configuración de depuración de C++
ms.custom: seodec18
ms.date: 11/26/2018
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 163b3e2d3ac222fd2e495e7a3b71841c818a4a3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961853"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Configuración del proyecto para una configuración de depuración de C++
Puede cambiar la configuración del proyecto para una configuración de depuración de C o Visual C++ en el **páginas de propiedades** cuadro de diálogo, como se describe en [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). En las siguientes tablas se muestra dónde encontrar los valores relacionados con el depurador en el cuadro de diálogo **Páginas de propiedades**.  
  
> [!NOTE]
>  La configuración de depuración del proyecto en el **propiedades de configuración/depuración** categoría son diferentes para las aplicaciones UWP y para los componentes que están escritos en C++. Consulte [iniciar una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Cada configuración de depuración se escribe automáticamente y se guardan en el archivo "por usuario" (. vcxproj.user) de la solución cuando guarde la solución.  

 Especifique el depurador que se va a usar en el **depurador para iniciar** cuadro de lista, como se describe en la tabla siguiente. La opción determinará qué propiedades serán visibles.  
    
## <a name="configuration-properties-folder-debugging-category"></a>Carpeta Propiedades de configuración (categoría Depuración)  
  
| **Configuración** | **Descripción** |
| - | - |
| **Depurador para iniciar** | Especifica el depurador que se va a ejecutar, con las opciones siguientes:<br /><br /> -   **Depurador local de Windows**<br />-   **Depurador remoto de Windows**<br />-   **Depurador de explorador web**<br />-   **Depurador de servicio web** |
| **Comando** (Depurador local de Windows) | Especifica el comando usado para iniciar el programa que se está depurando en el equipo local. |
| **Comando remoto** (Depurador remoto de Windows) | La ruta de acceso al archivo .exe en el equipo remoto. Escriba la ruta de acceso como lo haría en el equipo remoto. |
| **Argumentos de comandos** (depurador Local de Windows)<br /><br /> **Argumentos de comando remoto** (depurador remoto de Windows) | -   Especifica los argumentos del comando especificado anteriormente.<br /><br /> Puede utilizar los siguientes operadores de redirección en este cuadro:<br /><br /> < `file`<br /> Lee stdin del archivo.<br /><br /> > `file`<br /> Escribe stdout en el archivo.<br /><br /> >> `file`<br /> Agrega stdout al archivo.<br /><br /> 2> `file`<br /> Escribe stderr en el archivo.<br /><br /> 2>> `file`<br /> Agrega stderr al archivo.<br /><br /> 2> &1<br /> Envía el resultado de stderr (2) a la misma posición que stdout (1).<br /><br /> 1> &2<br /> Envía el resultado de stdout (1) a la misma posición que stderr (2).<br /><br /> En la mayoría de los casos, estos operadores solo pueden utilizarse en aplicaciones de consola. |
| **Directorio de trabajo** | Especifica el directorio de trabajo del programa que se está depurando en relación con el directorio del proyecto en el que se encuentra el archivo EXE. Si lo deja en blanco, el directorio de trabajo será el directorio del proyecto. Para la depuración remota, el directorio del proyecto está en el servidor remoto. |
| **Asociar** (Depurador local de Windows y Depurador remoto de Windows) | Especifica si se debe iniciar o asociar a la aplicación. La configuración predeterminada es No. |
| **Nombre de servidor remoto** (Depurador remoto de Windows) | Especifica el nombre de un equipo (que no es el suyo) en el que desea depurar una aplicación.<br /><br /> La macro de compilación RemoteMachine está establecida en el valor de esta propiedad; para obtener más información, vea [Macros comunes para propiedades y comandos de compilación](/cpp/ide/common-macros-for-build-commands-and-properties). |
| **Conexión** (Depurador remoto de Windows) | Permite intercambiar entre los tipos de conexión estándar y sin autenticación para la depuración remota. Especifique el nombre de un equipo remoto en el cuadro **Nombre de servidor remoto**. Entre los tipos de conexión se incluyen los siguientes:<br /><br /> -   **Remoto con autenticación de Windows**<br />-   **Remoto sin autenticación**<br /><br /> **Nota**: La depuración sin autenticación puede dejar el equipo remoto expuesto a infracciones de seguridad. El modo de autenticación de Windows es más seguro.<br /><br /> Para obtener más información, vea [Remote Debugging](../debugger/remote-debugging.md) (Instalación de la depuración remota). |
| **Dirección URL HTTP** (Depurador de servicio web y Depurador de explorador web) | Especifica la dirección URL en la que se encuentra el proyecto que se depura. |
| **Tipo de depurador** | Especifica el tipo de depurador que se usará: **Solo nativo**, **solo administrado**, **solo GPU**, **mixto**, **automática** (valor predeterminado), o **Script**.<br /><br /> -   **Solo nativo** es para código de C++ no administrado.<br />-   **Solo administrado** es para código que se ejecuta bajo Common Language Runtime (código administrado).<br />-   **Mixto** invoca depuradores para código administrado y no administrado.<br />-   **Automático** determina el tipo de depurador en función de la información del compilador y del archivo EXE.<br />-   **Script** invoca a un depurador para los scripts.<br />-   **Solo GPU** es para el código de C++ AMP que se ejecuta en un dispositivo GPU o en el rasterizador de referencia de DirectX. Consulte [código de depuración de GPU](../debugger/debugging-gpu-code.md). |
| **Entorno** (depurador Local de Windows y depurador remoto de Windows) | Especifica las variables de entorno del programa que se depura. Utilice la sintaxis de variables de entorno estándar (por ejemplo, `PATH="%SystemRoot%\..."`). Estas variables reemplazan el entorno del sistema o se fusionan mediante combinación con este, en función de la configuración **Fusionar mediante combinación entorno**. Cuando haga clic en la columna configuración, "Editar …" aparece. Seleccione este vínculo para editar las variables de entorno. |
| **Combinar entorno** (Depurador local de Windows) | Determina si las variables especificadas en el cuadro **Entorno** se combinarán con el entorno definido por el sistema operativo. La configuración predeterminada es Sí. |
| **Depuración de SQL** (todos menos el Depurador de clúster MPI) | Habilita la depuración de procedimientos SQL desde la aplicación de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. La configuración predeterminada es No. |
| **Tipo de acelerador de depuración** (solo depuración de GPU) | Especifica el dispositivo GPU que se debe usar para la depuración. La instalación de controladores de dispositivo para dispositivos GPU compatibles agregará opciones adicionales. La configuración predeterminada es **GPU - Emulador de software**. |
| **Comportamiento de interrupción predeterminado de GPU** (solo para la depuración de GPU) | Especifica si se debe generar un evento de punto de interrupción para cada subproceso de una deformación SIMD. La configuración predeterminada consiste en generar el evento de punto de interrupción una sola vez por deformación. |
| **Acelerador predeterminado de AMP** | Especifica el acelerador predeterminado de AMP al depurar código de GPU. Elija **Acelerador de software WARP** para investigar si un problema está provocado por el hardware o por un controlador en lugar de por el código. |
| **Directorio de implementación** (Depurador remoto de Windows) | Especifica la ruta de acceso en el equipo remoto en la que se copiará el resultado del proyecto antes del lanzamiento. La ruta de acceso puede ser un recurso compartido de red en el equipo remoto, o bien una ruta de acceso a una carpeta del equipo remoto. La configuración predeterminada está vacía, lo que significa que el resultado del proyecto no se copia en un recurso compartido de red. Para habilitar la implementación de los archivos, también debe activar la casilla **Implementar** en el cuadro de diálogo Administrador de configuración. Para obtener más información, vea [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md). |
| **Archivos adicionales para implementar** (Depurador remoto de Windows) | Si se establece la propiedad directorio de implementación, esto es una lista delimitada por punto y coma de archivos adicionales para copiar en el directorio de implementación. La configuración predeterminada está vacía, lo que significa que no se copia ningún archivo adicional en el directorio de implementación. Para habilitar la implementación de los archivos, también debe activar la casilla **Implementar** en el cuadro de diálogo Administrador de configuración. Para obtener más información, vea [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md). |
| **Implementar bibliotecas de depuración en tiempo de ejecución de Visual C++** (Depurador remoto de Windows) | Si se establece la propiedad Directorio de implementación, especifica si las bibliotecas de tiempo de ejecución de depuración de Visual C++ de la plataforma actual se deben copiar en el recurso compartido de red. El valor predeterminado es Sí. |
  
## <a name="cc-folder-general-category"></a>Carpeta C/C++ (categoría General)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Formato de la información de depuración** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Especifica el tipo de información de depuración que se va a crear para el proyecto.<br /><br /> La opción predeterminada (/ZI) crea una base de datos de programa (PDB) en formato compatible con Editar y continuar. Para obtener más información, vea [/Z7, /Zd, /Zi, /ZI (Formato de la información de depuración)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Carpeta C/C++ (categoría Optimización)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Optimization**|Especifica si el compilador debe optimizar el código que produce. La optimización cambia el código que se ejecuta. El código optimizado ya no coincide con el código fuente, lo que dificulta la depuración.<br /><br /> La opción predeterminada **Deshabilitado (/0d)** suprime la optimización. Puede desarrollar con la optimización desactivada y activarla posteriormente cuando cree la versión de producción del código.|  
  
## <a name="linker-folder-debugging-category"></a>Carpeta Vinculador (categoría Depuración)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Generar información de depuración** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Indica al vinculador que incluya información de depuración, que tendrá el formato especificado mediante [/Z7, /Zd, Zi o /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
|**Generar archivo de base de datos de programas** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|En este cuadro, especifique el nombre de un archivo de programa (PDB) de la base de datos. Debe seleccionar ZI o /Zi en Formato de la información de depuración.|  
|**Quitar símbolos privados** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Especifique el nombre de un archivo PDB en este cuadro si no desea incluir símbolos privados en dicho archivo. Esta opción crea un segundo archivo PDB al compilar la imagen del programa con cualquiera del compilador o vinculador opciones que generan un archivo PDB, como/Debug, / Z7, / Zd. O /Zi. En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes. Para obtener más información, vea [/PDBSTRIPPED (Quitar símbolos privados)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Generar archivo de asignaciones** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Indica al vinculador que genere un archivo de asignaciones durante la vinculación. La configuración predeterminada es No. Para obtener más información, consulte [/MAP (generar archivo de asignaciones)](/cpp/build/reference/map-generate-mapfile).|  
|**Asignación de nombre de archivo** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*nombre*)|Si elige Generar archivo de asignaciones, puede especificar el archivo de asignaciones en este cuadro. Para obtener más información, consulte [/MAP (generar archivo de asignaciones)](/cpp/build/reference/map-generate-mapfile).|  
|**Exportaciones de asignaciones** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Incluye las funciones exportadas en el archivo de asignaciones. La configuración predeterminada es No. Para obtener más información, consulte [/MAPINFO (incluir información en el archivo de asignaciones)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Ensamblado depurable** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Especifica la configuración de la opción /ASSEMBLYDEBUG del vinculador. Los valores posibles son:<br /><br /> -   **No se emitió el atributo Debuggable**.<br />-   **Seguimiento de runtime y deshabilitar optimizaciones (/ASSEMBLYDEBUG)**. Esta es la configuración predeterminada.<br />-   **No realizar seguimiento del motor en tiempo de ejecución ni habilitar optimizaciones (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<heredar de primario o valores predeterminados del proyecto>**.<br />-   Para obtener más información, vea [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Puede cambiar esta configuración en la carpeta Propiedades de configuración (categoría Depuración) mediante programación a través de la interfaz de Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Para obtener más información, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Otras configuraciones de proyecto

Para depurar los tipos de proyecto, como las bibliotecas estáticas y archivos DLL, el proyecto de Visual Studio debe ser capaz de encontrar los archivos correctos. Cuando el código fuente está disponible, puede agregar las bibliotecas estáticas y archivos DLL como proyectos independientes a la misma solución, para facilitar la depuración. Para obtener información sobre cómo crear estos tipos de proyecto, vea [creación y uso de una biblioteca de vínculos dinámicos (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) y [creación de una biblioteca estática mediante](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Con el código fuente disponible, también puede crear un nuevo proyecto de Visual Studio eligiendo **archivo** > **New** > **proyecto del código existente**.

Para depurar archivos DLL que son externas a su proyecto, consulte [proyectos DLL de depuración](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Si tiene que depurar su propio proyecto DLL, pero no tiene acceso al proyecto de la aplicación que realiza la llamada, consulte [cómo depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)   
 [Crear y administrar proyectos de Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Macros comunes para propiedades y comandos de compilación](/cpp/ide/common-macros-for-build-commands-and-properties)