---
title: Personalización del shell aislado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555976"
---
# <a name="customizing-the-isolated-shell"></a>Personalización de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede personalizar la aplicación de Shell aislado de Visual Studio cambiando distintos aspectos de la interfaz de usuario de Visual Studio y restringiendo los comandos y las características que se incluyen en la aplicación especializada.  
  
## <a name="using-the-applicationpkgdef-file"></a>Usar el archivo Application. pkgdef  
 La solución de plantilla de Shell aislado incluye un *solutionname*. Archivo Application. pkgdef que le permite modificar las características siguientes:  
  
##### <a name="the-application-title"></a>Título de la aplicación  
 Puede personalizar el título de la aplicación, que es el nombre que se muestra en la barra de título de la aplicación, cambiando el valor de la fila "AppName" en el *solutionname*. Archivo Application. pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si no desea que el título de la aplicación muestre el proyecto cargado actualmente, cambie el valor de la fila "ShowHierarchyRootInTitle" en el *solutionname*. Archivo Application. pkgdef de DWORD: 00000001 a DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Icono de la aplicación  
 Puede personalizar el icono de la aplicación, que es el icono que se muestra en el nombre de la aplicación en la barra de título de la aplicación. Copie un icono diferente en el directorio de iconos. En **Explorador de soluciones**, agregue el icono a la carpeta archivos de recursos. A continuación, abra el archivo VSShellStub. RC y reemplace el valor de IDI_STUBPROGRAM por el nombre del nuevo icono. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>El logotipo de la línea de comandos  
 Puede personalizar el logotipo de la línea de comandos, que es el texto que aparece cuando la aplicación se inicia desde la línea de comandos, cambiando el valor de la fila "CommandLineLogo" en el *solutionname*. Archivo Application. pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>El nombre de la subcarpeta archivos de usuario  
 Puede cambiar el nombre de la carpeta que la aplicación mantiene para los archivos de usuario cambiando el valor de la fila "UserFilesSubFolderName" en *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Título del nodo de árbol de la solución en el cuadro de diálogo nuevo proyecto  
 Puede personalizar el título del nodo de la solución en el cuadro de diálogo nuevo proyecto cambiando el valor de la fila "NewProjDlgSlnTreeNodeTitle" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Encabezado plantillas instaladas en el cuadro de diálogo nuevo proyecto  
 Puede cambiar el encabezado plantillas instaladas en el cuadro de diálogo nuevo proyecto cambiando el valor de la fila "NewProjDlgInstalledTemplatesHdr" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Si se ocultan o no archivos varios de forma predeterminada  
 Puede especificar si desea ocultar o no archivos varios de forma predeterminada cambiando el valor de la fila "HideMiscellaneousFilesByDefault" en el *solutionname*. Archivo Application. pkgdef. Para ocultar archivos varios, establezca el valor `dword:00000001` y para mostrar los archivos, establezca el valor `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Si se deshabilitará o no la ventana de salida  
 Puede especificar si desea deshabilitar o no la ventana de salida de la aplicación cambiando el valor de la fila "DisableOutputWindow" en el *solutionname*. Archivo Application. pkgdef. Para deshabilitar la ventana de salida, establezca el valor `dword:00000001` y, para mostrar la ventana de salida, establezca el valor `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Indica si se permiten o no archivos colocados en la ventana principal  
 Puede especificar si desea permitir o no los archivos colocados en la ventana principal de la aplicación cambiando el valor de la fila "AllowsDroppedFilesOnMainWindow" en el *solutionname*. Archivo Application. pkgdef. Para permitir los archivos colocados, establezca el valor `dword:00000001` y, para impedir que se quiten los archivos, establezca el valor `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>La página de búsqueda predeterminada  
 Puede personalizar la página del explorador Web, que es la página que se muestra cuando se abre la ventana del explorador Web, cambiando el valor de la fila "DefaultSearchPage" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-default-home-page"></a>La Página principal predeterminada  
 Puede personalizar la Página principal cambiando el valor de la fila "DefaultHomePage" en el *solutionname*. Archivo Application. pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Si se va a ocultar o no el concepto de la solución  
 Puede especificar si desea ocultar o no la solución en la aplicación cambiando el valor de la fila "HideSolutionConcept" en el *solutionname*. Archivo Application. pkgdef. Para ocultar la solución, establezca el valor `dword:00000001` y, para mostrar la solución, establezca el valor `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>El motor de depuración predeterminado  
 Puede cambiar el motor de depuración que utiliza la aplicación cambiando el valor de la fila "DefaultDebugEngine" en el *solutionname*. Archivo Application. pkgdef al GUID del motor de depuración.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>La extensión de archivo del archivo de opciones de usuario  
 Puede cambiar el nombre de la carpeta que la aplicación mantiene para los archivos de usuario cambiando el valor de la fila "UserOptsFileExt" en *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-solution-file-extension"></a>La extensión de archivo de la solución  
 Puede cambiar la extensión utilizada para los archivos de solución cambiando el valor de la fila "SolutionFileExt" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La raíz de la carpeta de archivos de usuario predeterminada  
 Puede cambiar el nombre de la carpeta raíz de los archivos de usuario de la aplicación cambiando el valor de la fila "UserFilesSubFolderName" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identificador del creador del archivo de solución  
 Puede cambiar el identificador usado para los archivos de solución cambiando el valor de la fila "SolutionFileCreatorIdentifier" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-default-projects-location"></a>La ubicación predeterminada de los proyectos  
 Puede cambiar el nombre de la ubicación predeterminada de los proyectos cambiando el valor de la fila "DefaultProjectsLocation" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="the-application-localization-package"></a>El paquete de localización de aplicaciones  
 Puede cambiar el paquete de localización que se usa para la aplicación cambiando el valor de la fila "AppLocalizationPackage" en el *solutionname*. Archivo Application. pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Indica si se debe mostrar o no la raíz de la jerarquía en el título  
 Puede especificar si desea mostrar o no la raíz de la jerarquía en la barra de título de la aplicación cambiando el valor de la fila "ShowHierarchyRootInTitle" en el *solutionname*. Archivo Application. pkgdef. Para mostrar la raíz de la jerarquía, establezca el valor `dword:00000001` y para ocultar la raíz de la jerarquía, establezca el valor `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Especificar una página de inicio  
 Para especificar una página de inicio para la aplicación personalizada, en el *solutionname*. Archivo Application. pkgdef, establezca el valor de "DisableStartPage" en `dword:00000000` y en `[$RootKey$\StartPage\Default]` establezca el URI en la ubicación del archivo. XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 En el archivo ApplicationCommands. Vsct del proyecto de la interfaz de usuario de *solutionname*, comente la entrada "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Debe agregar el archivo. XAML y los archivos de gráficos que necesite al proyecto de *solutionname* . Estos archivos deben copiarse en el directorio del proyecto de *solutionname* , no se pueden agregar desde otro directorio.  
  
 En todos los archivos, establezca la propiedad **tipo de elemento** en archivo de **Shell aislado** para que los archivos se copien en el directorio *$RootFolder $* . (Para establecer la propiedad **tipo de elemento** , haga clic con el botón secundario en el archivo y seleccione **propiedades**. Esta propiedad se encuentra en **propiedades de configuración**, **General**.)  
  
 Para obtener más información sobre cómo personalizar las páginas de inicio, vea [personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Usar otros elementos del shell aislado  
 Puede usar otros archivos y proyectos que se incluyen en la plantilla de solución de Shell aislado para personalizar aún más la aplicación.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Habilitar o deshabilitar paquetes de Visual Studio  
 El archivo *solutionname*. pkgundef permite deshabilitar determinados tipos de funcionalidad de Visual Studio excluyendo determinados paquetes. Por ejemplo, la siguiente línea:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 quita el proyecto de archivos varios del conjunto de plantillas de proyecto que se muestra en el cuadro de diálogo **nuevo proyecto** . Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Habilitar o deshabilitar comandos de menú  
 El archivo. Vsct de la interfaz de usuario de *solutionname*incluye una lista con comentarios de todos los comandos de menú disponibles para el shell aislado. Para deshabilitar un comando determinado, quite la marca de comentario de la fila correspondiente. Por ejemplo, para deshabilitar el comentario de ventana/división, quite la marca de comentario de la `<Define name="No_SplitCommand"/>` fila. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>El mapa de bits usado en la pantalla de presentación  
 Puede personalizar el mapa de bits que se usa en la pantalla de presentación, que es la ventana que se muestra cuando se inicia la aplicación, cambiando el valor de la fila "SplashScreenBitmap" en el *solutionname*. Archivo Application. pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Ventana ayuda/acerca de  
 En la plantilla de Shell aislado hay un proyecto independiente que puede usar para personalizar el cuadro de ayuda/acerca de la aplicación. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
