---
title: Personalización del Shell aislado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097186ba43202c537bf8acbe0b47893151055c19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733787"
---
# <a name="customizing-the-isolated-shell"></a>Personalización del Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede personalizar la aplicación de shell aislado de Visual Studio cambiando diferentes aspectos de la interfaz de usuario de Visual Studio y restringiendo los comandos y las características incluidas en su aplicación especializada.  
  
## <a name="using-the-applicationpkgdef-file"></a>Mediante el archivo Application.pkgdef  
 La solución de plantilla de shell aislado incluye un *SolutionName*. Archivo Application.pkgdef que le permite modificar las siguientes características:  
  
##### <a name="the-application-title"></a>El título de la aplicación  
 Puede personalizar el título de la aplicación, que es el nombre que se muestra en la barra de título de la aplicación, cambiando el valor de la fila "AppName" en el *SolutionName*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si no desea que el título de la aplicación para mostrar el proyecto que está cargado actualmente, cambie el valor de la fila "ShowHierarchyRootInTitle" en el *SolutionName*. Archivo de Application.pkgdef de DWORD: 00000001 a DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>El icono de aplicación  
 Puede personalizar el icono de aplicación, que es el icono que muestra el nombre de la aplicación en la barra de título de la aplicación. Copie un icono diferente en el directorio de icono. En **el Explorador de soluciones**, el icono Agregar a la carpeta de archivos de recursos. A continuación, abra el archivo VSShellStub.rc y reemplace el valor de IDI_STUBPROGRAM con el nombre del nuevo icono. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>El logotipo de la línea de comandos  
 Puede personalizar el logotipo de línea de comandos, que es el texto que aparece cuando se inicia la aplicación desde la línea de comandos, cambie el valor de la fila "CommandLineLogo" en el *SolutionName*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>El nombre de la subcarpeta de archivos de usuario  
 Puede cambiar el nombre de la carpeta de la aplicación se mantiene para los archivos de usuario cambiando el valor de la fila "UserFilesSubFolderName" *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>El título del nodo de árbol de la solución en el cuadro de diálogo nuevo proyecto  
 Puede personalizar el título del nodo de solución en el cuadro de diálogo nuevo proyecto, cambie el valor de la fila "NewProjDlgSlnTreeNodeTitle" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>El encabezado de plantillas instaladas en el cuadro de diálogo nuevo proyecto  
 Puede cambiar el encabezado de plantillas instaladas en el cuadro de diálogo nuevo proyecto, cambie el valor de la fila "NewProjDlgInstalledTemplatesHdr" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Si se deben ocultar archivos varios de forma predeterminada  
 Puede especificar si desea ocultar archivos varios de forma predeterminada, cambie el valor de la fila "HideMiscellaneousFilesByDefault" o no el *SolutionName*. Archivo Application.pkgdef. Para ocultar archivos varios, establezca el valor `dword:00000001`y para mostrar los archivos, establezca el valor `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Si se deben deshabilitar la ventana de salida  
 Puede especificar si se deben deshabilitar la ventana de salida en la aplicación cambiando el valor de la fila "DisableOutputWindow" en el *SolutionName*. Archivo Application.pkgdef. Para deshabilitar la ventana de salida, establezca el valor `dword:00000001`y para mostrar la ventana de salida, establezca el valor `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Si desea permitir que los archivos colocados en la ventana principal o no  
 Puede especificar si desea permitir que los archivos colocados en la ventana principal de la aplicación cambiando el valor de la fila "AllowsDroppedFilesOnMainWindow" o no el *SolutionName*. Archivo Application.pkgdef. Para permitir que los archivos colocados, establezca el valor `dword:00000001`y para no permitir a los archivos colocados, establezca el valor `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>La página de búsqueda predeterminado  
 Puede personalizar la página del explorador web, que es la página que se muestra cuando se abre la ventana del explorador web, cambiando el valor de la fila "DefaultSearchPage" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>La página principal predeterminada  
 Puede personalizar la página principal, cambie el valor de la fila "DefaultHomePage" en el *SolutionName*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Si se debe o no ocultan el concepto de solución  
 Puede especificar si desea ocultar la solución en la aplicación cambiando el valor de la fila "HideSolutionConcept" o no el *SolutionName*. Archivo Application.pkgdef. Para ocultar la solución, establezca el valor `dword:00000001`y para mostrar la solución, establezca el valor `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>El motor de depuración predeterminada  
 Puede cambiar el motor de depuración que usa su aplicación cambiando el valor de la fila "DefaultDebugEngine" en el *SolutionName*. Archivo Application.pkgdef al GUID de su motor de depuración.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>La extensión de archivo del archivo de opciones de usuario  
 Puede cambiar el nombre de la carpeta de la aplicación se mantiene para los archivos de usuario cambiando el valor de la fila "UserOptsFileExt" *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>La extensión de archivo de solución  
 Puede cambiar la extensión utilizada para los archivos de solución, cambie el valor de la fila "SolutionFileExt" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La raíz de carpeta de archivos de usuario predeterminada  
 Puede cambiar el nombre de la carpeta raíz de los archivos de usuario para su aplicación cambiando el valor de la fila "UserFilesSubFolderName" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>El identificador de creador de archivo de solución  
 Puede cambiar el identificador utilizado para los archivos de solución, cambie el valor de la fila "SolutionFileCreatorIdentifier" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>La ubicación de proyectos predeterminada  
 Puede cambiar el nombre de la ubicación de proyectos predeterminado cambiando el valor de la fila "DefaultProjectsLocation" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>El paquete de localización de aplicaciones  
 Puede cambiar el paquete de localización usado para la aplicación cambiando el valor de la fila "AppLocalizationPackage" en el *SolutionName*. Archivo Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>La raíz de la jerarquía se muestra en el título o no  
 Puede especificar la raíz de la jerarquía se muestra en la barra de título de la aplicación cambiando el valor de la fila "ShowHierarchyRootInTitle" o no el *SolutionName*. Archivo Application.pkgdef. Para mostrar la raíz de la jerarquía, establezca el valor `dword:00000001`y para ocultar la raíz de la jerarquía, establezca el valor `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Especificar una página de inicio  
 Para especificar una página de inicio de la aplicación personalizada en el *SolutionName*. Archivo Application.pkgdef, establezca el valor de "DisableStartPage" en `dword:00000000`y en `[$RootKey$\StartPage\Default]` establece el URI en la ubicación del archivo .xaml:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 En el archivo Applicationcommands.vsct el *SolutionName*proyecto de interfaz de usuario, comente la entrada "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Debe agregar el archivo .xaml y los archivos de gráficos que necesita, a la *SolutionName* proyecto. En realidad, estos archivos deben copiarse en el *SolutionName* directorio del proyecto, no se agregó desde otro directorio.  
  
 En todos los archivos, establezca el **tipo de elemento de** propiedad **archivos de Shell aislado** en orden de los archivos que se copiarán en el *$RootFolder$* directory. (Para establecer el **tipo de elemento** propiedad, haga clic en el archivo y seleccione **propiedades**. Esta propiedad se encuentra en **propiedades de configuración**, **General**.)  
  
 Para obtener más información sobre la personalización de páginas de inicio, consulte [personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Uso de otros elementos del shell aislado  
 Puede usar otros archivos y proyectos que se incluyen en la plantilla de solución de shell aislado para personalizar aún más la aplicación.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Habilitar o deshabilitar los paquetes de Visual Studio  
 El *SolutionName*archivo .pkgundef le permite deshabilitar ciertas clases de funcionalidad de Visual Studio mediante la exclusión de determinados paquetes. Por ejemplo, la siguiente línea:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Quita el proyecto archivos varios del conjunto de plantillas de proyecto que se muestra en el **nuevo proyecto** cuadro de diálogo. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Habilitar o deshabilitar los comandos de menú  
 El *SolutionName*UI.vsct archivo incluye una lista de comentada de todos los comandos de menú disponibles en el shell aislado. Para deshabilitar un comando determinado, quite la fila correspondiente. Por ejemplo, para deshabilitar el comentario de la ventana o dividir, quite el `<Define name="No_SplitCommand"/>` fila. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>El mapa de bits utilizado en la pantalla de presentación  
 Puede personalizar el mapa de bits utilizado en la pantalla de presentación, que es la ventana que se muestra cuando se inicia la aplicación, cambiando el valor de la fila "SplashScreenBitmap" en el *SolutionName*. Archivo Application.pkgdef. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>La ayuda/acerca de la ventana  
 En la plantilla de shell aislado, hay un proyecto independiente se puede usar para personalizar la ayuda/acerca de la casilla de la aplicación. Para obtener más información, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).

