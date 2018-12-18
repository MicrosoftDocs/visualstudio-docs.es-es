---
title: Ver datos del documento y el documento en editores personalizados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2076f1a6c96aea717470fa1e955e5b9786f7fcc5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639820"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Datos del documento y vista de documento en editores personalizados
Un editor personalizado consta de dos partes: un objeto de datos de documento y un objeto de vista de documento. Como sugieren los nombres, el objeto de datos representa los datos de texto que se mostrará. De forma similar, el objeto de vista de documento (o "vista") representa una o varias ventanas en el que se va a mostrar el objeto de datos.  
  
## <a name="document-data-object"></a>Objeto de datos de documento  
 Un objeto de datos de documento es una representación de datos de texto en el búfer de texto. Es un objeto COM que almacena el texto del documento y otra información. El objeto de datos también administra la persistencia del documento y permite que varias vistas de sus datos. Para obtener más información, consulte  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> y [documentar Windows](../extensibility/internals/document-windows.md).  
  
 Diseñadores y editores personalizados pueden optar por usar la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto o su propio búfer personalizado. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sigue el modelo de incrustación simplificado para un editor estándar admite varias vistas y proporciona interfaces de eventos que se usan para administrar varias vistas.  
  
## <a name="document-view-object"></a>Objeto de vista de documento  
 Una ventana que muestra el código y otro texto se conoce como un documento de vista o vista. Cuando se crea un editor, puede elegir una vista única, en el que se muestra texto en una sola ventana. O bien, puede elegir una vista de varias, en el que se muestra texto en más de una ventana. La elección depende de la aplicación. Por ejemplo, si necesita modificar en paralelo, elegiría MultipleView. Cada vista se asocia con una entrada en el entorno de desarrollo integrado de (IDE de) ejecución (RDT) de tabla de documentos. Windows vista pertenecen a un proyecto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.  
  
 Si el editor admite varias vistas de un objeto de datos de documento, a continuación, los datos del documento y los objetos de vista de documento deben ser independientes. En caso contrario, se pueden agrupar juntos. Para obtener más información, consulte [admite varias vistas de documento](../extensibility/supporting-multiple-document-views.md).  
  
 El IDE notifica vistas sobre eventos (por ejemplo, cuando se cierra una solución que contiene un documento) mediante la coincidencia de un identificador (ID) del elemento para cada entrada de la tabla de documentos en ejecución. Para obtener más información, consulte [ejecutando la tabla de documentos](../extensibility/internals/running-document-table.md).  
  
 Hay dos opciones para crear una vista para un editor personalizado. Uno es el modelo de activación en contexto, donde la vista se hospeda en una ventana con un control ActiveX o un objeto de datos del documento. El segundo es el modelo de incrustación simplificado, donde se hospeda la vista por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de ventana. Para obtener información sobre el modelo de activación en contexto, vea [activación en contexto](../extensibility/in-place-activation.md). Para obtener información sobre el modelo de incrustación simplificado, vea [incrustación simplificada](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Vea también  
 [Admite varias vistas de documento](../extensibility/supporting-multiple-document-views.md)   
 [Incrustación simplificada](../extensibility/simplified-embedding.md)   
 [Cómo: adjuntar vistas a datos del documento](../extensibility/how-to-attach-views-to-document-data.md)   
 [Administración de propietarios de bloqueo de documento](../extensibility/document-lock-holder-management.md)   
 [Vistas únicas y varias pestañas](../extensibility/single-and-multi-tab-views.md)   
 [Guardar un documento estándar](../extensibility/internals/saving-a-standard-document.md)   
 [Persistencia y la tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinar qué editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Generadores de editores](../extensibility/editor-factories.md)