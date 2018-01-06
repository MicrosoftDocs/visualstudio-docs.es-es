---
redirect_url: shell/customizing-the-isolated-shell
title: Personalizar el Shell aislado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e02d93e966f676e0933b866cc8e74bfdd011231f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-isolated-shell"></a>Personalizar el Shell aislado
Puede personalizar la aplicación de shell aislado de Visual Studio cambiando distintos aspectos de la interfaz de usuario de Visual Studio y restringiendo los comandos y las características incluidas en la aplicación especializada.  
  
## <a name="using-the-applicationpkgdef-file"></a>Mediante el archivo Application.pkgdef  
 La solución de plantilla de shell aislado incluye un *nombresolución*. Archivo de Application.pkgdef que le permite modificar las siguientes características:  
  
##### <a name="the-application-title"></a>El título de la aplicación  
 Puede personalizar el título de la aplicación, que es el nombre que se muestra en la barra de título de la aplicación, cambiando el valor de la fila "AppName" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si no desea que el título de la aplicación para mostrar el proyecto que está cargado actualmente, cambie el valor de la fila "ShowHierarchyRootInTitle" en la *nombresolución*. Archivo Application.pkgdef from DWORD: 00000001 DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>El icono de la aplicación  
 Puede personalizar el icono de la aplicación, que es el icono que se muestra por el nombre de la aplicación en la barra de título de la aplicación. Copie un icono diferente en el directorio de icono. En **el Explorador de soluciones**, el icono para agregar a la carpeta de archivos de recursos. A continuación, abra el archivo VSShellStub.rc y sustituya el valor de IDI_STUBPROGRAM con el nombre del nuevo icono. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>El logotipo de la línea de comandos  
 Puede personalizar el logotipo de línea de comandos, que es el texto que aparece cuando la aplicación se inicia desde la línea de comandos, cambiando el valor de la fila "CommandLineLogo" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>El nombre de la subcarpeta de archivos de usuario  
 Puede cambiar el nombre de la carpeta de la aplicación mantiene archivos de usuario cambiando el valor de la fila "UserFilesSubFolderName" *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>El título del nodo de árbol de la solución en el cuadro de diálogo nuevo proyecto  
 Puede personalizar el título del nodo de solución en el cuadro de diálogo nuevo proyecto, cambie el valor de la fila "NewProjDlgSlnTreeNodeTitle" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>El encabezado de plantillas instaladas en el cuadro de diálogo nuevo proyecto  
 Puede cambiar el encabezado de plantillas instaladas en el cuadro de diálogo nuevo proyecto, cambie el valor de la fila "NewProjDlgInstalledTemplatesHdr" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Si desea ocultar archivos varios de manera predeterminada o no  
 Puede especificar si desea ocultar archivos varios de forma predeterminada, cambie el valor de la fila "HideMiscellaneousFilesByDefault" o no el *nombresolución*. Archivo Application.pkgdef. Para ocultar archivos varios, establezca el valor `dword:00000001`y para mostrar los archivos, establezca el valor `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Si desea deshabilitar la ventana de salida o no  
 Puede especificar si desea deshabilitar la ventana de salida en la aplicación cambiando el valor de la fila "DisableOutputWindow" o no el *nombresolución*. Archivo Application.pkgdef. Para deshabilitar la ventana de salida, establezca el valor `dword:00000001`y para mostrar la ventana de salida, establezca el valor `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Si desea permitir que los archivos colocados en la ventana principal o no  
 Puede especificar si desea permitir que los archivos colocados en la ventana principal de la aplicación cambiando el valor de la fila "AllowsDroppedFilesOnMainWindow" o no el *nombresolución*. Archivo Application.pkgdef. Para permitir que los archivos eliminados, establezca el valor `dword:00000001`y para denegar los archivos colocados, establezca el valor `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>La página de búsqueda predeterminada  
 Puede personalizar la página de explorador web, que es la página que se muestra cuando se abre la ventana del explorador web, cambiando el valor de la fila "DefaultSearchPage" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>La página principal predeterminada  
 Puede personalizar la página principal, cambie el valor de la fila "DefaultHomePage" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Si desea ocultar el concepto de solución o no  
 Puede especificar si desea ocultar la solución en la aplicación cambiando el valor de la fila "HideSolutionConcept" o no el *nombresolución*. Archivo Application.pkgdef. Para ocultar la solución, establezca el valor `dword:00000001`y para mostrar la solución, establezca el valor `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>El motor de depuración predeterminada  
 Puede cambiar el motor de depuración de la aplicación utiliza cambiando el valor de la fila "DefaultDebugEngine" en la *nombresolución*. Archivo de Application.pkgdef para el GUID de su motor de depuración.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>La extensión de archivo del archivo de opciones de usuario  
 Puede cambiar el nombre de la carpeta de la aplicación mantiene archivos de usuario cambiando el valor de la fila "UserOptsFileExt" *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>La extensión de archivo de solución  
 Puede cambiar la extensión utilizada para los archivos de solución, cambie el valor de la fila "SolutionFileExt" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La raíz de carpeta de archivos de usuario predeterminado  
 Puede cambiar el nombre de la carpeta raíz de los archivos de usuario para la aplicación cambiando el valor de la fila "UserFilesSubFolderName" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>El identificador de creador de archivo de solución  
 Puede cambiar el identificador utilizado para los archivos de solución, cambie el valor de la fila "SolutionFileCreatorIdentifier" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>La ubicación de proyectos predeterminada  
 Puede cambiar el nombre de la ubicación de proyectos de manera predeterminada, cambie el valor de la fila "DefaultProjectsLocation" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>El paquete de localización de la aplicación  
 Puede cambiar el paquete de localización usado para la aplicación cambiando el valor de la fila "AppLocalizationPackage" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Si se debe o no mostrar la raíz de la jerarquía en el título  
 Puede especificar si se debe o no mostrar la raíz de la jerarquía en la barra de título de la aplicación cambiando el valor de la fila "ShowHierarchyRootInTitle" en la *nombresolución*. Archivo Application.pkgdef. Para mostrar la raíz de la jerarquía, establezca el valor `dword:00000001`y para ocultar la raíz de la jerarquía, establezca el valor `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Especificar una página de inicio  
 Para especificar una página de inicio de la aplicación personalizada, en la *nombresolución*. Archivo de Application.pkgdef, establezca el valor de "DisableStartPage" en `dword:00000000`y en `[$RootKey$\StartPage\Default]` establecer el URI a la ubicación del archivo .xaml:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 En el archivo Applicationcommands.vsct en el *SolutionName*interfaz de usuario del proyecto, comenta la entrada "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Debe agregar el archivo .xaml y los archivos de gráficos que necesite, a la *nombresolución* proyecto. Estos archivos deben copiarse realmente en el *SolutionName* directorio del proyecto, no se agregó desde otro directorio.  
  
 En todos los archivos, establezca la **tipo de elemento de** propiedad **aislado de archivos de Shell** en orden para los archivos se copien en el *$RootFolder$* directory. (Para establecer el **tipo de elemento** propiedad, haga clic en el archivo y seleccione **propiedades**. Esta propiedad se encuentra en **propiedades de configuración**, **General**.)  
  
 Para obtener más información acerca de cómo personalizar las páginas de inicio, consulte [personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Uso de otros elementos de shell aislado  
 Puede usar otros archivos y proyectos que se incluyen en la plantilla de solución de shell aislado para personalizar aún más la aplicación.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Habilitar o deshabilitar los paquetes de Visual Studio  
 El *nombresolución*.pkgundef archivo le permite deshabilitar ciertos tipos de funcionalidad de Visual Studio mediante la exclusión de algunos paquetes. Por ejemplo, la siguiente línea:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Quita el proyecto archivos varios del conjunto de plantillas de proyecto que se muestran en la **nuevo proyecto** cuadro de diálogo. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Habilitar o deshabilitar los comandos de menú  
 El *nombresolución*UI.vsct archivo incluye una lista de comentarios de todos los comandos de menú disponibles al shell aislado. Para deshabilitar un comando determinado, quite la fila correspondiente. Por ejemplo, para deshabilitar el comentario de la ventana de división, quite el `<Define name="No_SplitCommand"/>` fila. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>El mapa de bits utilizado en la pantalla de presentación  
 Puede personalizar el mapa de bits utilizado en la pantalla de presentación, que es la ventana que se muestra cuando se inicia la aplicación, cambiando el valor de la fila "SplashScreenBitmap" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>La ayuda/acerca de la ventana  
 En la plantilla de shell aislado hay un proyecto independiente que se puede utilizar para personalizar la ayuda/acerca de la casilla para la aplicación. Para obtener más información, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).