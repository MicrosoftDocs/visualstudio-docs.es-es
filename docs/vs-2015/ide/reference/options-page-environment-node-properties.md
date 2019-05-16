---
title: Página de opciones, Propiedades de nodo Entorno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64deddd3ae8323298ad04e5a1a3a78e93c21a87a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674716"
---
# <a name="options-page-environment-node-properties"></a>Página de opciones, Propiedades de nodo Entorno
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este documento se describen las páginas (o colecciones de propiedades) asociadas a la categoría **Entorno**, `DTE.Properties("Environment", <Property Page>)`, del cuadro de diálogo **Opciones**. El título de cada subsección es la llamada que se usa para acceder a la colección Propiedades y, en la tabla de cada subsección, se muestran las propiedades que se encuentran en la colección.  
  
## <a name="general"></a>General  
 `DTE.Properties("Environment", "General")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|ShowStatusBar|Get/Set (Boolean)|Determina si la barra de estado está visible.|  
|WindowMenuContainsNItems|Get/Set (Short)|Determina cómo se encuentran las ventanas de documento en la parte inferior del menú Ventana.|  
|MRUListContainsNItems|Get/Set (Short)|Determina cuántos archivos se muestran en el submenú "Usados más recientemente".|  
|Animaciones|Get/Set (Boolean)|Determina si el entorno de desarrollo integrado (IDE) utiliza animación en la barra de estado.|  
|AnimationSpeed|Get/Set (Short)||  
|AutoAdjustExperience|Get/Set (Boolean)|Ajusta automáticamente la experiencia visual según el rendimiento del cliente.|  
|RichClientExperienceOptions|Get/Set (Enum)|Habilita la experiencia visual de cliente enriquecida con los valores de <xref:EnvDTE100.vsRichClientExperienceOptions>.|  
|CloseButtonActiveTabOnly|Get/Set (Boolean)|Determina si el botón **Cerrar** aparece solo en la pestaña activa.|  
|AutohidePinActiveTabOnly|Get/Set (Boolean)|Determina si el botón **Ocultar automáticamente** afecta solo a la pestaña activa.|  
  
## <a name="add-inmacros-security"></a>Seguridad de macros/complementos  
 `DTE.Properties("Environment", "AddinMacrosSecurity")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|MacrosEnabled|Get/Set (Boolean)|Permite la ejecución de macros.|  
|AddinsEnabled|Get/Set (Boolean)|Permite cargar complementos.|  
|LoadAddinsFromTheWeb|Get/Set (Boolean)|Permite cargar complementos desde una dirección URL de la Web.|  
  
## <a name="documents"></a>Documentos  
 `DTE.Properties("Environment", "Documents")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|ReuseSavedActiveDocWindow|Get/Set (Boolean)|Determina si al abrir un nuevo archivo se vuelve a utilizar la ventana de documento actual si se guarda el documento actual. `false` significa que siempre se abrirá una nueva ventana de documento para cada documento que se abra.|  
|DetectFileChangesOutsideIDE|Get/Set (Boolean)|Determina si el entorno vuelve a cargar automáticamente los archivos abiertos en el IDE cuando el sistema operativo notifica al IDE de que los archivos se modificaron en el disco.|  
|AutoloadExternalChanges|Get/Set (Boolean)|Determina si las modificaciones externas detectadas para abrir los documentos vuelven a cargar automáticamente el archivo modificado si no se modifica el documento abierto. Si se modifica el documento abierto y esta propiedad es`true`, el IDE muestra un mensaje como si esta propiedad fuera `false`.|  
|InitializeOpenFileFromCurrentDocument|Get/Set (Boolean)|Determina si el comando <xref:EnvDTE.DTEClass.OpenFile%2A> propaga el directorio y el nombre de archivo desde el último documento activo o desde el último lugar en el que abrió un archivo.|  
|MiscFilesProjectSavesLastNItems|Get/Set (Short)|Determina cuántos archivos graba el proyecto Archivos varios. Como resultado, puede ver lo último que abrió como archivos varios en el disco cuando vuelva a usar el IDE.|  
|ShowMiscFilesProject|Get/Set (Boolean)|Determina si se muestra el proyecto Archivos varios.|  
|CheckForConsisentLineEndings|Get/Set (Boolean)|Comprueba que los finales de línea son coherentes en la carga de archivos.|  
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boolean)|Guarda documentos como Unicode cuando no se pueden guardar los datos en la página de códigos.|  
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boolean)|Muestra una advertencia cuando Deshacer global va a modificar otros archivos editados.|  
|AllowEditingReadOnlyFiles|Get/Set (Boolean)|Permite la edición de archivos de solo lectura, pero muestra una advertencia cuando se produce un intento de guardarlos.|  
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Posición correcta en la pestaña en la que se va a insertar el documento abierto.|  
  
## <a name="extension-manager"></a>Administrador de extensiones  
 `DTE.Properties("Environment", "ExtensionManager")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|EnableAdminExtensions|Get/Set (Boolean)|Carga las extensiones por usuario cuando Visual Studio se ejecuta con las credenciales de administrador. Visual Studio debe reiniciarse después de que este valor cambie.|  
|EnableOnline|Get/Set (Boolean)|Habilita el acceso a las extensiones de la Galería de Visual Studio.|  
|AutomaticallyCheckForUpdates|Get/Set (Boolean)|Comprueba automáticamente si hay actualizaciones de las extensiones instaladas.|  
  
## <a name="find-and-replace"></a>Buscar y reemplazar  
 `DTE.Properties("Environment", "FindAndReplace")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|ShowWarningMessages|Get/Set (Boolean)|Muestra mensajes de advertencia.|  
|InitializeFromEditor|Get/Set (Boolean)|Rellena automáticamente el cuadro **Buscar** con texto del editor.|  
|ShowMessageBoxes|Get/Set (Boolean)|Muestra mensajes informativos.|  
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boolean)|Oculta la ventana **Buscar y reemplazar** después de localizar una coincidencia con **Búsqueda rápida** o **Reemplazo rápido**.|  
  
## <a name="import-and-export-settings"></a>Importar y exportar configuraciones  
 `DTE.Properties("Environment", "Import and Export Settings")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|TrackTeamSettings|Get/Set (Boolean)|Usar la configuración del archivo especificado por TeamSettingsFile.|  
|TeamSettingsFile|Get/Set (String)|Nombre del archivo que tiene la configuración del equipo.|  
|AutoSaveFile|Get/Set (String)|Nombre del archivo donde se guarda automáticamente la configuración de usuario.|  
  
## <a name="international-settings"></a>Configuración internacional  
 `DTE.Properties("Environment", "International")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|Lenguaje|Get/Set (String)|Valor LCID del idioma actual de Visual Studio.|  
  
## <a name="keyboard"></a>Teclado  
 `DTE.Properties("Environment", "Keyboard")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|Scheme|Get/Set (String)|Devuelve una cadena que contiene un esquema integrado, una cadena que contiene la ruta de acceso completa del archivo .vsk cargado o "(Default)" si no hay ninguno cargado.|  
  
## <a name="projects-and-solution"></a>Proyectos y solución  
 `DTE.Properties("Environment", "ProjectsAndSolution")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|OnRunOrPreview|Get/Set (String)|Determina si el IDE guarda todo antes de obtener una vista previa o ejecutar un proyecto compilado.|  
|ProjectsLocation|Get/Set (String)|Determina el directorio predeterminado donde guarda los proyectos nuevos el cuadro de diálogo **Agregar proyecto**.|  
|ShowOutputWindowBeforeBuild|Get/Set (Boolean)|Determina si al iniciar una compilación se muestra la ventana **Salida**.|  
|ShowTaskListAfterBuild|Get/Set (Boolean)|Determina si, al producirse una operación de compilación incorrecta, se muestra la **Lista de tareas** cuando se completa la compilación.|  
|TrackFileSelectionInExplorer|Get/Set (Boolean)|Determina si se realiza un seguimiento del elemento actual en el **Explorador de soluciones**.|  
|AlwaysShowSolutionNode|Get/Set (Boolean)|Determina si se muestra el nodo de la solución.|  
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boolean)|Determina si las operaciones de almacenamiento están limitadas a los proyectos de inicio y sus archivos dependientes.|  
|ShowAdvancedBuildConfigurations|Get/Set (Boolean)|Determina si se muestran las configuraciones de compilación avanzadas.|  
|ConcurrentBuilds|Get/Set (String)|Determina el número máximo de compilaciones de proyecto paralelas que se pueden producir.|  
|SaveNewProjects|Get/Set (Boolean)|Determina si los nuevos proyectos se guardan automáticamente después de crearse.|  
|PromptForRenameSymbol|Get/Set (Boolean)|Especifica si se debe solicitar el cambio de nombre simbólico cuando se cambia el nombre de los archivos.|  
|OnRunWhenErrors|Get/Set (Enum)|Especifica el comportamiento en ejecución cuando una compilación se completa con errores.|  
|OnRunWhenOutOfDate|Get/Set (Enum)|Especifica el comportamiento en ejecución cuando un proyecto no está actualizado.|  
|ProjectTemplatesLocation|Get/Set (String)|Directorio que contiene las plantillas de proyecto de usuario.|  
|ProjectItemTemplatesLocation|Get/Set (String)|Directorio que contiene las plantillas de elementos de usuario.|  
|DefaultBehaviorForStartupProjects|Get/Set (String)||  
|MSBuildOutputVerbosity|Get/Set (String)|Especifica el nivel de detalle de la salida de compilación.|  
  
## <a name="startup"></a>Inicio  
 `DTE.Properties("Environment", "Startup")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|OnStartUp|Get/Set (Enum)|Acción que se realiza en el inicio, desde <xref:EnvDTE.vsStartUp>, con valores de 0 a 5:<br /><br /> -   0: Abrir la página principal<br />-   1: Cargar última solución cargada<br />-   2: Mostrar el cuadro de diálogo **Abrir proyecto**<br />-   3: Mostrar el cuadro de diálogo **Nuevo proyecto**<br />-   4: Mostrar el entorno vacío<br />-   5: Mostrar página de inicio|  
|StartPageRSSUrl|Get/Set (String)|Dirección URL de la fuente RSS que se usa en el inicio.|  
|StartPageRefreshDownloadedContent|Get/Set (Boolean)|Actualiza la página de inicio después de cada paso del intervalo especificado en StartPageRefreshInterval.|  
|StartPageRefreshInterval|Get/Set (Short)|Intervalo en minutos para actualizar la página de inicio.|  
  
## <a name="tasklist"></a>TaskList  
 `DTE.Properties("Environment", "TaskList")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|ConfirmTaskDeletion|Get/Set (Boolean)|Especifica si se muestra un cuadro de confirmación al eliminar tareas desde la **Lista de tareas**.|  
|WarnOnAddingHiddenItem|Get/Set (Boolean)|Especifica si recibe una advertencia al agregar una tarea de usuario que no se mostrará.|  
|DontShowFilePaths|Get/Set (Boolean)|Especifica si se muestran las rutas de acceso completas al archivo en la Lista de tareas.|  
|CommentTokens|SafeArray|Devuelve una matriz SafeArray de valores de token de comentarios. Cada uno tiene los campos `Name` (cadena) y `Priority` (<xref:EnvDTE.vsTaskPriority>, alto, medio o bajo).|  
  
## <a name="web-browser"></a>Explorador web  
 `DTE.Properties("Environment", "WebBrowser")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|------------------------|-----------|-----------------|  
|HomePage|Get/Set (String)|Representa la dirección URL de la página principal.|  
|SearchPage|Get/Set (String)|Representa la URL de la página de búsqueda.|  
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (origen, diseño, externa).|  
|ViewSourceExternalProgram|Get/Set (String)|Ruta de acceso del visor de origen externo.|  
  
## <a name="see-also"></a>Vea también  
 [Controlar la configuración de opciones](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinar los nombres de los elementos de propiedades en las páginas de opciones](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Página de opciones, Propiedades de nodo Fuentes y colores](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Página de opciones, Propiedades de nodo Editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Opciones de entorno (Cuadro de diálogo)](../../ide/reference/environment-options-dialog-box.md)
