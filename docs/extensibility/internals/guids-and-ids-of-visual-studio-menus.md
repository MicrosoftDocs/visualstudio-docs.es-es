---
title: GUID e IDs de Visual Studio menús | Microsoft Docs
description: Vea una lista de valores guid e identificador para los menús y grupos en la barra de menús Visual Studio que se incluye en el entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: bceee5fce8a77ad5169020bd3d21896bdbc71443
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898076"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e iDs de Visual Studio menús
En este artículo se enumeran los valores guid e identificador de los menús y grupos de la Visual Studio menús. Estos valores se definen en *los archivos .vsct* que se instalan como parte del SDK Visual Studio. Para obtener más información, vea [Comandos, menús](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)y grupos definidos por IDE.

 Para obtener más información sobre cómo trabajar con objetos de entorno de desarrollo integrado (IDE) definidos en archivos *.vsct,* vea [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Los menús y grupos de la Visual Studio de menús usan el GUID `guidSHLMainMenu` . La propia barra de menús tiene un identificador de `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupos en la barra Visual Studio menú
 Para agregar un menú a la barra de menús, establezca uno de estos grupos como primario.

|Group (Grupo)|ID|
|-----------|--------|
|Archivo, edición o vista|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Build|IDG_VS_MM_BUILDDEBUGRUN|
|Formato y herramientas|IDG_VS_MM_TOOLSADDINS|
|Ventana/Ayuda/Comunidad|IDG_VS_MM_WINDOWHELP|
|Complementos|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menús de la barra Visual Studio menús
 Para agregar un grupo a un menú Visual Studio existente, establezca uno de los siguientes menús como su elemento primario. Los submenús no se incluyen en esta lista.

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

## <a name="groups-on-visual-studio-menus"></a>Grupos en Visual Studio menús
 En las listas siguientes se muestran los grupos que descienden directamente de los menús de la Visual Studio menús. La manera más rápida de agregar un comando a un menú Visual Studio es establecer uno de estos grupos como primario. Los grupos que descienden de los submenús no aparecen en esta sección.

### <a name="file-menu-groups"></a>Grupos de menús de archivos

|Group (Grupo)|ID|
|-----------|--------|
|Nuevo/Abierto|IDG_VS_FILE_FILE|
|Sumar|IDG_VS_FILE_ADD|
|Solución|IDG_VS_FILE_SOLUTION|
|Varios|IDG_VS_FILE_MISC|
|Guardar|IDG_VS_FILE_SAVE|
|Cambiar nombre|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Impresión|IDG_VS_FILE_PRINT|
|Usado más recientemente|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Salir|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Editar grupos de menús

|Group (Grupo)|ID|
|-----------|--------|
|Deshacer/rehacer|IDG_VS_EDIT_UNDOREDO|
|Cortar, copiar y pegar|IDG_VS_EDIT_CUTCOPY|
|Seleccionar|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Buscar|IDG_VS_EDIT_FIND|
|Objetos|IDG_VS_EDIT_OBJECTS|
|Verbos OLE|IDG_VS_EDIT_OLEVERBS|
|Command Well|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Refactorización de grupos de menús

|Group (Grupo)|ID|
|-----------|--------|
|Comunes|IDG_REFACTORING_COMMON|
|Avanzado|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Ver grupos de menús

|Group (Grupo)|ID|
|-----------|--------|
|Código de formulario|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definir vistas|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Ventanas de arquitectura|IDG_VS_VIEW_ARCH_WINDOWS|
|Ventanas de organización|IDG_VS_VIEW_ORG_WINDOWS|
|Explorador de código|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Ventanas de desarrollo|IDG_VS_VIEW_DEV_WINDOWS|
|Barras de herramientas|IDG_VS_VIEW_TOOLBARS|
|Símbolos|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navegar|IDG_VS_VIEW_NAVIGATE|
|Navegación pequeña|IDG_VS_VIEW_SMALLNAVIGATE|
|Examinador de objetos|IDG_VS_VIEW_OBJBRWSR|
|Command Well|IDG_VS_VIEW_COMMANDWELL|
|Páginas de propiedades|IDG_VS_VIEW_PROPPAGES|
|Actualizar|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Grupos de menús del proyecto

|Group (Grupo)|ID|
|-----------|--------|
|Agregar varios|IDG_VS_PROJ_MISCADD|
|Sumar|IDG_VS_PROJ_ADD|
|Carpeta|IDG_VS_PROJ_FOLDER|
|Descargar o recargar|IDG_VS_PROJ_UNLOADRELOAD|
|Referencia|IDG_VS_PROJ_REFERENCE|
|Opciones|IDG_VS_PROJ_OPTIONS|
|Configuración|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Crear grupos de menús

|Group (Grupo)|ID|
|-----------|--------|
|Solución|IDG_VS_BUILD_SOLUTION|
|Selección|IDG_VS_BUILD_SELECTION|
|Optimización guiada por perfiles|IDG_VS_PGO_SELECTION|
|Varios|IDG_VS_BUILD_MISC|
|Cancelar|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Grupos de menús herramientas

|Group (Grupo)|ID|
|-----------|--------|
|Línea de comandos|IDG_VS_TOOLS_CMDLINE|
|Fragmentos de código|IDG_VS_TOOLS_SNIPPETS|
|Subconjunto de objetos|IDG_VS_TOOLS_OBJSUBSET|
|Opciones|IDG_VS_TOOLS_OPTIONS|
|Otros 2|IDG_VS_TOOLS_OTHER2|
|Herramientas externas|IDG_VS_TOOLS_EXT_TOOLS|
|Personalizaciones externas|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Grupos de menús de ventana

|Group (Grupo)|ID|
|-----------|--------|
|Nuevo|IDG_VS_WINDOW_NEW|
|Acoplar/cerrar|IDG_VS_DOCKCLOSE|
|Acoplar u ocultar|IDG_VS_DOCKHIDE|
|Organizar|IDG_VS_WINDOW_ARRANGE|
|Navegación|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Grupos de menús de ayuda

|Group (Grupo)|ID|
|-----------|--------|
|Ejemplos|IDG_VS_HELP_SAMPLES|
|Soporte técnico|IDG_VS_HELP_SUPPORT|
|Acerca de|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Submenús de Visual Studio menús
 En la jerarquía siguiente se muestran los submenús asociados a los menús de la Visual Studio menús. Dado que solo un grupo puede tener un menú como su elemento primario, cada submenú debe descender de un grupo de un menú, en lugar de hacerlo directamente desde el menú. Para obtener más información sobre la relación entre menús, grupos y submenús, vea [Agregar un submenú a un menú](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Los nombres de los menús de la barra de menús Visual Studio no se muestran por separado en esta jerarquía porque se pueden deducir de la convención de nomenclatura para los grupos del IDE, como se indica a continuación: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

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

## <a name="see-also"></a>Consulta también
- [GUID e IDs de Visual Studio barras de herramientas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID e IDs de Visual Studio comandos](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio de tabla de comandos (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
