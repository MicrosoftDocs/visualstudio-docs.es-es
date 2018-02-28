---
title: Ver los datos del documento y documentos en editores personalizados | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7c7e24ed2db4538ab0fd38dbb85930452611f0ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Datos del documento y la vista de documento en editores personalizados
Un editor personalizado consta de dos partes: un objeto de datos de documento y un objeto de vista de documento. Como sugieren los nombres, el objeto de datos de documento representa los datos de texto que se mostrará y el objeto de vista de documento (o "vista") representa una o varias ventanas en el que se va a mostrar el objeto de datos del documento.  
  
## <a name="document-data-object"></a>Objeto de datos de documento  
 Un objeto de datos de documento es una representación de datos de texto en el búfer de texto. Es un objeto COM que almacena el texto del documento y otra información, controla la persistencia del documento y permite que varias vistas de sus datos. Para obtener más información, consulte  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>y [las ventanas de documento](../extensibility/internals/document-windows.md).  
  
 Editores personalizados y diseñadores, pueden optar por usar la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto o su propio búfer personalizado. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>sigue el modelo de incrustación simplificado para un editor estándar, es compatible con varias vistas y proporciona interfaces de eventos que se usan para administrar varias vistas.  
  
## <a name="document-view-object"></a>Objeto de vista de documento  
 Una ventana que muestra el código y otro texto se conoce como un documento de vista o la vista. Cuando se crea un editor, puede elegir una sola vista, en el que se muestra texto en una sola ventana, o una vista de varios, en el que se muestra texto en más de una ventana. La elección depende de la aplicación. Por ejemplo, si necesita editar side-by-side, elegiría MultipleView. Cada vista está asociado con una entrada en el entorno de desarrollo integrado de (IDE) ejecuta tabla document (RDT). Windows vista pertenecen a un proyecto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.  
  
 Si el editor admite varias vistas de un objeto de datos del documento, a continuación, los datos del documento y los objetos de vista de documento deben ser independientes. En caso contrario, se pueden agrupar juntos. Para obtener más información, consulte [admitir varias vistas de documento](../extensibility/supporting-multiple-document-views.md).  
  
 El IDE notifica vistas acerca de los eventos (por ejemplo, cuando se cierra una solución que contenga un documento) mediante la correspondencia de un identificador (ID) del elemento para cada entrada en la tabla de documento de ejecución. Para obtener más información sobre esto, consulte [ejecutando tabla Document](../extensibility/internals/running-document-table.md).  
  
 Hay dos opciones para crear una vista para un editor personalizado. Uno es el modelo de activación en contexto, donde se hospeda la vista en una ventana con un control ActiveX o un objeto de datos del documento. El segundo es el modelo de incrustación simplificado, donde se hospeda la vista por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de la ventana. Para obtener información sobre el modelo de activación en contexto, vea [activación en contexto](../extensibility/in-place-activation.md). Para obtener información sobre el modelo de incrustación simplificado, vea [incrustación simplificada](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Vea también  
 [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md)   
 [Simplifica la incrustación de objetos](../extensibility/simplified-embedding.md)   
 [Cómo: adjuntar vistas para datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Administración de propietario de bloqueo de documento](../extensibility/document-lock-holder-management.md)   
 [Vistas simples y múltiples pestaña](../extensibility/single-and-multi-tab-views.md)   
 [Guardar un documento estándar](../extensibility/internals/saving-a-standard-document.md)   
 [Persistencia y la tabla Document de ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinar qué Editor se abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Generadores de editores](../extensibility/editor-factories.md)