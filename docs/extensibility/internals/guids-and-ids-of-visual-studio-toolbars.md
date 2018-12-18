---
title: GUID e identificadores de barras de herramientas de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6982835b9d3b6259a47439dbe7b1b9252edc3dbe
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499011"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Barras de herramientas de GUID e identificadores de Visual Studio
En este tema enumera los valores GUID y el Id. de las barras de herramientas que se incluyen en el entorno de desarrollo integrado (IDE) de Visual Studio y de los grupos que contienen. Estos valores se definen en *.vsct* archivos que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Muchas de las barras de herramientas disponibles para Visual Studio no se definen mediante Visual Studio así como sus GUID y los valores de identificador no son públicos. En este tema se muestra sólo las barras de herramientas que se definen en el SDK de Visual Studio *.vsct* archivos.  
  
 Para obtener más información sobre cómo trabajar con objetos IDE que se definen en *.vsct* archivos, consulte [amplían los menús y comandos](../../extensibility/extending-menus-and-commands.md).  
  
 El GUID de las barras de herramientas predeterminada proporcionadas por el IDE de Visual Studio usan `guidSHLMainMenu`, salvo que se especifique lo contrario mediante el uso de `GUID:ID` sintaxis.  
  
## <a name="ide-toolbars"></a>Barras de herramientas del IDE  
 El IDE de Visual Studio proporciona las siguientes barras de herramientas. Se pueden mostrar las barras de herramientas seleccionándolos en la **las barras de herramientas** submenú de la **herramientas** menú. Barras de herramientas en ventanas de herramientas no se incluyen en esta sección.  
  
 Solo los grupos pueden descender directamente desde las barras de herramientas. Para agregar un grupo, establezca a su elemento primario en el GUID y el identificador de la barra de herramientas. Para agregar un botón a una barra de herramientas, establecer a su elemento primario a un grupo en la barra de herramientas.  
  
|Barra de herramientas|Id.|  
|-------------|--------|  
|Estándar|IDM_VS_TOOL_STANDARD|  
|Compilar|IDM_VS_TOOL_BUILD|  
|Editor de texto|IDM_VS_TOOL_TEXTEDITOR|  
|Depuración|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Ubicación de depuración|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Barras de herramientas especiales  
 Estas barras de herramientas definidas por el IDE de Visual Studio, pero realizan funciones especializadas y no hospedan grupos de comandos.  
  
|Barra de herramientas|Id.|  
|-------------|--------|  
|Add (Comando)|IDM_VS_TOOL_ADDCOMMAND|  
|Sin definir|IDM_VS_TOOL_UNDEFINED|  
|Esquema XML|IDM_VS_TOOL_SCHEMA|  
|datos XML|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Grupos en las barras de herramientas IDE  
 Para agregar un botón a una barra de herramientas estándar, establezca uno de los siguientes grupos como su elemento primario. Los grupos se ordenan por la barra de herramientas principal.  
  
### <a name="standard-toolbar-groups"></a>Grupos de la barra de herramientas estándar  
  
|nombre|Id.|  
|----------|--------|  
|Guardar o abrir|IDG_VS_TOOLSB_SAVEOPEN|  
|Cortar/Copiar|IDG_VS_TOOLSB_CUTCOPY|  
|Deshacer/rehacer|IDG_VS_TOOLSB_UNDOREDO|  
|Compilación y ejecución|IDG_VS_TOOLSB_RUNBUILD|  
|Buscar|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Nuevas ventanas|IDG_VS_TOOLSB_NEWWINDOWS|  
|Cargar o guardar|IDG_VS_WINDOWUI_LOADSAVE|  
|Medidor|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Crear grupos de la barra de herramientas  
  
|nombre|Id.|  
|----------|--------|  
|Barra de compilación|IDG_VS_BUILDBAR|  
|Cancelar|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Grupos de barra de herramientas del editor de texto  
  
|nombre|Id.|  
|----------|--------|  
|Finalización|IDM_VS_TOOL_TEXTEDITOR|  
|Sangría|IDG_VS_EDITTOOLBAR_INDENT|  
|Comentario|IDG_VS_EDITTOOLBAR_COMMENT|  
|Marcadores|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Grupos de la barra de herramientas de depuración  
  
|nombre|Id.|  
|----------|--------|  
|Execution|IDM_DEBUG_TOOLBAR|  
|Recorrido paso a paso|IDG_DEBUG_TOOLBAR_STEPPING|  
|Watch|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Grupos de barra de herramientas ubicación de depuración  
  
|nombre|Id.|  
|----------|--------|  
|Ubicación de depuración|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Ventana de herramientas (barras de herramientas)  
 Las barras de herramientas pueden aparecer directamente en el IDE o en las ventanas de herramientas, como **el Explorador de soluciones**. Dado que las ventanas de herramientas no están definidas en *.vsct* archivos, barras de herramientas de ventana de herramienta no ha definido elementos primarios. En su lugar, se colocan en el código. La siguiente tabla muestra las barras de herramientas que aparecen en ventanas de herramientas en el IDE y los grupos de comandos que contienen.  
  
> [!NOTE]
>  Las barras de herramientas y los grupos usan el GUID `guidSHLMainMenu`, salvo que se especifique lo contrario mediante el uso de sintaxis de GUID: Id. Cuando se especifica un GUID para una barra de herramientas, también se aplica a los grupos que descienden de esa barra de herramientas.  
  
|Ventana de herramientas|Barra de herramientas|Grupos|  
|-----------------|-------------|------------|  
|Explorador de soluciones|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Explorador de servidores|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Propiedades|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Vista de clases|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Vista de clases|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Examinador de objetos|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Examinador de objetos|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Salida|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Buscar y reemplazar|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Buscar resultados 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Resultados de búsqueda 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Fragmento de código|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Marcadores|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Lista de tareas|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Tareas de usuario|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Lista de errores|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Explorador de llamadas|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Puntos de interrupción|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Desensamblado|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Memoria de 1 a 4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Procesos|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Vea también  
 [Agregar un controlador de menú a una barra de herramientas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Agregar una barra de herramientas a una ventana de herramientas](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Menús de GUID e identificadores de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)