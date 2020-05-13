---
title: Datos de documentos y vista de documentos en editores personalizados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712144"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Datos de documentos y vista de documentos en editores personalizados
Un editor personalizado consta de dos partes: un objeto de datos de documento y un objeto de vista de documento. Como sugieren los nombres, el objeto de datos del documento representa los datos de texto que se van a mostrar. Del mismo modo, el objeto de vista de documento (o "vista") representa una o varias ventanas en las que se va a mostrar el objeto de datos del documento.

## <a name="document-data-object"></a>Objeto de datos de documento
 Un objeto de datos de documento es una representación de datos de texto en el búfer de texto. Es un objeto COM que almacena texto del documento y otra información. El objeto de datos de documento también controla la persistencia del documento y habilita varias vistas de sus datos. Para obtener más información, vea

 <xref:EnvDTE80.Window2.DocumentData%2A>y [Documento de Windows](../extensibility/internals/document-windows.md).

 Los editores y diseñadores <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> personalizados pueden optar por usar el objeto o su propio búfer personalizado. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>sigue el modelo de incrustación simplificado para un editor estándar, admite varias vistas y proporciona interfaces de eventos que se utilizan para administrar varias vistas.

## <a name="document-view-object"></a>Objeto de vista de documento
 Una ventana que muestra código y otro texto se conoce como vista o vista de documento. Al crear un editor, puede elegir una sola vista, en la que el texto se muestra en una sola ventana. O bien, puede elegir una vista múltiple, en la que el texto se muestra en más de una ventana. Su elección depende de su aplicación. Por ejemplo, si necesita una edición en paralelo, elegiría varias vistas. Cada vista está asociada a una entrada en la tabla de documentos en ejecución (RDT) del entorno de desarrollo integrado (IDE). Las ventanas de vista <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> pertenecen a un proyecto o a un objeto.

 Si el editor admite varias vistas de un objeto de datos de documento, los datos del documento y los objetos de vista de documento deben ser independientes. De lo contrario, se pueden agrupar. Para obtener más información, consulte [Compatibilidad con varias vistas](../extensibility/supporting-multiple-document-views.md)de documentos.

 El IDE notifica las vistas sobre los eventos (por ejemplo, cuando se cierra una solución que contiene un documento) haciendo coincidir un identificador de elemento (ItemID) para cada entrada de la tabla de documento sin ejecución. Para obtener más información al respecto, consulte Ejecución de la tabla de [documentos](../extensibility/internals/running-document-table.md).

 Hay dos opciones para crear una vista para un editor personalizado. Uno es el modelo de activación en contexto, donde la vista se hospeda en una ventana mediante un control ActiveX o un objeto de datos de documento. El segundo es el modelo de incrustación [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] simplificado, donde la vista está hospedada y <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de ventana. Para obtener información sobre el modelo de activación in situ, consulte [Activación en contexto](/visualstudio/misc/in-place-activation?view=vs-2015). Para obtener información sobre el modelo de incrustación simplificado, consulte [Incrustación simplificada](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Vea también

- [Soporta múltiples vistas de documentos](../extensibility/supporting-multiple-document-views.md)
- [Incrustación simplificada](../extensibility/simplified-embedding.md)
- [Cómo: Adjuntar vistas a los datos del documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Gestión del soporte de bloqueo de documentos](../extensibility/document-lock-holder-management.md)
- [Vistas de una y varias pestañas](../extensibility/single-and-multi-tab-views.md)
- [Guardar un documento estándar](../extensibility/internals/saving-a-standard-document.md)
- [Persistencia y la tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Determinar qué editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
