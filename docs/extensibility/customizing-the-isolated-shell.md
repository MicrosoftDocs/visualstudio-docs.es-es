---
title: "Personalizar el Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell de Visual Studio, modo aislado"
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Personalizar el Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede personalizar la aplicación de shell aislado de Visual Studio cambiando distintos aspectos de la interfaz de usuario de Visual Studio y restringiendo los comandos y las características incluidas en la aplicación especializada.  
  
## Mediante el archivo Application.pkgdef  
 La solución de plantilla de shell aislado incluye un *SolutionName*. Archivo de Application.pkgdef que le permite modificar las siguientes características:  
  
##### El título de la aplicación  
 Puede personalizar el título de la aplicación, que es el nombre que se muestra en la barra de título de la aplicación, cambiando el valor de la fila "AppName" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si no desea que el título de la aplicación para mostrar el proyecto que está cargado actualmente, cambie el valor de la fila "ShowHierarchyRootInTitle" en la *nombresolución*. Archivo de Application.pkgdef de DWORD: 00000001 para DWORD: 00000000.  
  
##### El icono de la aplicación  
 Puede personalizar el icono de la aplicación mediante el icono que muestra el nombre de la aplicación en la barra de título de la aplicación. Copiar un icono diferente en el directorio de icono. En **el Explorador de soluciones**, agregar el icono de la carpeta archivos de recursos. A continuación, abra el archivo VSShellStub.rc y reemplace el valor de IDI\_STUBPROGRAM por el nombre del nuevo icono. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### El logotipo de la línea de comandos  
 Puede personalizar el logotipo de línea de comandos, que es el texto que aparece cuando se inicia la aplicación desde la línea de comandos, cambie el valor de la fila "CommandLineLogo" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### El nombre de la subcarpeta de archivos de usuario  
 Puede cambiar el nombre de la carpeta de la aplicación se mantiene para los archivos de usuario cambiando el valor de la fila "UserFilesSubFolderName" *nombresolución*. Archivo Application.pkgdef.  
  
##### El título del nodo del árbol de solución en el cuadro de diálogo nuevo proyecto  
 Puede personalizar el título del nodo de solución en el cuadro de diálogo nuevo proyecto, cambie el valor de la fila "NewProjDlgSlnTreeNodeTitle" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### El encabezado de plantillas instaladas en el cuadro de diálogo nuevo proyecto  
 Puede cambiar el encabezado de plantillas instaladas en el cuadro de diálogo nuevo proyecto, cambie el valor de la fila "NewProjDlgInstalledTemplatesHdr" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### Si desea ocultar archivos varios de manera predeterminada o no  
 Puede especificar si desea ocultar archivos varios de manera predeterminada, cambie el valor de la fila "HideMiscellaneousFilesByDefault" o no el *SolutionName*. Archivo Application.pkgdef. Para ocultar archivos varios, establezca el valor `dword:00000001`, y para mostrar los archivos, establezca el valor `dword:00000000`.  
  
##### Si desea deshabilitar la ventana de salida o no  
 Puede especificar si desea deshabilitar la ventana de salida de la aplicación cambiando el valor de la fila "DisableOutputWindow" o no el *SolutionName*. Archivo Application.pkgdef. Para deshabilitar la ventana de salida, establezca el valor `dword:00000001`, y para mostrar la ventana de salida, establezca el valor `dword:00000000`.  
  
##### Si desea permitir que los archivos colocados en la ventana principal o no  
 Puede especificar si se debe o no permitir que los archivos colocados en la ventana principal de la aplicación cambiando el valor de la fila "AllowsDroppedFilesOnMainWindow" en la *nombresolución*. Archivo Application.pkgdef. Para permitir que los archivos eliminados, establezca el valor `dword:00000001`, y para no permitir archivos colocados, establezca el valor `dword:00000000`.  
  
##### La página de búsqueda predeterminada  
 Puede personalizar la página del explorador web, que es la página que se muestra cuando se abre la ventana del explorador web, cambiando el valor de la fila "DefaultSearchPage" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### La página principal predeterminada  
 Puede personalizar la página principal, cambie el valor de la fila "DefaultHomePage" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### Si desea ocultar el concepto de solución o no  
 Puede especificar si desea ocultar la solución en la aplicación cambiando el valor de la fila "HideSolutionConcept" o no el *SolutionName*. Archivo Application.pkgdef. Para ocultar la solución, establezca el valor `dword:00000001`, y para mostrar la solución, establezca el valor `dword:00000000`.  
  
##### El motor de depuración predeterminada  
 Puede cambiar el motor de depuración que usa la aplicación cambiando el valor de la fila "DefaultDebugEngine" en la *nombresolución*. Archivo Application.pkgdef al GUID de su motor de depuración.  
  
##### La extensión de archivo del archivo de opciones de usuario  
 Puede cambiar el nombre de la carpeta de la aplicación se mantiene para los archivos de usuario cambiando el valor de la fila "UserOptsFileExt" *nombresolución*. Archivo Application.pkgdef.  
  
##### La extensión de archivo de solución  
 Puede cambiar la extensión utilizada para los archivos de solución, cambie el valor de la fila "SolutionFileExt" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### La raíz de carpetas de archivos de usuario predeterminado  
 Puede cambiar el nombre de la carpeta raíz de los archivos de usuario de la aplicación cambiando el valor de la fila "UserFilesSubFolderName" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### El identificador de creador de archivo de solución  
 Puede cambiar el identificador usado para los archivos de solución, cambie el valor de la fila "SolutionFileCreatorIdentifier" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### La ubicación de proyectos predeterminada  
 Puede cambiar el nombre de la ubicación de proyectos predeterminada cambiando el valor de la fila "DefaultProjectsLocation" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### El paquete de la localización de aplicaciones  
 Puede cambiar el paquete de localización usado para la aplicación cambiando el valor de la fila "AppLocalizationPackage" en la *nombresolución*. Archivo Application.pkgdef.  
  
##### Si se debe o no mostrar la raíz de la jerarquía en el título  
 Puede especificar si se debe o no mostrar la raíz de la jerarquía en la barra de título de la aplicación cambiando el valor de la fila "ShowHierarchyRootInTitle" en la *nombresolución*. Archivo Application.pkgdef. Para mostrar la raíz de la jerarquía, establezca el valor `dword:00000001`, y para ocultar la raíz de la jerarquía, establezca el valor `dword:00000000`.  
  
##### Especificar una página de inicio  
 Para especificar una página de inicio para la aplicación personalizada en el *SolutionName*. Archivo Application.pkgdef, establezca el valor de "DisableStartPage" en `dword:00000000`, y en `[$RootKey$\StartPage\Default]` establecer el URI a la ubicación del archivo .xaml:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 En el archivo Applicationcommands.vsct en la *nombresolución*proyecto de interfaz de usuario, comente la entrada "No\_ShellPkg\_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Debe agregar el archivo .xaml y los archivos de gráficos que necesite, a la *nombresolución* proyecto. En realidad, estos archivos deben copiarse en el *SolutionName* directorio del proyecto, no se agregó desde otro directorio.  
  
 En todos los archivos, establezca la **tipo de elemento** propiedad **aislado de archivos de Shell** en orden de los archivos se copien en el *$RootFolder$* directory. \(Para establecer el **tipo de elemento** propiedad, haga clic en el archivo y seleccione **propiedades**. Esta propiedad se encuentra en **Propiedades de configuración**, **General**.\)  
  
 Para obtener más información acerca de cómo personalizar páginas de inicio, consulte [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## Uso de otros elementos del shell aislado  
 Puede utilizar otros archivos y proyectos que se incluyen en la plantilla de solución de shell aislado para personalizar aún más la aplicación.  
  
##### Habilitar o deshabilitar los paquetes de Visual Studio  
 El *nombresolución*.pkgundef archivo le permite deshabilitar ciertos tipos de funcionalidad de Visual Studio mediante la exclusión de ciertos paquetes. Por ejemplo, la siguiente línea:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Quita el proyecto de archivos varios del conjunto de plantillas de proyecto que se muestra en el **nuevo proyecto** cuadro de diálogo. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### Habilitar o deshabilitar comandos de menú  
 El *nombresolución*UI.vsct archivo incluye una lista de comentario de todos los comandos de menú disponibles al shell aislado. Para deshabilitar un comando determinado, quite la fila correspondiente. Por ejemplo, para deshabilitar el comentario de la ventana de división, quite el `<Define name="No_SplitCommand"/>` fila. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### Mapa de bits utilizado en la pantalla de presentación  
 Puede personalizar el mapa de bits utilizado en la pantalla de presentación, que es la ventana que se muestra cuando se inicia la aplicación, cambiando el valor de la fila "SplashScreenBitmap" en la *nombresolución*. Archivo Application.pkgdef. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### La ayuda\/acerca de la ventana  
 En la plantilla de shell aislado, hay un proyecto independiente que se puede utilizar para personalizar la ayuda acerca del cuadro de la aplicación. Para obtener más información, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).