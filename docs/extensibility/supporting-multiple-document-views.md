---
title: Admitir varias vistas del documento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4efd76830356996bdf75c923f457d19d2381763c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-document-views"></a>Admitir varias vistas del documento
Puede proporcionar más de una vista de un documento mediante la creación de datos de documentos independientes y objetos de vista de documento para el editor. Algunos casos en que una vista de documento adicionales sería útil son:  
  
-   Nueva compatibilidad con las ventanas: desea que el editor para proporcionar dos o más vistas del mismo tipo, por lo que un usuario que ya tiene una ventana abierta en el editor puede abrir una ventana nueva, seleccione la **nueva ventana** línea de comandos desde el **ventana** menú.  
  
-   Admite en las vistas formulario y el código: desea que el editor para proporcionar vistas de tipos diferentes. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por ejemplo, proporciona una vista de formulario y una vista de código.  
  
 Para obtener más información sobre esto, vea el procedimiento de CreateEditorInstance en el archivo EditorFactory.cs en el proyecto de editor personalizado creado por la plantilla de paquete de Visual Studio. Para obtener más información sobre este proyecto, vea [Tutorial: crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Sincronizando las vistas  
 Al implementar varias vistas, el objeto de datos de documento es responsable de mantener sincronizadas con los datos de todas las vistas. También puede usar el evento control interfaces en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para sincronizar varias vistas con los datos.  
  
 Si no utiliza la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que se va a sincronizar varias vistas, a continuación, debe implementar su propio sistema de eventos para controlar los cambios realizados en el objeto de datos del documento. Puede utilizar distintos niveles de granularidad para mantener actualizado varias vistas. Con un valor de granularidad máximo, a medida que escribe en una vista las otras vistas se actualizan inmediatamente. Con una granularidad mínima, otras vistas no se actualizan hasta que se activan.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Determinar los datos del documento si ya está abierto  
 La tabla document ejecución (RDT) en el entorno de desarrollo integrado (IDE) le ayuda a realizar un seguimiento de si los datos de un documento ya estén abiertos, como se muestra en el diagrama siguiente.  
  
 ![Gráfico de DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Varias vistas  
  
 De forma predeterminada, cada vista (objeto de vista de documento) se encuentra en su propio marco de ventana (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Como ya se indicó, sin embargo, los datos de documento se pueden mostrar en varias vistas. Para habilitar esta opción, Visual Studio comprueba el RDT para determinar si el documento en cuestión ya está abierto en un editor. Cuando se llama el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear el editor, se devuelve un valor distinto de NULL en la `punkDocDataExisting` parámetro indica que el documento ya está abierto en otro editor. Para obtener más información acerca de cómo ver las funciones RDT, [ejecutando tabla Document](../extensibility/internals/running-document-table.md).  
  
 En su <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementación, examine el objeto de datos de documento devuelto en `punkDocDataExisting` para determinar si los datos del documento están adecuados para el editor. (Por ejemplo, solo los datos HTML deben mostrarse mediante un editor de HTML.) Si es adecuado, el generador de editores debe proporcionar una segunda vista para los datos. Si el `punkDocDataExisting` parámetro no es `NULL`, es posible ya que el objeto de datos de documento está abierto en otro editor o, más probable, que los datos del documento ya está abiertos en una vista diferente con el mismo que el editor. Si los datos del documento están abiertos en un editor distinto que no es compatible con el generador de editores, a continuación, Visual Studio genera un error abrir el generador de editores. Para obtener más información, consulte [Cómo: adjuntar vistas a datos del documento](../extensibility/how-to-attach-views-to-document-data.md).