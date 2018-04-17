---
title: Bloqueo titular de la administración de documentos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65f5a38f5d4da0986b7f95c9287a94e657efa9c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="document-lock-holder-management"></a>Administración de propietario de bloqueo de documento
La tabla de documento ejecutando (RDT) mantiene un recuento de los documentos abiertos y los bloqueos de edición tienen. Es posible colocar un bloqueo de edición en un documento en el RDT cuando se edita mediante programación en segundo plano sin que el usuario ve un documento abierto en una ventana de documento. Esta funcionalidad se utiliza a menudo los diseñadores que modifique varios archivos a través de una interfaz gráfica de usuario.  
  
## <a name="document-lock-holder-scenarios"></a>Escenarios de titular del bloqueo de documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Archivo de "a" una dependencia en el archivo tiene "b"  
 Considere la posibilidad de una situación donde se implementa un editor estándar "A" para el tipo de archivo "a" y cada archivo de tipo "a" tiene una referencia a (o dependencia de) un archivo de tipo "b". Existe un editor estándar "B" de archivos de tipo "b". Cuando abre el editor de "A" archivo "a", lo recupera la referencia al archivo correspondiente "b". No se muestra el archivo "b", pero puede modificarla editor "A". Editor de "A" obtiene una referencia a los datos del documento de archivo "b" de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método y también mantiene un bloqueo de edición en el archivo "b". Modificar el archivo "b" puede disminuir el bloqueo de edición contar una vez terminado editor "A" en el archivo "b" mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> método. Puede omitir este paso si se hubiera llamado el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método con el parámetro `dwRDTLockType` establecido en <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Se abre el archivo "b" por un Editor distinto  
 En caso de que ya se abre el archivo "b" editor "B" cuando intente abrirlo editor "A", hay dos escenarios diferentes para controlar:  
  
-   Si el archivo "b" se abre en un editor compatible, debe tener editor "A" registrar un bloqueo de edición de documento en el archivo "b" mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> método. Después de realiza modificación archivo "b" en el editor "A", anular el registro del documento editar bloqueo mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> método.  
  
-   Si el archivo "b" se abre de manera incompatible, se puede dejar que el intento apertura del archivo "b" Editor "A" por error, o puede dejar la vista asociada con el editor de "A" parcialmente abre y mostrar un mensaje de error adecuado. El mensaje de error debe indicar al usuario para cerrar el archivo "b" en el editor incompatible y, a continuación, vuelva a abrir el archivo "a" con "A en" el editor. También puede implementar la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> para solicitar al usuario al cerrar el archivo "b" que esté abierto en el editor incompatible. Si el usuario cierra el archivo "b", la apertura del archivo "a" editor en "A" continúa con normalidad.  
  
## <a name="additional-document-edit-lock-considerations"></a>Consideraciones de bloqueo de edición de documentos adicionales  
 Obtendrá un comportamiento diferente si editor "A" es el único editor que tiene un documento editar bloqueo en el archivo "b", que lo haría si editor "B" también contiene un documento edit bloqueo en el archivo "b". En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Diseñador de clases** es un ejemplo de un diseñador visual que no mantiene un bloqueo de edición en el archivo de código asociado. Es decir, si el usuario tiene un diagrama de clases abierto en la vista Diseño y el archivo de código asociado se abre al mismo tiempo, y si el usuario modifica el archivo de código, pero no guarda los cambios, los cambios también se pierde en el archivo de diagrama (CD) de la clase. Si el **Diseñador de clases** tiene el documento solo editar bloqueo en el archivo de código, se pregunta al usuario no desea guardar los cambios al cerrar el archivo de código. El IDE solicita al usuario que guarde los cambios solo después de que el usuario cierra el **Diseñador de clases**. Los cambios guardados se reflejan en ambos archivos. Si tanto la **Diseñador de clases** y el editor de archivos de código mantiene los bloqueos de edición de documentos en el archivo de código, a continuación, el usuario se pregunte si desea guardar al cerrar el archivo de código o en el formulario. En ese momento se reflejan los cambios guardados en el formulario y el archivo de código. Para obtener más información sobre los diagramas de clases, consulte [trabajar con diagramas de clases (Diseñador de clases)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Tenga en cuenta que si tiene que colocar un bloqueo de edición de un documento por un editor de no, debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaz.  
  
 Muchas veces un diseñador de la UI que modifica los archivos de código mediante programación realiza cambios en más de un archivo. En estos casos el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> método controla el almacenamiento de uno o más documentos por medio de la **¿desea guardar los cambios en los siguientes elementos?** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)   
 [Persistencia y tabla de documentos en ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)