---
title: Administración de propietarios de bloqueo de documentos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8eaeb8529f570db112bf43813fe20339f3bca7c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786306"
---
# <a name="document-lock-holder-management"></a>Administración de propietarios de bloqueo de documentos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tabla de documentos de ejecución (RDT) mantiene un recuento de documentos abiertos y los bloqueos de edición que tienen. Puede colocar un bloqueo de edición en un documento en el RDT mientras se edita mediante programación en segundo plano sin que el usuario ve un documento abierto en una ventana de documento. Esta funcionalidad se utiliza a menudo por los diseñadores que modificar varios archivos a través de una interfaz gráfica de usuario.  
  
## <a name="document-lock-holder-scenarios"></a>Escenarios de titular de bloqueo de documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Archivo "a" una dependencia en el archivo tiene "b"  
 Considere una situación donde se implementa un editor estándar "A" para el tipo de archivo "a" y cada archivo de tipo "a" tiene una referencia a (o una dependencia de) un archivo de tipo "b". Existe un editor estándar "B" para archivos de tipo "b". Cuando abre el editor "A" archivo "a", lo recupera la referencia al archivo correspondiente "b". No se muestra el archivo "b", pero puede modificarla editor "A". Editor de "A" obtiene una referencia a los datos del documento de archivo "b" de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método y también mantiene un bloqueo de edición en el archivo "b". Modificar el archivo "b" puede disminuir el bloqueo de edición contar una vez realizado el editor "A" en el archivo "b" mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método. Puede omitir este paso si se hubiera llamado el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método con el parámetro `dwRDTLockType` establecido en <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Se abre el archivo "b" por otro Editor  
 En caso de que ya está abierto el archivo "b" Editor "B" cuando "A" editor intenta abrirlo, hay dos escenarios independientes para controlar:  
  
-   Si el archivo "b" está abierto en un editor compatible, debe tener editor "A" registrar un bloqueo de edición del documento sobre el uso de archivo "b" el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método. Después de que el editor "A" se realiza una modificación de archivo "b", anular el registro del documento editar bloqueo mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> método.  
  
-   Si el archivo "b" está abierto en un modo incompatible, se puede dejar que la apertura de intentada de archivo "b" Editor "A" por error, o puede dejar la vista asociada con el editor "A" parcialmente abre y mostrar un mensaje de error adecuado. El mensaje de error debe indicar al usuario para cerrar el archivo "b" en el editor incompatible y, a continuación, vuelva a abrir el archivo "a" usando el editor "A". También puede implementar la [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> para preguntar al usuario al cerrar el archivo "b" que está abierto en el editor incompatible. Si el usuario cierra el archivo "b", la apertura del archivo "a" in editor "A" continúa con normalidad.  
  
## <a name="additional-document-edit-lock-considerations"></a>Consideraciones de bloqueo de documento adicionales edición  
 Obtener un comportamiento diferente si el editor "A" es el único editor que tiene un documento de editar el bloqueo en el archivo "b" a como lo haría si editor "B" también contiene un documento de editar el bloqueo en el archivo "b". En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **Diseñador de clases** es un ejemplo de un diseñador visual que no contiene un bloqueo de edición en el archivo de código asociado. Es decir, si el usuario tiene un diagrama de clases abierto en la vista Diseño y el archivo de código asociado se abre al mismo tiempo, y si el usuario modifica el archivo de código, pero no guardar los cambios, los cambios también se pierden en el archivo de diagrama (. CD). Si el **Diseñador de clases** tiene el documento solo editar bloqueo en el archivo de código, el usuario no se le pide para guardar los cambios al cerrar el archivo de código. El IDE le pide al usuario para guardar los cambios solo después de que el usuario cierra el **Diseñador de clases**. Los cambios guardados se reflejan en ambos archivos. Si tanto el **Diseñador de clases** y el editor de archivos de código mantiene los bloqueos de edición del documento en el archivo de código, a continuación, se solicita al usuario guardar al cerrar el archivo de código o el formulario. En ese momento se reflejan los cambios guardados en el formulario y el archivo de código. Para obtener más información sobre los diagramas de clases, vea [trabajar con diagramas de clases (Diseñador de clases)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Tenga en cuenta que si tiene que colocar un bloqueo de edición en un documento para un no editor, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz.  
  
 Muchas veces un diseñador de IU que se modifica mediante programación los archivos de código realiza cambios en más de un archivo. En estos casos el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> método controla el almacenamiento de uno o varios documentos por medio de la **¿desea guardar los cambios en los siguientes elementos?** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)   
 [Persistencia y tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)

