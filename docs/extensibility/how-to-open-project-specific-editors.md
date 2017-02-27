---
title: "C&#243;mo: abrir editores espec&#237;ficos del proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto, abra un editor específico del proyecto"
  - "editores [Visual Studio SDK], abrir los editores específicos del proyecto"
  - "proyectos [Visual Studio SDK], abrir carpetas"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: abrir editores espec&#237;ficos del proyecto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si un archivo del elemento que lo abre un proyecto se enlaza intrínseco al editor determinado para ese proyecto, el proyecto debe abrir el archivo con un editor específico del proyecto.  El archivo no se puede delegar hasta el mecanismo del IDE para seleccionar un editor.  Por ejemplo, en lugar de utilizar un editor bitmap estándar, puede utilizar esta opción específica de proyecto de editor de especificar un editor bitmap concreto que reconoce la información en el archivo que es único al proyecto.  
  
 El IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> cuando determina que un archivo se debe abrir por un proyecto concreto.  Para obtener más información, vea [Mostrar archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md).  Utilice las instrucciones siguientes para implementar el método de `OpenItem` para que el proyecto se abre un archivo con un editor específico del proyecto.  
  
### Para implementar el método de OpenItem con un editor específico de proyecto  
  
1.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> \(RDT\_EditLock\) para determinar si el archivo \(objeto del documento\) está abierto.  
  
    > [!NOTE]
    >  Para obtener más información sobre los datos del documento y objetos de vista de documentos, vea [Datos del documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Si el archivo está abierto, vuelva a mejorar el archivo llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> y especificando un valor de IDO\_ActivateIfOpen para el parámetro de `grfIDO` .  
  
     Si el archivo está abierto y el documento es propiedad de un proyecto distinto del proyecto de llamada, una advertencia se mostrará al usuario que el editor abierta es de otro proyecto.  La ventana del archivo se emerge.  
  
3.  Si el búfer de texto \(objeto del documento\) ya está abierto y desea asociar otra vista para, es responsable de enlazar encima de esa vista.  El enfoque recomendado para crear instancias de una vista \(objeto de vista del documento\) desde el proyecto, es como sigue:  
  
    1.  Llame a `QueryService` en el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> para obtener un puntero a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> .  
  
    2.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para crear una instancia de la clase de la vista del documento.  
  
4.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> , especificando el objeto de vista del documento.  
  
     Sitios de este método el objeto de vista del documento en una ventana de documento.  
  
5.  Realiza las llamadas adecuadas a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> o métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> .  
  
     En este punto, la vista debe inicializarse en todo momento y listo totalmente que desea abrir.  
  
6.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> para mostrar y para abrir la vista.  
  
## Vea también  
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores estándares](../extensibility/how-to-open-standard-editors.md)   
 [Cómo: abrir editores para los documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)