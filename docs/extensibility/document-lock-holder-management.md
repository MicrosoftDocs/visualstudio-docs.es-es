---
title: Administración de titulares de bloqueo de documentos | Microsoft Docs
description: Obtenga información acerca de cómo colocar un bloqueo de edición en un documento en la tabla de documentos en ejecución sin que el usuario vea un documento abierto en una ventana de documento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88e66ed3b0a5434f4d875bf941e3eeffb8adc092
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091193"
---
# <a name="document-lock-holder-management"></a>Administración de titulares de bloqueo de documentos

La tabla de documentos en ejecución (RDT) mantiene un recuento de documentos abiertos y cualquier bloqueo de edición que tengan. Puede colocar un bloqueo de edición en un documento de RDT cuando se edita mediante programación en segundo plano sin que el usuario vea un documento abierto en una ventana de documento. Esta funcionalidad suele ser utilizada por los diseñadores que modifican varios archivos a través de una interfaz gráfica de usuario.

## <a name="document-lock-holder-scenarios"></a>Escenarios de marcador de bloqueo de documento

### <a name="file-a-has-a-dependence-on-file-b"></a>El archivo "a" tiene una dependencia del archivo "b"

Considere una situación en la que implementa un editor estándar "A" para el tipo de archivo "a", y cada archivo de tipo "a" tiene una referencia a (o a la dependencia de) un archivo de tipo "b". Existe un editor estándar "B" para los archivos de tipo "b". Cuando el editor "A" abre el archivo "a", recupera la referencia al archivo "b" correspondiente. No se muestra el archivo "b", pero el editor "A" puede modificarlo. El editor "A" obtiene una referencia a los datos de documento del archivo "b" del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método y también mantiene un bloqueo de edición en el archivo "b". Después de que el editor "A" termine de modificar el archivo "b", puede reducir el recuento de bloqueos de edición en el archivo "b" llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método. Puede omitir este paso si ha llamado al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método con el parámetro `dwRDTLockType` establecido en [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Un editor diferente abre el archivo "b"

En caso de que el archivo "b" ya esté abierto por el editor "B" cuando el editor "A" intente abrirlo, hay dos escenarios independientes para controlar:

- Si el archivo "b" está abierto en un editor compatible, debe hacer que el editor "A" registre un bloqueo de edición de documento en el archivo "b" mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método. Después de que el editor "A" termine de modificar el archivo "b", elimine del registro el bloqueo de edición del documento mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> método.

- Si el archivo "b" está abierto de forma no compatible, puede dejar que se produzca un error al intentar abrir el archivo "b" por el editor "A", o bien puede dejar que la vista asociada al editor "A" se abra parcialmente y muestre un mensaje de error adecuado. El mensaje de error debe indicar al usuario que cierre el archivo "b" en el editor incompatible y, a continuación, vuelva a abrir el archivo "a" mediante el editor "A". También puede implementar el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> para solicitar al usuario que cierre el archivo "b" que está abierto en el editor incompatible. Si el usuario cierra el archivo "b", la apertura del archivo "a" en el editor "A" continúa con normalidad.

## <a name="additional-document-edit-lock-considerations"></a>Consideraciones adicionales sobre el bloqueo de edición de documentos

Obtiene un comportamiento diferente si el editor "A" es el único editor que tiene un bloqueo de edición de documento en el archivo "b" que si el editor "B" también contuviera un bloqueo de edición de documento en el archivo "b". En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , **Diseñador de clases** es un ejemplo de un diseñador visual que no contiene un bloqueo de edición en el archivo de código asociado. Es decir, si el usuario tiene un diagrama de clases abierto en la vista Diseño y el archivo de código asociado se abre simultáneamente, y si el usuario modifica el archivo de código pero no guarda los cambios, los cambios también se pierden en el archivo de diagrama de clases (. CD). Si el **Diseñador de clases** tiene el único bloqueo de edición del documento en el archivo de código, no se pide al usuario que guarde los cambios al cerrar el archivo de código. El IDE pide al usuario que guarde los cambios solo después de que el usuario cierre el **Diseñador de clases**. Los cambios guardados se reflejan en ambos archivos. Si tanto el **Diseñador de clases** como el editor de archivos de código mantenían bloqueos de edición de documentos en el archivo de código, se solicitará al usuario que lo guarde al cerrar el archivo de código o el formulario. En ese momento, los cambios guardados se reflejan en el formulario y en el archivo de código. Para obtener más información sobre los diagramas de clases, vea [trabajar con diagramas de clases (diseñador de clases)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Tenga en cuenta que si necesita colocar un bloqueo de edición en un documento para un editor que no sea de, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz.

Muchas veces un diseñador de la interfaz de usuario que modifica los archivos de código mediante programación realiza cambios en más de un archivo. En tales casos, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> método controla el almacenamiento de uno o más documentos por medio del cuadro de diálogo **¿desea guardar los cambios en los elementos siguientes?** .

## <a name="see-also"></a>Consulte también

- [Tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)
- [Persistencia y la tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)
