---
title: 'Cómo: abrir editores específica del proyecto | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae2e634d36c13632619d01cc97d5726dc5576819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-open-project-specific-editors"></a>Cómo: abrir editores específica del proyecto
Si un archivo de elemento que se está abriendo un proyecto intrínsecamente está enlazado al editor determinado para ese proyecto, el proyecto debe abrir el archivo con un editor específico del proyecto. El archivo no se puede delegar hasta del mecanismo del IDE para la selección de un editor. Por ejemplo, en lugar de utilizar un editor de mapa de bits estándar, puede usar esta opción de editor específico del proyecto para especificar un editor de mapa de bits específico que reconoce la información en el archivo que es único para el proyecto.  
  
 Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método cuando determina que se debe abrir un archivo de un proyecto específico. Para obtener más información, consulte [mostrar archivos mediante el comando archivo abrir](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilice las siguientes directrices para implementar la `OpenItem` método para que el proyecto abra un archivo con un editor específico del proyecto.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Para implementar el método OpenItem con un editor específico del proyecto  
  
1.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> (método) (RDT_EditLock) para determinar si el archivo (objeto de datos de documento) ya está abierto.  
  
    > [!NOTE]
    >  Para obtener más información sobre datos del documento y los objetos de vista de documento, consulte [datos del documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Si el archivo ya está abierto, reaparece el archivo mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método y especificando un valor de IDO_ActivateIfOpen para el `grfIDO` parámetro.  
  
     Si el archivo está abierto y el documento pertenece a un proyecto distinto del que realiza la llamada, se mostrará una advertencia al usuario que sea el editor que se está abriendo desde otro proyecto. A continuación, aparece la ventana de archivo.  
  
3.  Si el búfer de texto (objeto de datos de documento) ya está abierto y que desea conectar otra vista a ella, es responsabilidad suya enlazar esa vista. El método recomendado para crear instancias de una vista (objeto de vista de documento) desde el proyecto, es como sigue:  
  
    1.  Llame a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> servicio para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfaz.  
  
    2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> método para crear una instancia de la clase de vista de documento.  
  
4.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> método, especificando el objeto de vista de documento.  
  
     Este método sitios el objeto de vista de documento en una ventana de documento.  
  
5.  Realizar las llamadas adecuadas a cualquiera la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> métodos.  
  
     En este momento, la vista debe ser totalmente inicializado y listo para abrirse.  
  
6.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para mostrar y abrir la vista.  
  
## <a name="see-also"></a>Vea también  
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores estándares](../extensibility/how-to-open-standard-editors.md)   
 [Apertura de editores para documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)