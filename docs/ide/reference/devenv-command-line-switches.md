---
title: "Modificadores de línea de comandos para Devenv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f06722f4a6192323d92ce6828b25bc57666de8bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="devenv-command-line-switches"></a>Modificadores de línea de comandos para Devenv
Devenv permite establecer diversas opciones para el entorno de desarrollo integrado (IDE), así como compilar, depurar e implementar proyectos, desde la línea de comandos. Utilice estos modificadores para ejecutar el IDE desde un script o un archivo .bat (por ejemplo, un script de compilación nocturna) o para iniciar el IDE con una configuración determinada.  
  
> [!NOTE]
>  Para las tareas relacionadas con la compilación, se recomienda usar MSBuild en lugar de devenv. Para obtener más información, vea [Referencia de la línea de comandos](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Debe ejecutar devenv como administrador para poder usar los modificadores [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md).  
  
## <a name="devenv-switch-syntax"></a>Sintaxis de los modificadores de devenv  
 De forma predeterminada, los comandos devenv pasan modificadores a la utilidad devenv.com.  
  
 La utilidad devenv.com se ocupa del envío de los resultados a través de secuencias del sistema estándar, como `stdout` y `stderr`, y determina la redirección de E/S adecuada al capturar el resultado, por ejemplo, a un archivo .txt. Los comandos que comienzan por `devenv.exe` pueden utilizar los mismos modificadores, pero se enviarán al programa devenv.exe, omitiendo la utilidad devenv.com.  
  
 Las reglas de sintaxis de los modificadores de `devenv` son similares a las de otros programas de línea de comandos de DOS. Las siguientes reglas sintácticas se aplican a todos los modificadores de `devenv` y sus argumentos:  
  
-   Los comandos comienzan por `devenv`.  
  
-   Los modificadores no distinguen mayúsculas de minúsculas.  
  
-   Cuando se especifica una solución o un proyecto, el primer argumento es el nombre del archivo de solución o del archivo de proyecto, incluida la ruta de acceso del archivo.  
  
-   Si el primer argumento es un archivo que no es una solución ni un proyecto, ese archivo se abrirá en el editor adecuado, en una nueva instancia del IDE.  
  
-   Cuando se indica un nombre de archivo de proyecto en lugar de un nombre de archivo de solución, un comando `devenv` buscará en la carpeta primaria del archivo de proyecto un archivo de solución que tenga el mismo nombre. Por ejemplo, el comando `devenv /build myproject1.vbproj` buscará en la carpeta primaria un archivo de solución denominado "myproject1.sln".  
  
    > [!NOTE]
    >  En su carpeta primaria debe haber un archivo de solución, y solamente uno, que haga referencia a este proyecto. Si la carpeta primaria no contiene ningún archivo de solución que hace referencia a este proyecto, o si contiene dos o más archivos de solución que hacen referencia a él, se creará en ella un archivo de solución temporal con el nombre de este proyecto y que haga referencia a él.  
  
-   Si las rutas de acceso y los nombres de archivo contienen espacios en blanco, deben incluirse entre comillas dobles (""). Por ejemplo, "c:\project a\\".  
  
-   Inserte un carácter de espacio entre los modificadores y los argumentos de la misma línea. Por ejemplo, el comando **devenv /log output.txt** abre el IDE y envía toda la información de registro de esa sesión a output.txt.  
  
-   No se puede utilizar la sintaxis de coincidencia de patrones en los comandos de `devenv`.  
  
## <a name="devenv-switches"></a>Modificadores de devenv  
 Utilice los modificadores de línea de comandos siguientes para mostrar el IDE y realizar la tarea descrita.  
  
|Modificador de la línea de comandos|Description|  
|-------------------------|-----------------|  
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Inicia el IDE y ejecuta el comando especificado.|  
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Carga un archivo ejecutable de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bajo el control del depurador. Este modificador no está disponible para los archivos ejecutables de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Para obtener más información, vea [Iniciar automáticamente un proceso en el depurador](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) o `/l`|Establece el idioma predeterminado del IDE. Si el idioma especificado no está incluido en la instalación de Visual Studio, se omitirá este valor.|  
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y registra toda la actividad en el archivo de registro.|  
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) o `/r`|Compila y ejecuta la solución especificada.|  
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Compila y ejecuta la solución especificada, minimiza el IDE cuando se ejecuta la solución y cierra el IDE una vez finalizada la ejecución de la solución.|  
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Hace que el IDE use las variables de entorno PATH, INCLUDE y LIB para la compilación de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] en lugar de la configuración especificada en la sección Directorios de VC++ de las opciones de **Proyectos** del cuadro de diálogo **Opciones**. Para obtener más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|  
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Abre los archivos especificados en una instancia en ejecución de esta aplicación. Si no hay ninguna instancia en ejecución, iniciará una nueva instancia con un diseño de ventanas simplificado.|  
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Inicia una instancia del IDE de Visual Studio sin cargar el complemento especificado.|  
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro y solo carga el entorno y los servicios predeterminados, así como las versiones de paquetes de terceros suministradas.|  
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Borra todas las etiquetas SkipLoading agregadas a VSPackages por usuarios que desean evitar problemas al cargar VSPackages.|  
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Fuerza a Visual Studio a fusionar mediante combinación los metadatos de recursos que describen los menús, las barras de herramientas y los grupos de comandos de todos los VSPackages disponibles.|  
  
 Utilice los modificadores de la línea de comandos siguientes para realizar la tarea descrita. Estos modificadores de la línea de comandos no muestran el IDE.  
  
|Modificador de la línea de comandos|Description|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Muestra ayuda para los modificadores de devenv en la **ventana de símbolo del sistema**.<br /><br /> **Devenv /?**|  
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Compila la solución o el proyecto especificado según la configuración de la solución especificada.<br /><br /> **Devenv myproj.csproj /build**|  
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Elimina los archivos creado por el comando de compilación, sin afectar a los archivos de código fuente.<br /><br /> **Devenv myproj.csproj /clean**|  
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Compila la solución, junto con los archivos necesario para la implementación, según la configuración de soluciones.<br /><br /> **Devenv myproj.csproj /deploy**|  
|[/Diff](../../ide/reference/diff.md)|Compara dos archivos.  Toma cuatro parámetros: SourceFile, TargetFile, SourceDisplayName (opcional), TargetDisplayName (opcional).|  
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Registra las plantillas de proyecto o elemento incluidas en *\<VisualStudioInstallDir>*\Common7\IDE\ProjectTemplates o *\<VisualStudioInstallDir>*\Common7\IDE\ItemTemplates para que se pueda obtener acceso a ellas a través de los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**.<br /><br /> **Devenv /InstallVSTemplates**|  
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Permite especificar un archivo para recibir los errores al compilar.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|  
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Proyecto que se va a compilar, limpiar o implementar. Solo se puede utilizar este modificador si también se ha indicado el modificador /build, /rebuild, /clean o /deploy.|  
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Especifica la configuración de proyecto que se va a compilar o implementar. Solo se puede utilizar este modificador si también se ha indicado el modificador /project.|  
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Limpia y, a continuación, compila la solución o el proyecto especificado según la configuración de la solución especificada.|  
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Restaura la configuración predeterminada de Visual Studio. Opcionalmente, restablece la configuración del archivo .vssettings especificado.|  
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Notifica a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que combine los paquetes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.|  
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Actualiza el archivo de solución especificado y todos sus archivos de proyecto, o el archivo de proyecto especificado, a los formatos actuales de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para estos archivos.|  
  
## <a name="see-also"></a>Vea también  
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)