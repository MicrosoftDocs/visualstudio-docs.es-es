---
title: Gestión de soportes de bloqueo de documentos (Document Lock Holder Management) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712121"
---
# <a name="document-lock-holder-management"></a>Gestión del soporte de bloqueo de documentos

La tabla de documentos en ejecución (RDT) mantiene un recuento de documentos abiertos y los bloqueos de edición que tienen. Puede colocar un bloqueo de edición en un documento en el RDT cuando se edita mediante programación en segundo plano sin que el usuario vea un documento abierto en una ventana de documento. Esta funcionalidad es utilizada a menudo por diseñadores que modifican varios archivos a través de una interfaz gráfica de usuario.

## <a name="document-lock-holder-scenarios"></a>Escenarios de soporte de bloqueo de documentos

### <a name="file-a-has-a-dependence-on-file-b"></a>El archivo "a" depende del archivo "b"

Considere una situación en la que implemente un editor estándar "A" para el tipo de archivo "a", y cada archivo de tipo "a" tiene una referencia a (o dependencia de) un archivo de tipo "b". Existe un editor estándar "B" para archivos de tipo "b". Cuando el editor "A" abre el archivo "a" recupera la referencia al archivo correspondiente "b". El archivo "b" no se muestra, pero el editor "A" puede modificarlo. Editor "A" obtiene una referencia a los datos del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> documento del archivo "b" del método y también mantiene un bloqueo de edición en el archivo "b". Después de que el editor "A" haya terminado de modificar el archivo "b" puede disminuir el recuento de bloqueo de edición en el archivo "b" llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método. Puede omitir este paso si <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> ha llamado `dwRDTLockType` al método con el parámetro establecido en [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>El archivo "b" es abierto por un editor diferente

En el caso de que el archivo "b" ya esté abierto por el editor "B" cuando el editor "A" intenta abrirlo, hay dos escenarios independientes para manejar:

- Si el archivo "b" está abierto en un editor compatible, debe tener el editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> "A" registrar un bloqueo de edición de documento en el archivo "b" utilizando el método. Después de que el editor "A" haya terminado de modificar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> el archivo "b", anule el registro del bloqueo de edición de documentos utilizando el método.

- Si el archivo "b" está abierto de una manera incompatible, puede dejar que el intento de apertura del archivo "b" por el editor "A" falle, o puede dejar que la vista asociada con el editor "A" se abra parcialmente y mostrar un mensaje de error adecuado. El mensaje de error debe indicar al usuario que cierre el archivo "b" en el editor incompatible y, a continuación, vuelva a abrir el archivo "a" utilizando el editor "A". También puede implementar [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> el método para solicitar al usuario que cierre el archivo "b" que está abierto en el editor incompatible. Si el usuario cierra el archivo "b", la apertura del archivo "a" en el editor "A" continúa normalmente.

## <a name="additional-document-edit-lock-considerations"></a>Consideraciones adicionales sobre el bloqueo de edición de documentos

Obtiene un comportamiento diferente si el editor "A" es el único editor que tiene un bloqueo de edición de documentos en el archivo "b" que si el editor "B" también tiene un bloqueo de edición de documento en el archivo "b". En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], el Diseñador de **clases** es un ejemplo de un diseñador visual que no contiene un bloqueo de edición en el archivo de código asociado. Es decir, si el usuario tiene un diagrama de clases abierto en la vista de diseño y el archivo de código asociado abierto simultáneamente, y si el usuario modifica el archivo de código pero no guarda los cambios, los cambios también se pierden en el archivo de diagrama de clases (.cd). Si el Diseñador de **clases** tiene el único bloqueo de edición de documento en el archivo de código, no se pide al usuario que guarde los cambios al cerrar el archivo de código. El IDE pide al usuario que guarde los cambios solo después de que el usuario cierre el **Diseñador de clases**. Los cambios guardados se reflejan en ambos archivos. Si tanto el Diseñador de **clases** como el editor de archivos de código mantuvieron bloqueos de edición de documentos en el archivo de código, se solicita al usuario que guarde al cerrar el archivo de código o el formulario. En ese momento, los cambios guardados se reflejan tanto en el formulario como en el archivo de código. Para obtener más información sobre los diagramas de clases, vea Trabajar con diagramas de [clases (Diseñador de clases).](../ide/class-designer/designing-and-viewing-classes-and-types.md)

Tenga en cuenta que si necesita colocar un bloqueo de edición <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> en un documento para un no editor, debe implementar la interfaz.

Muchas veces, un diseñador de interfaz de usuario que modifica los archivos de código mediante programación realiza cambios en más de un archivo. En tales <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> casos, el método controla el guardado de uno o más documentos mediante el cuadro de diálogo **¿Desea guardar los cambios en los siguientes elementos?.**

## <a name="see-also"></a>Vea también

- [Tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)
- [Persistencia y la tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)
