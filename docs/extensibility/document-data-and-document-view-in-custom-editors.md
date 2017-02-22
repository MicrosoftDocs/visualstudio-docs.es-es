---
title: "Datos del documento y vista de documento en editores personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - datos de documentos y vista de documento"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Datos del documento y vista de documento en editores personalizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un editor personalizado consta de dos partes: un objeto de datos de documento y un objeto de vista de documento. Como sugieren los nombres, el objeto de datos de documento representa los datos de texto que se mostrará y el objeto de vista de documento \(o "view"\) representa una o varias ventanas para mostrar el objeto de datos del documento.  
  
## Objeto de datos de documento  
 Un objeto de datos de documento es una representación de datos de texto en el búfer de texto. Es un objeto COM que almacena el texto del documento y otra información, administra la persistencia del documento y permite varias vistas de sus datos. Para obtener más información, vea  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> y [Ventanas de documento](../extensibility/internals/document-windows.md).  
  
 Editores personalizados y diseñadores pueden optar por usar la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto o su propio búfer personalizado.<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sigue el modelo de incrustación simplificado para un editor estándar, admite varias vistas y proporciona interfaces de eventos que se usan para administrar varias vistas.  
  
## Objeto de vista de documento  
 Una ventana que muestra el código y cualquier otro texto se conoce como un documento de vista o vista. Cuando se crea un editor, puede elegir una sola vista, en el que se muestra texto en una sola ventana, o una vista de varios, en el que se muestra texto en más de una ventana. La elección depende de la aplicación. Por ejemplo, si necesita editar side\-by\-side, elegiría MultipleView. Cada vista está asociado a una entrada en el entorno de desarrollo integrado de \(IDE\) ejecuta la tabla document \(RDT\). Windows vista pertenecen a un proyecto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.  
  
 Si el editor admite varias vistas de un objeto de datos del documento, a continuación, los datos del documento y los objetos de vista de documento deben ser independientes. De lo contrario, se pueden agrupar juntos. Para obtener más información, consulta [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md).  
  
 El IDE notifica vistas sobre eventos \(por ejemplo, cuando se cierra una solución que contenga un documento\) mediante la coincidencia de un identificador \(ID\) del elemento para cada entrada en la tabla del documento de ejecución. Para obtener más información sobre este tema vea [Tabla de documentos de ejecución](../extensibility/internals/running-document-table.md).  
  
 Hay dos opciones para crear una vista para un editor personalizado. Uno es el modelo de activación en contexto, donde se hospeda la vista en una ventana con un control ActiveX o un objeto de datos del documento. El segundo es el modelo de incrustación simplificado, donde se hospeda la vista por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de ventana. Para obtener información sobre el modelo de activación en contexto, vea [activación en contexto](../misc/in-place-activation.md). Para obtener información sobre el modelo de incrustación simplificado, vea [Incrustación simplificada](../extensibility/simplified-embedding.md).  
  
## Vea también  
 [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md)   
 [Incrustación simplificada](../extensibility/simplified-embedding.md)   
 [Cómo: adjuntar vistas de datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Administración de propietario de bloqueo de documento](../extensibility/document-lock-holder-management.md)   
 [Únicas y ficha múltiples vistas](../extensibility/single-and-multi-tab-views.md)   
 [Guardar un documento estándar](../extensibility/internals/saving-a-standard-document.md)   
 [Persistencia y la tabla Document de ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinar qué Editor se abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Generadores de editores](../extensibility/editor-factories.md)