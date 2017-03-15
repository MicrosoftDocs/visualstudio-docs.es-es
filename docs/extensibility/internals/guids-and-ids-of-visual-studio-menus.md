---
title: "GUID e identificadores de men&#250;s de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús de Visual studio"
  - "grupos de Visual studio"
  - "id"
  - "menús existentes"
  - "GUID"
  - "menús"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# GUID e identificadores de men&#250;s de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este tema enumera los valores GUID y el ID de los menús y los grupos en la barra de menús de Visual Studio. Estos valores se definen en los archivos .vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulta [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obtener más información acerca de cómo trabajar con objetos de entorno \(IDE\) de desarrollo integrado que se definen en los archivos .vsct, vea [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
 Los menús y los grupos en la barra de menús de Visual Studio utilizan el GUID `guidSHLMainMenu`. Las propias barras de menús tiene un Id. de `IDM_VS_TOOL_MAINMENU`.  
  
## Grupos en la barra de menús de Visual Studio  
 Para agregar un menú a la barra de menús, establezca uno de estos grupos como su elemento primario.  
  
|Agrupar|Id.|  
|-------------|---------|  
|Archivo, edición, ver|IDG\_VS\_MM\_FILEEDITVIEW|  
|Refactorización|IDG\_VS\_MM\_REFACTORING:|  
|Proyecto|IDG\_VS\_MM\_PROJECT|  
|Compilar|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|Formato y herramientas|IDG\_VS\_MM\_TOOLSADDINS|  
|Ventana, ayuda y Comunidad|IDG\_VS\_MM\_WINDOWHELP|  
|AddIns|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## Menús de la barra de menús de Visual Studio  
 Para agregar un grupo a un menú existente de Visual Studio, establezca uno de los siguientes menús como su elemento primario. Submenús no se incluyen en esta lista.  
  
|Menú|Id.|  
|----------|---------|  
|Archivo|IDM\_VS\_MENU\_FILE|  
|Editar|IDM\_VS\_MENU\_EDIT|  
|Ver|IDM\_VS\_MENU\_VIEW|  
|Refactorizar|IDM\_VS\_MENU\_REFACTORING|  
|Proyecto|IDM\_VS\_MENU\_PROJECT|  
|Compilar|IDM\_VS\_MENU\_BUILD|  
|Formato|IDM\_VS\_MENU\_FORMAT|  
|Herramientas|IDM\_VS\_MENU\_TOOLS|  
|Ventana|IDM\_VS\_MENU\_WINDOW|  
|AddIns|IDM\_VS\_MENU\_ADDINS|  
|comunidad|IDM\_VS\_MENU\_COMMUNITY|  
|Ayuda|IDM\_VS\_MENU\_HELP|  
  
## Grupos de menús de Visual Studio  
 Las listas siguientes muestran los grupos que descienden directamente desde los menús en la barra de menús de Visual Studio. Es la forma más rápida de agregar un comando a un menú de Visual Studio establecer uno de estos grupos como elemento primario. Grupos que descienden de submenús no aparecen en esta sección.  
  
### Grupos de menús de archivo  
  
|Agrupar|Id.|  
|-------------|---------|  
|Nuevo o abrir|IDG\_VS\_FILE\_FILE|  
|Add|IDG\_VS\_FILE\_ADD|  
|Solución|IDG\_VS\_FILE\_SOLUTION|  
|Varios|IDG\_VS\_FILE\_MISC|  
|Guardar|IDG\_VS\_FILE\_SAVE|  
|Cambiar nombre|IDG\_VS\_FILE\_RENAME|  
|Explorador|IDG\_VS\_FILE\_BROWSER|  
|Imprimir|IDG\_VS\_FILE\_PRINT|  
|Usados más recientemente|IDG\_VS\_FILE\_MRU|  
|Mover|IDG\_VS\_FILE\_MOVE|  
|Salir|IDG\_VS\_FILE\_EXIT|  
  
### Editar grupos de menús  
  
|Agrupar|Id.|  
|-------------|---------|  
|Deshacer\/rehacer|IDG\_VS\_EDIT\_UNDOREDO|  
|Cortar, copiar y pegar|IDG\_VS\_EDIT\_CUTCOPY|  
|Seleccionar|IDG\_VS\_EDIT\_SELECT|  
|GoTo|IDG\_VS\_EDIT\_GOTO|  
|Find|IDG\_VS\_EDIT\_FIND|  
|de la empresa|IDG\_VS\_EDIT\_OBJECTS|  
|Verbos OLE|IDG\_VS\_EDIT\_OLEVERBS|  
|Además de comando|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### Refactorizar grupos de menús  
  
|Agrupar|Id.|  
|-------------|---------|  
|Común|IDG\_REFACTORING\_COMMON|  
|Avanzadas|IDG\_REFACTORING\_ADVANCED|  
  
### Ver grupos de menú  
  
|Agrupar|Id.|  
|-------------|---------|  
|Código del formulario|IDG\_VS\_VIEW\_FORMCODE|  
|Explorador|IDG\_VS\_VIEW\_BROWSER|  
|Definir vistas|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Diseñar la arquitectura de Windows|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|Windows de la organización|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|Explorador de código|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|Windows de desarrollo|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|Barras de herramientas|IDG\_VS\_VIEW\_TOOLBARS|  
|Símbolos|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|Navegar|IDG\_VS\_VIEW\_NAVIGATE|  
|Navegue pequeño|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|Examinador de objetos|IDG\_VS\_VIEW\_OBJBRWSR|  
|Además de comando|IDG\_VS\_VIEW\_COMMANDWELL|  
|Páginas de propiedades|IDG\_VS\_VIEW\_PROPPAGES|  
|Actualizar|IDG\_VS\_VIEW\_REFRESH|  
  
### Grupos de menús de proyecto  
  
|Agrupar|Id.|  
|-------------|---------|  
|Varios agregar|IDG\_VS\_PROJ\_MISCADD|  
|Add|IDG\_VS\_PROJ\_ADD|  
|Carpeta|IDG\_VS\_PROJ\_FOLDER|  
|Descargar y volver a cargar|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|Referencia|IDG\_VS\_PROJ\_REFERENCE|  
|Opciones|IDG\_VS\_PROJ\_OPTIONS|  
|Configuración|IDG\_VS\_PROJ\_SETTINGS|  
  
### Crear grupos de menús  
  
|Agrupar|Id.|  
|-------------|---------|  
|Solución|IDG\_VS\_BUILD\_SOLUTION|  
|Selección|IDG\_VS\_BUILD\_SELECTION|  
|Optimización guiada por perfiles|IDG\_VS\_PGO\_SELECTION|  
|Varios|IDG\_VS\_BUILD\_MISC|  
|Cancelar|IDG\_VS\_BUILD\_CANCEL|  
  
### Grupos de menús de herramientas  
  
|Agrupar|Id.|  
|-------------|---------|  
|Línea de comandos|IDG\_VS\_TOOLS\_CMDLINE|  
|Fragmentos de código|IDG\_VS\_TOOLS\_SNIPPETS|  
|Subconjunto de objeto|IDG\_VS\_TOOLS\_OBJSUBSET|  
|Opciones|IDG\_VS\_TOOLS\_OPTIONS|  
|Otros 2|IDG\_VS\_TOOLS\_OTHER2|  
|Herramientas externas|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|Personalizaciones externas|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### Grupos de menús de la ventana  
  
|Agrupar|Id.|  
|-------------|---------|  
|Nuevo|IDG\_VS\_WINDOW\_NEW|  
|Acoplar o cerrar|IDG\_VS\_DOCKCLOSE|  
|Acoplar u ocultar|IDG\_VS\_DOCKHIDE|  
|Organizar|IDG\_VS\_WINDOW\_ARRANGE|  
|Navegación|IDG\_VS\_WINDOW\_NAVIGATION|  
|Lista|IDG\_VS\_WINDOW\_LIST|  
  
### Grupos de menús de ayuda  
  
|Agrupar|Id.|  
|-------------|---------|  
|Muestras|IDG\_VS\_HELP\_SAMPLES|  
|Compatibilidad|IDG\_VS\_HELP\_SUPPORT|  
|Acerca de|IDG\_VS\_HELP\_ABOUT|  
  
## Submenús de menús de Visual Studio  
 La siguiente jerarquía muestra los submenús que están asociados a los menús de la barra de menús de Visual Studio. Dado que sólo un grupo puede tener un menú como su elemento primario, cada submenú debe descender de un grupo en un menú, en lugar de directamente desde el menú. Para obtener más información sobre la relación entre los menús, los grupos y submenús, consulte [Agregar un submenú a un menú](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Los nombres de los menús en la barra de menús de Visual Studio no se muestran por separado en esta jerarquía ya que se puede deducir de la convención de nomenclatura para los grupos en el IDE, como sigue: IDG\_VS\_*nombre del menú*\_*nombre del grupo de*.  
  
|Grupo primario|Submenú|Grupos secundarios|  
|--------------------|-------------|------------------------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1... 6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## Vea también  
 [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)