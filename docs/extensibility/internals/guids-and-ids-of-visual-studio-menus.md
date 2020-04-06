---
title: GUID e iDE de los menús de Visual Studio Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708244"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e iDs de los menús de Visual Studio
En este artículo se enumeran los valores GUID e ID de los menús y grupos de la barra de menús de Visual Studio. Estos valores se definen en archivos *.vsct* que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [Comandos, menús y grupos definidos por IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Para obtener más información sobre cómo trabajar con objetos de entorno de desarrollo integrado (IDE) definidos en archivos *.vsct,* vea [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Los menús y grupos de la `guidSHLMainMenu`barra de menús de Visual Studio usan el GUID . La barra de menús `IDM_VS_TOOL_MAINMENU`en sí tiene un ID de .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupos en la barra de menús de Visual Studio
 Para agregar un menú a la barra de menús, establezca uno de estos grupos como su elemento primario.

|Grupo|id|
|-----------|--------|
|Archivo/Editar/Ver|IDG_VS_MM_FILEEDITVIEW|
|Refactorización|IDG_VS_MM_REFACTORING:|
|proyecto|IDG_VS_MM_PROJECT|
|Compilar|IDG_VS_MM_BUILDDEBUGRUN|
|Formato/Herramientas|IDG_VS_MM_TOOLSADDINS|
|Ventana/Ayuda/Comunidad|IDG_VS_MM_WINDOWHELP|
|Complementos|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menús en la barra de menús de Visual Studio
 Para agregar un grupo a un menú existente de Visual Studio, establezca uno de los siguientes menús como su elemento primario. Los submenús no se incluyen en esta lista.

|Menú|id|
|----------|--------|
|Archivo|IDM_VS_MENU_FILE|
|Editar|IDM_VS_MENU_EDIT|
|Ver|IDM_VS_MENU_VIEW|
|Refactorización|IDM_VS_MENU_REFACTORING|
|proyecto|IDM_VS_MENU_PROJECT|
|Compilar|IDM_VS_MENU_BUILD|
|Formato|IDM_VS_MENU_FORMAT|
|Herramientas|IDM_VS_MENU_TOOLS|
|Extensiones|IDM_VS_MENU_EXTENSIONS|
|Periodo|IDM_VS_MENU_WINDOW|
|Complementos|IDM_VS_MENU_ADDINS|
|Comunidad|IDM_VS_MENU_COMMUNITY|
|Ayuda|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Grupos en menús de Visual Studio
 En las listas siguientes se muestran los grupos que descienden directamente de los menús de la barra de menús de Visual Studio. La forma más rápida de agregar un comando a un menú de Visual Studio es establecer uno de estos grupos como el elemento primario. Los grupos que descienden de los submenús no aparecen en esta sección.

### <a name="file-menu-groups"></a>Grupos de menú sin archivos

|Grupo|id|
|-----------|--------|
|Nuevo/Abierto|IDG_VS_FILE_FILE|
|Sumar|IDG_VS_FILE_ADD|
|Solución|IDG_VS_FILE_SOLUTION|
|Varios|IDG_VS_FILE_MISC|
|Save|IDG_VS_FILE_SAVE|
|Cambiar nombre|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Print|IDG_VS_FILE_PRINT|
|Utilizado más recientemente|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Salir|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Editar grupos de menús

|Grupo|id|
|-----------|--------|
|Deshacer/rehacer|IDG_VS_EDIT_UNDOREDO|
|Cortar/Copiar/Pegar|IDG_VS_EDIT_CUTCOPY|
|Seleccionar|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Buscar|IDG_VS_EDIT_FIND|
|Objetos|IDG_VS_EDIT_OBJECTS|
|Verbos OLE|IDG_VS_EDIT_OLEVERBS|
|Comando Bien|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Refactorizar grupos de menús

|Grupo|id|
|-----------|--------|
|Comunes|IDG_REFACTORING_COMMON|
|Avanzado|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Ver grupos de menús

|Grupo|id|
|-----------|--------|
|Código de formulario|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definir vistas|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Arquitecto de Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Organización Windows|IDG_VS_VIEW_ORG_WINDOWS|
|Navegador de código|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Barras de herramientas|IDG_VS_VIEW_TOOLBARS|
|Symbols|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navegar|IDG_VS_VIEW_NAVIGATE|
|Navegación pequeña|IDG_VS_VIEW_SMALLNAVIGATE|
|Examinador de objetos|IDG_VS_VIEW_OBJBRWSR|
|Comando Bien|IDG_VS_VIEW_COMMANDWELL|
|Páginas de propiedades|IDG_VS_VIEW_PROPPAGES|
|Actualizar|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Grupos de menús del proyecto

|Grupo|id|
|-----------|--------|
|Añadir varios|IDG_VS_PROJ_MISCADD|
|Sumar|IDG_VS_PROJ_ADD|
|Carpeta|IDG_VS_PROJ_FOLDER|
|Descarga/Recarga|IDG_VS_PROJ_UNLOADRELOAD|
|Referencia|IDG_VS_PROJ_REFERENCE|
|Opciones|IDG_VS_PROJ_OPTIONS|
|Configuración|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Crear grupos de menús

|Grupo|id|
|-----------|--------|
|Solución|IDG_VS_BUILD_SOLUTION|
|Número de selección|IDG_VS_BUILD_SELECTION|
|Optimización guiada por perfiles|IDG_VS_PGO_SELECTION|
|Varios|IDG_VS_BUILD_MISC|
|Cancelar|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Grupos de menú stools

|Grupo|id|
|-----------|--------|
|Línea de comandos|IDG_VS_TOOLS_CMDLINE|
|Fragmentos de código|IDG_VS_TOOLS_SNIPPETS|
|Subconjunto de objetos|IDG_VS_TOOLS_OBJSUBSET|
|Opciones|IDG_VS_TOOLS_OPTIONS|
|Otros 2|IDG_VS_TOOLS_OTHER2|
|Herramientas externas|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizaciones externas|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Grupos de menús de ventanas

|Grupo|id|
|-----------|--------|
|Nuevo|IDG_VS_WINDOW_NEW|
|Dock/Cerrar|IDG_VS_DOCKCLOSE|
|Dock/Ocultar|IDG_VS_DOCKHIDE|
|Organizar|IDG_VS_WINDOW_ARRANGE|
|Navegación|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Grupos de menú de ayuda

|Grupo|id|
|-----------|--------|
|Ejemplos|IDG_VS_HELP_SAMPLES|
|Soporte técnico|IDG_VS_HELP_SUPPORT|
|Información|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Submenús de los menús de Visual Studio
 La jerarquía siguiente muestra los submenús asociados a los menús de la barra de menús de Visual Studio. Dado que solo un grupo puede tener un menú como elemento primario, cada submenú debe descender de un grupo de un menú, en lugar de directamente desde el menú. Para obtener más información sobre la relación entre menús, grupos y submenús, consulte [Agregar un submenú a un menú](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Los nombres de los menús de la barra de menús de Visual Studio no se muestran por separado en esta jerarquía porque se pueden deducir de la convención de nomenclatura para los grupos del IDE, como se indica a continuación: *IDG_VS_\<Nombre\>\<\>* del menú _ Nombre de grupo .

|Grupo primario|Submenú|Grupos de niños|
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
- [GUID e iDs de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID e iD de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
