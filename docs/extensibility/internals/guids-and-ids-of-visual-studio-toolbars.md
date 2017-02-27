---
title: "GUID e identificadores de las barras de herramientas de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "grupos de Visual studio"
  - "barras de herramientas"
  - "barra de herramientas de Visual studio"
  - "id"
  - "grupo de toolgar"
  - "ventana de herramientas"
  - "GUID"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# GUID e identificadores de las barras de herramientas de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este tema muestra el GUID y los valores de identificador de barras de herramientas que se incluyen en el entorno de desarrollo integrado de \(IDE\) Visual Studio, y grupos contienen.  Estos valores se definen en los archivos de .vsct que se instalan como parte del SDK de Visual Studio.  Para obtener más información, vea [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Muchas de las barras de herramientas disponibles en Visual Studio no son definidas por Visual Studio, y su GUID y valores de identificador no son públicos.  Este tema enumera solo las barras de herramientas que se definen en los archivos de Visual Studio SDK .vsct.  
  
 Para obtener más información sobre cómo trabajar con objetos del IDE que se definen en archivos de .vsct, vea [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
 Las barras de herramientas predeterminadas proporcionadas por el IDE de Visual Studio utilizan GUID `guidSHLMainMenu`, excepto si especificado de otra manera utilizando GUID: Sintaxis de identificador.  
  
## Barras de herramientas del IDE  
 Las barras de herramientas siguientes se proporcionan en el IDE de Visual Studio.  Las barras de herramientas pueden mostrar seleccionándolos en el submenú de **barras de herramientas** de menú de **Herramientas** .  las barras de herramientas en ventanas de herramientas no se incluyen en esta sección.  
  
 Sólo los grupos pueden descender directamente de las barras de herramientas.  Para agregar un grupo, establezca su elemento primario al GUID y el identificador de la barra de herramientas.  para agregar un botón a una barra de herramientas, establezca a su elemento primario a un grupo en la barra de herramientas.  
  
|Barra de herramientas|Id.|  
|---------------------------|---------|  
|Standard|IDM\_VS\_TOOL\_STANDARD|  
|Compilar|IDM\_VS\_TOOL\_BUILD|  
|Editor de texto|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Depuración|guidVSDebugGroup: IDM\_DEBUG\_TOOLBAR|  
|Ubicación de depuración|guidVSDebugGroup: IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### barras de herramientas especiales  
 Estas barras de herramientas son definidas por el IDE de Visual Studio, pero proporcionan funciones especializadas y no los grupos de comando host.  
  
|Barra de herramientas|Id.|  
|---------------------------|---------|  
|agregue el comando|IDM\_VS\_TOOL\_ADDCOMMAND|  
|No definido|IDM\_VS\_TOOL\_UNDEFINED|  
|Esquema XML|IDM\_VS\_TOOL\_SCHEMA|  
|Datos XML|IDM\_VS\_TOOL\_DATA|  
  
## Grupos de las barras de herramientas del IDE  
 Para agregar un botón a una barra de herramientas estándar, establezca en uno de los siguientes grupos como su elemento primario.  La barra de herramientas principal ordenan los grupos.  
  
### grupos de la barra de herramientas Estándar  
  
|Name|Id.|  
|----------|---------|  
|Guarde y Abrir|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|Cortar o copia|IDG\_VS\_TOOLSB\_CUTCOPY|  
|Deshacer\/rehacer|IDG\_VS\_TOOLSB\_UNDOREDO|  
|Ejecución y compilado|IDG\_VS\_TOOLSB\_RUNBUILD|  
|Buscar|IDG\_VS\_TOOLSB\_SEARCH|  
|Ventanas|IDG\_VS\_TOOLSB\_WINDOWS|  
|Windows|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|Carga y guardar|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|medidor|IDG\_VS\_TOOLSB\_GAUGE|  
  
### Grupos de la barra de herramientas de compilación  
  
|Name|Id.|  
|----------|---------|  
|Barra de compilación|IDG\_VS\_BUILDBAR|  
|Cancelar|IDG\_VS\_BUILD\_CANCEL|  
  
### Grupos de la barra de herramientas editor de texto  
  
|Name|Id.|  
|----------|---------|  
|Finalización|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Indent|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|Comment|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|Marcadores|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### grupos de la barra de herramientas Depuración  
  
|Name|Id.|  
|----------|---------|  
|Execution|IDM\_DEBUG\_TOOLBAR|  
|Recorrido paso a paso|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|Ventanas|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### Grupos de la barra de herramientas ubicación de depuración  
  
|Name|Id.|  
|----------|---------|  
|Ubicación de depuración|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## barras de herramientas de la ventana de herramientas  
 Las barras de herramientas pueden aparecer directamente en el IDE o en ventanas de herramientas como **Explorador de soluciones**.  Dado que las ventanas de herramientas no se definen en archivos de .vsct, barras de herramientas de la ventana de herramientas no tienen elementos primarios definido.  En su lugar, se colocan en código.  La tabla siguiente muestra las barras de herramientas que aparecen en las ventanas de herramientas en el IDE, y grupos de comando que contienen.  
  
> [!NOTE]
>  Las barras de herramientas y grupos utilizan GUID `guidSHLMainMenu`, excepto si especificado de otra manera utilizando GUID: Sintaxis de identificador.  Donde GUID se especifica para una barra de herramientas, también se aplica a los grupos que descienden de la barra de herramientas.  
  
|ventana de herramientas|Barra de herramientas|Groups|  
|-----------------------------|---------------------------|------------|  
|Explorador de soluciones|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|Explorador de servidores|guid\_SE\_MenuGroup: IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|Propiedades|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|Vista de clases|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|Vista de clases|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEAR CH2|  
|Examinador de objetos|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|Examinador de objetos|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEAR CH2|  
|Output|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|Buscar y reemplazar|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|Resultados de la búsqueda 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|Resultados de la búsqueda 2|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|Marcadores|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|Lista de tareas|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|Tareas de usuario|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|Lista de errores|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|Explorador de llamadas|IDM\_VS\_TOOL\_ CALLBROWSER1. .16|\_ACTIONS OF IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_TYPE OF IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_CBSETTINGS OF IDG\_VS\_TOOLBAR\_ CALLBROWSER1|  
|Puntos de interrupción|guidVSDebugGroup: IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|Desensamblado|guidVSDebugGroup: IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|memoria 1\-4|guidVSDebugGroup: IDM\_MEMORY\_WINDOW\_TOOLBAR1… 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_ COLUMNS1. .4|  
|Procesos|guidVSDebugGroup: IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXE CCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## Vea también  
 [Agregar un controlador de menú a una barra de herramientas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Agregar una barra de herramientas a una ventana de herramientas](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)