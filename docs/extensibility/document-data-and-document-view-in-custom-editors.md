---
title: Datos de documento y vista de documento en editores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2aa8779a069f4b001743326470f69f3cb35a8c10
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568874"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Datos de documento y vista de documento en editores personalizados
Un editor personalizado consta de dos partes: un objeto de datos de documento y un objeto de vista de documento. Como sugieren los nombres, el objeto de datos del documento representa los datos de texto que se van a mostrar. Del mismo modo, el objeto de vista de documento (o "vista") representa una o más ventanas en las que se va a mostrar el objeto de datos del documento.

## <a name="document-data-object"></a>Objeto de datos de documento
 Un objeto de datos de documento es una representación de datos de texto en el búfer de texto. Es un objeto COM que almacena el texto del documento y otra información. El objeto de datos del documento también controla la persistencia del documento y permite varias vistas de sus datos. Para obtener más información, vea

 <xref:EnvDTE80.Window2.DocumentData%2A> y [ventanas de documento](../extensibility/internals/document-windows.md).

 Los editores y diseñadores personalizados pueden optar por usar el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> o su propio búfer personalizado. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sigue el modelo de incrustación simplificado para un editor estándar, admite varias vistas y proporciona interfaces de eventos que se usan para administrar varias vistas.

## <a name="document-view-object"></a>Objeto de vista de documento
 Una ventana que muestra código y otro texto se conoce como vista o vista de documento. Al crear un editor, puede elegir una sola vista, en la que el texto se muestra en una sola ventana. También puede elegir una vista múltiple, en la que el texto se muestra en más de una ventana. Su elección depende de la aplicación. Por ejemplo, si necesita la edición en paralelo, debe elegir vista múltiple. Cada vista está asociada a una entrada en la tabla de documentos en ejecución (IDE) de entorno de desarrollo integrado (IDE). Las ventanas de la vista pertenecen a un proyecto o a un objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.

 Si el editor admite varias vistas de un objeto de datos de documento, los datos de documento y los objetos de vista de documento deben ser independientes. De lo contrario, se pueden agrupar. Para obtener más información, vea [compatibilidad con varias vistas de documentos](../extensibility/supporting-multiple-document-views.md).

 El IDE notifica a las vistas acerca de los eventos (por ejemplo, cuando se cierra una solución que contiene un documento) haciendo coincidir un identificador de elemento (ItemID) con cada entrada de la tabla de documentos en ejecución. Para obtener más información sobre esto, vea [ejecutar la tabla de documentos](../extensibility/internals/running-document-table.md).

 Hay dos opciones para crear una vista para un editor personalizado. Uno es el modelo de activación en contexto, donde la vista se hospeda en una ventana con un control ActiveX o un objeto de datos de documento. El segundo es el modelo de incrustación simplificado, donde la vista se hospeda en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de la ventana. Para obtener información sobre el modelo de activación en contexto, consulte [activación en contexto](/visualstudio/misc/in-place-activation?view=vs-2015). Para obtener información sobre el modelo de incrustación simplificado, vea [incrustación simplificada](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Vea también

- [Compatibilidad con varias vistas de documento](../extensibility/supporting-multiple-document-views.md)
- [Incrustación simplificada](../extensibility/simplified-embedding.md)
- [Cómo: adjuntar vistas a datos de documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Administración de titulares de bloqueo de documentos](../extensibility/document-lock-holder-management.md)
- [Vistas de una y varias pestañas](../extensibility/single-and-multi-tab-views.md)
- [Guardar un documento estándar](../extensibility/internals/saving-a-standard-document.md)
- [Persistencia y la tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Determinar qué editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)