---
title: Procedimiento Apertura de editores específicos del proyecto | Documentos de Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: 96f760163fcbe80e53cca78f7d554563ff6b7225
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934419"
---
# <a name="how-to-open-project-specific-editors"></a>Procedimiento Abrir editores específicos del proyecto
Si el editor de ese proyecto concreto intrínsecamente depende de un archivo de elemento que se va a abrir un proyecto, el proyecto debe abrir el archivo con un editor específico del proyecto. El archivo no se puede delegar hasta el mecanismo de IDE para seleccionar un editor. Por ejemplo, en lugar de usar un editor de mapa de bits estándar, puede usar esta opción de editor específica del proyecto para especificar un editor específico del mapa de bits que reconoce la información en el archivo que es único para el proyecto.  
  
 Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método cuando determina que un archivo se debe abrir un proyecto específico. Para obtener más información, consulte [mostrar archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilice las siguientes directrices para implementar el `OpenItem` método para que el proyecto de abrir un archivo con un editor específico del proyecto.  
  
## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Para implementar el método OpenItem con un editor específico del proyecto  
  
1.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método (`RDT_EditLock`) para determinar si el archivo (objeto de datos de documento) ya está abierto.  
  
    > [!NOTE]
    >  Para obtener más información acerca de los datos del documento y los objetos de vista de documento, consulte [vista de datos y el documento en editores personalizados de documento](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Si el archivo ya está abierto, reaparece el archivo mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método y especificando un valor de IDO_ActivateIfOpen para el `grfIDO` parámetro.  
  
     Si el archivo está abierto y el documento es propiedad de un proyecto distinto del que realiza la llamada, se mostrará una advertencia al usuario que es el editor que se está abriendo desde otro proyecto. A continuación, aparece la ventana de archivo.  
  
3.  Si el búfer de texto (objeto de datos de documento) ya está abierto y desea utilizar otra vista, usted es responsable de enlazar esa vista. El método recomendado para crear instancias de una vista (objeto de vista de documento) del proyecto, es como sigue:  
  
    1.  Llame a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> service para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfaz.  
  
    2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> método para crear una instancia de la clase de vista de documento.  
  
4.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> método, especificando el objeto de vista del documento.  
  
     Este método sitios el objeto de vista de documento en una ventana de documento.  
  
5.  Realizar las llamadas adecuadas a cualquiera la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> métodos.  
  
     En este momento, la vista debe ser totalmente inicializado y listo para abrirse.  
  
6.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para mostrar y abra la vista.  
  
## <a name="see-also"></a>Vea también  
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: Abrir editores estándar](../extensibility/how-to-open-standard-editors.md)   
 [Cómo: Apertura de editores para documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)