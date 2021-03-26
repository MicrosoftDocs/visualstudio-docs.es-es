---
title: GUID e identificadores de los menús de Visual Studio | Microsoft Docs
description: Vea una lista de los valores de GUID y de identificador de los menús y grupos en la barra de menús de Visual Studio incluida en el entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9f5066c5ae5c9fa57517406b8eca388747979c4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082093"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e identificadores de los menús de Visual Studio
En este artículo se enumeran los valores de GUID y de identificador de los menús y grupos en la barra de menús de Visual Studio. Estos valores se definen en los archivos *. Vsct* que se instalan como parte del SDK de Visual Studio. Para obtener más información, vea [comandos, menús y grupos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Para obtener más información sobre cómo trabajar con objetos del entorno de desarrollo integrado (IDE) que se definen en archivos *. Vsct* , vea [extensión de menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Los menús y grupos en la barra de menús de Visual Studio usan el GUID `guidSHLMainMenu` . La barra de menús tiene un identificador de `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupos en la barra de menús de Visual Studio
 Para agregar un menú a la barra de menús, establezca uno de estos grupos como su elemento primario.

|Grupo|ID|
|-----------|--------|
|Archivo/edición/ver|IDG_VS_MM_FILEEDITVIEW|
|Refactorización|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Build|IDG_VS_MM_BUILDDEBUGRUN|
|Formato/herramientas|IDG_VS_MM_TOOLSADDINS|
|Ventana/ayuda/comunidad|IDG_VS_MM_WINDOWHELP|
|Complementos|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menús en la barra de menús de Visual Studio
 Para agregar un grupo a un menú existente de Visual Studio, establezca uno de los siguientes menús como su elemento primario. Los submenús no se incluyen en esta lista.

|Menú|ID|
|----------|--------|
|Archivo|IDM_VS_MENU_FILE|
|Editar|IDM_VS_MENU_EDIT|
|Ver|IDM_VS_MENU_VIEW|
|Refactorización|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Build|IDM_VS_MENU_BUILD|
|Formato|IDM_VS_MENU_FORMAT|
|Herramientas|IDM_VS_MENU_TOOLS|
|Extensiones|IDM_VS_MENU_EXTENSIONS|
|Periodo|IDM_VS_MENU_WINDOW|
|Complementos|IDM_VS_MENU_ADDINS|
|Comunidad|IDM_VS_MENU_COMMUNITY|
|Ayuda|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Grupos en los menús de Visual Studio
 En las listas siguientes se muestran los grupos que descienden directamente de los menús de la barra de menús de Visual Studio. La forma más rápida de agregar un comando a un menú de Visual Studio es establecer uno de estos grupos como elemento primario. Los grupos que descienden de los submenús no aparecen en esta sección.

### <a name="file-menu-groups"></a>Grupos de menús de archivos

|Grupo|ID|
|-----------|--------|
|Nuevo/abrir|IDG_VS_FILE_FILE|
|Sumar|IDG_VS_FILE_ADD|
|Solución|IDG_VS_FILE_SOLUTION|
|Varios|IDG_VS_FILE_MISC|
|Guardar|IDG_VS_FILE_SAVE|
|Cambiar nombre|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Impresión|IDG_VS_FILE_PRINT|
|Usados más recientemente|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Salir|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Editar grupos de menús

|Grupo|ID|
|-----------|--------|
|Deshacer/rehacer|IDG_VS_EDIT_UNDOREDO|
|Cortar/copiar/pegar|IDG_VS_EDIT_CUTCOPY|
|Seleccionar|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Buscar|IDG_VS_EDIT_FIND|
|de la empresa|IDG_VS_EDIT_OBJECTS|
|Verbos OLE|IDG_VS_EDIT_OLEVERBS|
|Cuadro de comandos|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Refactorizar grupos de menús

|Grupo|ID|
|-----------|--------|
|Comunes|IDG_REFACTORING_COMMON|
|Avanzado|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Ver grupos de menús

|Grupo|ID|
|-----------|--------|
|Código de formulario|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definir vistas|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Arquitectura de Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Ventanas de la organización|IDG_VS_VIEW_ORG_WINDOWS|
|Explorador de código|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Ventanas de desarrollo|IDG_VS_VIEW_DEV_WINDOWS|
|Barras de herramientas|IDG_VS_VIEW_TOOLBARS|
|Símbolos|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navegar|IDG_VS_VIEW_NAVIGATE|
|Desplazamiento pequeño|IDG_VS_VIEW_SMALLNAVIGATE|
|Examinador de objetos|IDG_VS_VIEW_OBJBRWSR|
|Cuadro de comandos|IDG_VS_VIEW_COMMANDWELL|
|Páginas de propiedades|IDG_VS_VIEW_PROPPAGES|
|Actualizar|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Grupos de menús del proyecto

|Grupo|ID|
|-----------|--------|
|Agregar varios|IDG_VS_PROJ_MISCADD|
|Sumar|IDG_VS_PROJ_ADD|
|Carpeta|IDG_VS_PROJ_FOLDER|
|Descargar/volver a cargar|IDG_VS_PROJ_UNLOADRELOAD|
|Referencia|IDG_VS_PROJ_REFERENCE|
|Opciones|IDG_VS_PROJ_OPTIONS|
|Configuración|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Grupos de menús de compilación

|Grupo|ID|
|-----------|--------|
|Solución|IDG_VS_BUILD_SOLUTION|
|Selección|IDG_VS_BUILD_SELECTION|
|Optimización guiada por perfiles|IDG_VS_PGO_SELECTION|
|Varios|IDG_VS_BUILD_MISC|
|Cancelar|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Grupos de menús de herramientas

|Grupo|ID|
|-----------|--------|
|Línea de comandos|IDG_VS_TOOLS_CMDLINE|
|Fragmentos de código|IDG_VS_TOOLS_SNIPPETS|
|Subconjunto de objetos|IDG_VS_TOOLS_OBJSUBSET|
|Opciones|IDG_VS_TOOLS_OPTIONS|
|Otros 2|IDG_VS_TOOLS_OTHER2|
|Herramientas externas|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizaciones externas|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Grupos de menús de ventana

|Grupo|ID|
|-----------|--------|
|Nuevo|IDG_VS_WINDOW_NEW|
|Acoplar/cerrar|IDG_VS_DOCKCLOSE|
|Acoplar/ocultar|IDG_VS_DOCKHIDE|
|Organizar|IDG_VS_WINDOW_ARRANGE|
|Navegación|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Grupos de menús de ayuda

|Grupo|ID|
|-----------|--------|
|Ejemplos|IDG_VS_HELP_SAMPLES|
|Soporte técnico|IDG_VS_HELP_SUPPORT|
|Acerca de|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Submenús de menús de Visual Studio
 En la jerarquía siguiente se muestran los submenús que están asociados a los menús de la barra de menús de Visual Studio. Dado que solo un grupo puede tener un menú como elemento primario, cada submenú debe ser descendente de un grupo en un menú, en lugar de hacerlo directamente desde el menú. Para obtener más información sobre la relación entre los menús, los grupos y los submenús, vea [Agregar un submenú a un menú](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Los nombres de los menús de la barra de menús de Visual Studio no se muestran por separado en esta jerarquía porque se pueden inferir de la Convención de nomenclatura para los grupos en el IDE, como se indica a continuación: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

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
|||IDG_VS_WNDO_OTRWNDWS1... 1,8|
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

## <a name="see-also"></a>Consulte también
- [GUID e identificadores de barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID e identificadores de comandos de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
