---
title: Ver datos del documento y el documento en editores personalizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f73ffde43f2ef3608ae492a9643f7920243d818
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987698"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Datos de documento y vista de documento en editores personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un editor personalizado consta de dos partes: un objeto de datos de documento y un objeto de vista de documento. Como sugieren los nombres, el objeto de datos representa los datos de texto que se mostrará y el objeto de vista de documento (o "vista") representa una o varias ventanas en el que se va a mostrar el objeto de datos.  
  
## <a name="document-data-object"></a>Objeto de datos de documento  
 Un objeto de datos de documento es una representación de datos de texto en el búfer de texto. Es un objeto COM que almacena el texto del documento y otra información, controla la persistencia del documento y habilita varias vistas de sus datos. Para obtener más información, consulte  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> y [documentar Windows](../extensibility/internals/document-windows.md).  
  
 Diseñadores y editores personalizados pueden optar por usar la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto o su propio búfer personalizado. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sigue el modelo de incrustación simplificado para un editor estándar admite varias vistas y proporciona interfaces de eventos que se usan para administrar varias vistas.  
  
## <a name="document-view-object"></a>Objeto de vista de documento  
 Una ventana que muestra el código y otro texto se conoce como un documento de vista o vista. Cuando se crea un editor, puede elegir una sola vista, en el que se muestra texto en una sola ventana, o una vista de varias, en el que se muestra texto en más de una ventana. La elección depende de la aplicación. Por ejemplo, si necesita modificar en paralelo, elegiría MultipleView. Cada vista se asocia con una entrada en el entorno de desarrollo integrado de (IDE de) ejecución (RDT) de tabla de documentos. Windows vista pertenecen a un proyecto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.  
  
 Si el editor admite varias vistas de un objeto de datos de documento, a continuación, los datos del documento y los objetos de vista de documento deben ser independientes. En caso contrario, se pueden agrupar juntos. Para obtener más información, consulte [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
 El IDE notifica vistas sobre eventos (por ejemplo, cuando se cierra una solución que contiene un documento) mediante la coincidencia de un identificador (ID) del elemento para cada entrada de la tabla de documentos en ejecución. Para obtener más información, consulte [tabla de documentos en ejecución](../extensibility/internals/running-document-table.md).  
  
 Hay dos opciones para crear una vista para un editor personalizado. Uno es el modelo de activación en contexto, donde la vista se hospeda en una ventana con un control ActiveX o un objeto de datos del documento. El segundo es el modelo de incrustación simplificado, donde se hospeda la vista por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de ventana. Para obtener información sobre el modelo de activación en contexto, vea [activación en contexto](../misc/in-place-activation.md). Para obtener información sobre el modelo de incrustación simplificado, vea [incrustación simplificada](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con varias vistas de documento](../extensibility/supporting-multiple-document-views.md)   
 [Incrustación simplificada](../extensibility/simplified-embedding.md)   
 [Cómo: Anexión de vistas de datos de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Administración de propietarios de bloqueo de documento](../extensibility/document-lock-holder-management.md)   
 [Vistas únicas y varias pestañas](../extensibility/single-and-multi-tab-views.md)   
 [Guardar un documento estándar](../extensibility/internals/saving-a-standard-document.md)   
 [Persistencia y la tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinar qué Editor se abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Generadores del editor](../extensibility/editor-factories.md)
