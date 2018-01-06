---
title: "GUID e identificadores de menús de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69ad8f62931b628582c73a3e370a86611795caa6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e identificadores de menús de Visual Studio
Este tema enumera los valores GUID y el ID de los menús y los grupos en la barra de menús de Visual Studio. Estos valores se definen en archivos de vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [IDE-Defined comandos, menús y grupos](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obtener más información sobre cómo trabajar con objetos de entorno (IDE) de desarrollo integrado que se definen en archivos de vsct, consulte [extender menús y comandos de](../../extensibility/extending-menus-and-commands.md).  
  
 Los menús y los grupos en la barra de menús de Visual Studio usan el GUID `guidSHLMainMenu`. Las propias barras de menús tienen un Id. de `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupos en la barra de menús de Visual Studio  
 Para agregar un menú a la barra de menús, seleccione uno de estos grupos como su elemento primario.  
  
|Agrupar|Id.|  
|-----------|--------|  
|Ver/Editar/archivo|IDG_VS_MM_FILEEDITVIEW|  
|Refactorización|IDG_VS_MM_REFACTORING:|  
|Proyecto|IDG_VS_MM_PROJECT|  
|Compilar|IDG_VS_MM_BUILDDEBUGRUN|  
|Formato/Tools|IDG_VS_MM_TOOLSADDINS|  
|Ventana/Ayuda/Community|IDG_VS_MM_WINDOWHELP|  
|AddIns|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menús en la barra de menús de Visual Studio  
 Para agregar un grupo a un menú de Visual Studio existente, seleccione uno de los siguientes menús como su elemento primario. Submenús no se incluyen en esta lista.  
  
|Menú|Id.|  
|----------|--------|  
|Archivo|IDM_VS_MENU_FILE|  
|Editar|IDM_VS_MENU_EDIT|  
|Ver|IDM_VS_MENU_VIEW|  
|Refactorizar|IDM_VS_MENU_REFACTORING|  
|Proyecto|IDM_VS_MENU_PROJECT|  
|Compilar|IDM_VS_MENU_BUILD|  
|Formato|IDM_VS_MENU_FORMAT|  
|Herramientas|IDM_VS_MENU_TOOLS|  
|Ventana|IDM_VS_MENU_WINDOW|  
|AddIns|IDM_VS_MENU_ADDINS|  
|comunidad|IDM_VS_MENU_COMMUNITY|  
|Ayuda|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Grupos de menús de Visual Studio  
 Las listas siguientes muestran los grupos que descienden directamente desde los menús en la barra de menús de Visual Studio. Es la forma más rápida de agregar un comando a un menú de Visual Studio establecer uno de estos grupos como el elemento primario. Grupos que descienden de submenús no aparecen en esta sección.  
  
### <a name="file-menu-groups"></a>Grupos de menús de archivo  
  
|Agrupar|Id.|  
|-----------|--------|  
|Nuevo o abrir|IDG_VS_FILE_FILE|  
|Add|IDG_VS_FILE_ADD|  
|Soluciones|IDG_VS_FILE_SOLUTION|  
|Varios|IDG_VS_FILE_MISC|  
|Guardar|IDG_VS_FILE_SAVE|  
|Cambiar nombre|IDG_VS_FILE_RENAME|  
|Explorador|IDG_VS_FILE_BROWSER|  
|Imprimir|IDG_VS_FILE_PRINT|  
|Usados más recientemente|IDG_VS_FILE_MRU|  
|Mover|IDG_VS_FILE_MOVE|  
|Salir|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Editar grupos de menús  
  
|Agrupar|Id.|  
|-----------|--------|  
|Deshacer/rehacer|IDG_VS_EDIT_UNDOREDO|  
|Cortar/Copiar/Pegar|IDG_VS_EDIT_CUTCOPY|  
|Seleccionar|IDG_VS_EDIT_SELECT|  
|GoTo|IDG_VS_EDIT_GOTO|  
|Find|IDG_VS_EDIT_FIND|  
|de la empresa|IDG_VS_EDIT_OBJECTS|  
|Verbos de OLE|IDG_VS_EDIT_OLEVERBS|  
|Comando también|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Refactorizar grupos de menús  
  
|Agrupar|Id.|  
|-----------|--------|  
|Común|IDG_REFACTORING_COMMON|  
|Avanzadas|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Ver grupos de menú  
  
|Agrupar|Id.|  
|-----------|--------|  
|Código del formulario|IDG_VS_VIEW_FORMCODE|  
|Explorador|IDG_VS_VIEW_BROWSER|  
|Definir vistas|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|Diseñar la arquitectura de Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Windows de la organización|IDG_VS_VIEW_ORG_WINDOWS|  
|Explorador de código|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Windows de desarrollo|IDG_VS_VIEW_DEV_WINDOWS|  
|Barras de herramientas|IDG_VS_VIEW_TOOLBARS|  
|Símbolos|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Navegar|IDG_VS_VIEW_NAVIGATE|  
|Navegue pequeño|IDG_VS_VIEW_SMALLNAVIGATE|  
|Examinador de objetos|IDG_VS_VIEW_OBJBRWSR|  
|Comando también|IDG_VS_VIEW_COMMANDWELL|  
|Páginas de propiedades|IDG_VS_VIEW_PROPPAGES|  
|Refresh|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Grupos de menús de proyecto  
  
|Agrupar|Id.|  
|-----------|--------|  
|Varios agregar|IDG_VS_PROJ_MISCADD|  
|Add|IDG_VS_PROJ_ADD|  
|Carpeta|IDG_VS_PROJ_FOLDER|  
|Descargar y volver a cargar|IDG_VS_PROJ_UNLOADRELOAD|  
|Referencia|IDG_VS_PROJ_REFERENCE|  
|Opciones|IDG_VS_PROJ_OPTIONS|  
|Configuración|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Crear grupos de menús  
  
|Agrupar|Id.|  
|-----------|--------|  
|Soluciones|IDG_VS_BUILD_SOLUTION|  
|Selección|IDG_VS_BUILD_SELECTION|  
|Optimización guiada por perfiles|IDG_VS_PGO_SELECTION|  
|Varios|IDG_VS_BUILD_MISC|  
|Cancelar|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Grupos de menús de herramientas  
  
|Agrupar|Id.|  
|-----------|--------|  
|Línea de comandos|IDG_VS_TOOLS_CMDLINE|  
|Fragmentos de código|IDG_VS_TOOLS_SNIPPETS|  
|Subconjunto de objeto|IDG_VS_TOOLS_OBJSUBSET|  
|Opciones|IDG_VS_TOOLS_OPTIONS|  
|Otras 2|IDG_VS_TOOLS_OTHER2|  
|Herramientas externas|IDG_VS_TOOLS_EXT_TOOLS|  
|Personalizaciones externas|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Grupos de menús de la ventana  
  
|Agrupar|Id.|  
|-----------|--------|  
|Nuevo|IDG_VS_WINDOW_NEW|  
|Acoplar o de cierre|IDG_VS_DOCKCLOSE|  
|Acoplar u ocultar|IDG_VS_DOCKHIDE|  
|Organizar|IDG_VS_WINDOW_ARRANGE|  
|Navegación|IDG_VS_WINDOW_NAVIGATION|  
|Lista|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Ayudar a los grupos de menú  
  
|Agrupar|Id.|  
|-----------|--------|  
|Muestras|IDG_VS_HELP_SAMPLES|  
|Compatibilidad|IDG_VS_HELP_SUPPORT|  
|Acerca de|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Submenús de menús de Visual Studio  
 La jerarquía siguiente muestra los submenús que están asociados a los menús en la barra de menús de Visual Studio. Dado que un grupo puede tener un menú como su elemento primario, cada submenú debe descienden de un grupo en un menú, en lugar de directamente desde el menú. Para obtener más información sobre la relación entre los menús, los grupos y los submenús, consulte [agregar un submenú a un menú](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Los nombres de los menús en la barra de menús de Visual Studio no se muestran por separado en esta jerarquía porque puede inferir a partir la convención de nomenclatura para los grupos en el IDE, como se indica a continuación: IDG_VS_*nombre del menú*_*denombredegrupo*.  
  
|Grupo primario|Submenú|Grupos secundarios|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Vea también  
 [GUID e identificadores de barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)