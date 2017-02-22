---
title: "Crear una instancia del Editor principal mediante la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - crear una instancia del editor"
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Crear una instancia del Editor principal mediante la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor es responsable de las funciones como la inserción, eliminación, copiar y pegar de edición de texto. Combina estas funciones con las que proporcionan servicios de lenguaje, como el color de texto, la sangría y la finalización de instrucciones de IntelliSense.  
  
 Puede crear una instancia del editor principal en una de tres maneras:  
  
-   Crear explícitamente una instancia del núcleo de editor en una ventana.  
  
-   Proporcionar un generador de editores que devuelve una instancia del editor principal  
  
-   Abrir un archivo desde la jerarquía del proyecto.  
  
 Las secciones siguientes describen cómo usar la API heredada para crear una instancia del editor.  
  
## Abrir explícitamente una instancia del Editor principal  
 Al obtener explícitamente una instancia del editor principal:  
  
-   Obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para mantener el objeto de datos de documento que se está editando.  
  
-   Crear una representación de línea orientada a servicios de objeto de datos de documentos mediante la creación de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> de la interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz.  
  
-   Establecer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> como el objeto de datos de documentos de una instancia de la implementación predeterminada de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfaz, usando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> \(método\).  
  
     Host la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> de la instancia en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz utilizando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> \(método\).  
  
 En este punto, mostrar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz proporciona una ventana que contiene una instancia del editor principal.  
  
 Sin embargo, esto no es una instancia muy útil, porque no tienen teclas de método abreviado, o tener acceso a características avanzadas. Para obtener acceso a características avanzadas y teclas de método abreviado:  
  
-   Utilice la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> para asociar un servicio de lenguaje y el objeto de datos de documento que utiliza el editor.  
  
-   Crear teclas de método abreviado, o utilizar el valor predeterminado del sistema estableciendo la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objetos mostrarán propiedades. Para ello, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> método con el <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propiedad.  
  
     Para obtener y usar teclas de método abreviado no estándar, generarlos utilizando el archivo .vsct. Para obtener más información, consulta [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Cómo usar un generador del Editor para obtener el Editor principal  
 Al implementar un editor principal con una fábrica de editor mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(método\), siga todos los pasos descritos en la sección anterior para hospedar explícitamente una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> con una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto de datos del documento, en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto.  
  
 Para mostrar el texto, obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto y llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(método\).  
  
 Para proporcionar un servicio de lenguaje para el editor, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método dentro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(método\).  
  
 Para obtener predeterminado teclas de método abreviado, a diferencia de la sección anterior, se usa el contexto de comandos devolviendo por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(método\) al obtener el editor principal de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(método\).  
  
 Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método devuelve el mismo GUID de comando como el editor de texto, la instancia del editor de núcleo obtiene automáticamente el valor predeterminado teclas de método abreviado.  
  
 Para obtener información general, consulte [Tutorial: Crear un Editor principal y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Tutorial: Crear un Editor principal y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)