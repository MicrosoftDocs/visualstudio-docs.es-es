---
title: Configuración de proyectos para una configuración de depuración de C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 404bbc753b2729ad5ec7625fa01803b8a6bdf5c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800801"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Configuración del proyecto para una configuración de depuración de C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede cambiar la configuración del proyecto para una configuración de depuración de C o Visual C++ en el **páginas de propiedades** cuadro de diálogo, como se describe en [Cómo: establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). En las tablas siguientes se muestran dónde encontrar valores relacionados con el depurador en el **páginas de propiedades** cuadro de diálogo.  
  
> [!WARNING]
>  La configuración de depuración del proyecto en el **propiedades de configuración/depuración** categoría para las aplicaciones de Windows Store y los componentes que están escritos en C++ son diferentes. Consulte [iniciar una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) en el centro de desarrollo de Windows.  
  
 Especifique el depurador que se va a usar en el **depurador para iniciar** cuadro de lista. La opción determinará qué propiedades serán visibles.  
  
 Cada vez que guarda la solución, la configuración de depuración se escribe y se guarda automáticamente en un archivo "de usuario" (.vcxproj.user).  
  
### <a name="configuration-properties-folder-debugging-category"></a>Carpeta Propiedades de configuración (categoría Depuración)  
  
|**Configuración de**|**Descripción**|  
|-----------------|---------------------|  
|**Depurador para iniciar**|Especifica el depurador que se va a ejecutar, con las opciones siguientes:<br /><br /> -   **Depurador local de Windows**<br />-   **Depurador remoto de Windows**<br />-   **Depurador de explorador Web**<br />-   **Depurador de servicio Web**|  
|**Comando** (depurador Local de Windows)|Especifica el comando usado para iniciar el programa que se está depurando en el equipo local.|  
|**Comando remoto** (depurador remoto de Windows)|La ruta de acceso al archivo .exe en el equipo remoto. Escriba la ruta de acceso como lo haría en el equipo remoto.|  
|**Argumentos de comandos** (depurador Local de Windows y depurador remoto de Windows)|: Especifica los argumentos del comando especificado anteriormente.<br /><br /> Puede utilizar los siguientes operadores de redirección en este cuadro:<br /><br /> < `file`<br /> Lee stdin del archivo.<br /><br /> > `file`<br /> Escribe stdout en el archivo.<br /><br /> >> `file`<br /> Agrega stdout al archivo.<br /><br /> 2> `file`<br /> Escribe stderr en el archivo.<br /><br /> 2>> `file`<br /> Agrega stderr al archivo.<br /><br /> 2> &1<br /> Envía el resultado de stderr (2) a la misma posición que stdout (1).<br /><br /> 1> &2<br /> Envía el resultado de stdout (1) a la misma posición que stderr (2).<br /><br /> En la mayoría de los casos, estos operadores solo pueden utilizarse en aplicaciones de consola.|  
|**Directorio de trabajo**|Especifica el directorio de trabajo del programa que se está depurando en relación con el directorio del proyecto en el que se encuentra el archivo EXE. Si lo deja en blanco, el directorio de trabajo será el directorio del proyecto. Para la depuración remota, el directorio del proyecto estará en el servidor remoto.|  
|**Adjuntar** (depurador Local de Windows y depurador remoto de Windows)|Especifica si se debe iniciar o asociar a la aplicación. La configuración predeterminada es No.|  
|**Nombre del servidor remoto** (depurador remoto de Windows)|Especifica el nombre de un equipo (que no es el suyo) en el que desea depurar una aplicación.<br /><br /> La macro de compilación RemoteMachine está establecida en el valor de esta propiedad; Para obtener más información, consulte [Macros para propiedades y comandos de compilación](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Conexión** (depurador remoto de Windows)|Permite intercambiar entre los tipos de conexión estándar y sin autenticación para la depuración remota. Especifique un nombre de equipo remoto en el **nombre del servidor remoto** cuadro. Entre los tipos de conexión se incluyen los siguientes:<br /><br /> -   **Remoto con autenticación de Windows**<br />-   **Remoto sin autenticación (solo nativo)**<br /><br /> **Tenga en cuenta** la depuración sin autenticación puede dejar el equipo remoto expuesto a infracciones de seguridad. El modo de autenticación de Windows es más seguro.<br /><br /> Para obtener más información, consulte [Remote Debugging Setup](../debugger/remote-debugging.md).|  
|**Dirección URL HTTP** (depurador de servicio y el depurador de explorador Web de Web)|Especifica la dirección URL en la que se encuentra el proyecto que se depura.|  
|**Tipo de depurador**|Especifica el tipo de depurador que se usará: **solo nativo**, **solo administrado**, **solo GPU**, **mixto**, **automática**(valor predeterminado), o **Script**.<br /><br /> -   **Solo nativo** es para código C++ no administrado.<br />-   **Solo administrado** para el código que se ejecuta bajo common language runtime (código administrado).<br />-   **Mixto** invoca depuradores para ambos administrado y código no administrado.<br />-   **Auto** determina el tipo de depurador basándose en información del compilador y EXE.<br />-   **Secuencia de comandos** invoca un depurador de scripts.<br />-   **Solo GPU** es para código C++ AMP que se ejecuta en un dispositivo GPU o en el rasterizador de referencia de DirectX. Consulte [depurar código de GPU](../debugger/debugging-gpu-code.md).|  
|**Entorno** (depurador Local de Windows)|Especifica las variables de entorno del programa que se depura. Utilice la sintaxis de variables de entorno estándar (por ejemplo, `PATH="%SystemRoot%\..."`). Estas variables se invalide el entorno del sistema o se combinan con el entorno del sistema, según la **fusionar mediante combinación entorno** configuración. Cuando se hace clic en la columna de configuración, aparece "Editar…". Haga clic en ese vínculo para modificar las variables de entorno.|  
|**Combinar entorno** (depurador Local de Windows)|Determina si las variables que están especificados en el **entorno** cuadro se combinarán con el entorno definido por el sistema operativo. La configuración predeterminada es Sí.|  
|**Depuración de SQL** (todos menos el depurador de clúster MPI)|Habilita la depuración de procedimientos SQL desde la aplicación de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. La configuración predeterminada es No.|  
|**Tipo de Acelerador de depuración** (solo depuración de GPU)|Especifica el dispositivo GPU que se debe usar para la depuración. La instalación de controladores de dispositivo para dispositivos GPU compatibles agregará opciones adicionales. La configuración predeterminada es "GPU - Emulador de software".|  
|**Comportamiento de punto de interrupción predeterminado de GPU** (solo depuración de GPU)|Especifica si se debe generar un evento de punto de interrupción para cada subproceso de una deformación SIMD. La configuración predeterminada consiste en generar el evento de punto de interrupción una sola vez por deformación.|  
|**Acelerador predeterminado de amp** (solo depuración de GPU)|Especifica el acelerador predeterminado de AMP al depurar código de GPU. Elija **Acelerador de software WARP** para investigar si un problema está provocado por el hardware o un controlador en lugar del código.|  
|**Directorio de implementación** (depurador remoto de Windows)|Especifica la ruta de acceso en el equipo remoto en la que se copiará el resultado del proyecto antes del lanzamiento. La ruta de acceso puede ser un recurso compartido de red en el equipo remoto, o bien una ruta de acceso a una carpeta del equipo remoto. La configuración predeterminada está vacía, lo que significa que el resultado del proyecto no se copia en un recurso compartido de red. Para habilitar la implementación de los archivos, también debe seleccionar la **implementar** casilla de verificación en el cuadro de diálogo Administrador de configuración. Para obtener más información, consulte [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).|  
|**Archivos adicionales para implementar** (depurador remoto de Windows)|Si se establece la propiedad Directorio de implementación, será una lista delimitada por punto y coma de archivos adicionales que se deben copiar en el directorio de implementación. La configuración predeterminada está vacía, lo que significa que no se copia ningún archivo adicional en el directorio de implementación. Para habilitar la implementación de los archivos, también debe seleccionar la **implementar** casilla de verificación en el cuadro de diálogo Administrador de configuración. Para obtener más información, consulte [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).|  
|**Implementar bibliotecas de depuración de Visual C++ en tiempo de ejecución** (depurador remoto de Windows)|Si se establece la propiedad Directorio de implementación, especifica si las bibliotecas de tiempo de ejecución de depuración de Visual C++ de la plataforma actual se deben copiar en el recurso compartido de red. El valor predeterminado es Sí.|  
  
### <a name="cc-folder-general-category"></a>Carpeta C/C++ (categoría General)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Formato de información de depuración** ([/Z7, / Zd, Zi, /ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Especifica el tipo de información de depuración que se va a crear para el proyecto.<br /><br /> La opción predeterminada (/ZI) crea una base de datos de programa (PDB) en formato compatible con Editar y continuar. Para obtener más información, consulte [/Z7, / Zd, / Zi, /ZI (formato de la información de depuración)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Carpeta C/C++ (categoría Optimización)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Optimization**|Especifica si el compilador debe optimizar el código que produce. La optimización cambia el código que se ejecuta. El código optimizado ya no coincide con el código fuente. Por tanto, la depuración resulta complicada.<br /><br /> La opción predeterminada (**deshabilitado (/ 0d**) suprime la optimización. Puede desarrollar con la optimización desactivada y activarla posteriormente cuando cree la versión de producción del código.|  
  
### <a name="linker-folder-debugging-category"></a>Carpeta Vinculador (categoría Depuración)  
  
|Parámetro|Descripción|  
|-------------|-----------------|  
|**Generar información de depuración** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Indica al vinculador que incluya información de depuración, que tendrá el formato especificado mediante /Z7, /Zd, Zi o /ZI.|  
|**Generar archivo de base de datos de programa** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|Especifique el nombre de un archivo PDB en este cuadro. Debe seleccionar ZI o /Zi en Formato de la información de depuración.|  
|**Quitar símbolos privados** ([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|Especifique el nombre de un archivo PDB en este cuadro si no desea incluir símbolos privados en dicho archivo. Esta opción crea un segundo archivo de base de datos de programa (PDB) al generar la imagen de un programa con cualquiera de las opciones del compilador o el vinculador que generan archivos PDB, como /DEBUG, /Z7 o /Zd. O /Zi. En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes. Para obtener más información, consulte [/PDBSTRIPPED (quitar símbolos privados)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Generar archivo de asignaciones** ([/MAP](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Indica al vinculador que genere un archivo de asignaciones durante la vinculación. La configuración predeterminada es No. Para obtener más información, consulte [/MAP (generar archivo de asignaciones)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Asignación de nombre de archivo** ([/MAP:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*nombre*)|Si elige Generar archivo de asignaciones, puede especificar el archivo de asignaciones en este cuadro. Para obtener más información, consulte [/MAP (generar archivo de asignaciones)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Exportaciones de asignaciones** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Incluye las funciones exportadas en el archivo de asignaciones. La configuración predeterminada es No. Para obtener más información, consulte [/MAPINFO (incluir información en el archivo de asignaciones)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Ensamblado depurable** ([/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Especifica la configuración de la opción /ASSEMBLYDEBUG del vinculador. Los valores posibles son los siguientes:<br /><br /> -   **Sin el atributo debuggable**.<br />-   **En tiempo de ejecución seguimiento y deshabilitar optimizaciones (/ ASSEMBLYDEBUG)**. Esta es la configuración predeterminada.<br />-   **Ningún optimizations(/ASSEMBLYDEBUG:DISABLE) en tiempo de ejecución, seguimiento y habilitar**.<br />-   **\<heredar de primario o valores pred >**.<br />-Para obtener más información, consulte [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Puede cambiar esta configuración en la carpeta Propiedades de configuración (categoría Depuración) mediante programación a través de la interfaz de Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Para obtener más información, consulta <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Creación y administración de proyectos de Visual C++](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (Agregar DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Macros comunes para propiedades y comandos de compilación](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



