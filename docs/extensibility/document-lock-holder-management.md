---
title: "Administraci&#243;n de propietario de bloqueo de documento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - bloqueo de documentos"
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Administraci&#243;n de propietario de bloqueo de documento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tabla en el documento \(RDT\) mantiene un recuento de documentos abiertos y cualquier edición los bloqueos tiene.  Puede colocar un bloqueo de edición en un documento del RDT cuando mediante programación se edita en segundo plano sin el usuario que ve un documento abierto en una ventana de documento.  Esta funcionalidad se suele utilizar por los diseñadores que modifican varios archivos a través de una interfaz gráfica de usuario.  
  
## Escenarios de marcador de bloqueo del documento  
  
### Archivo “a” que dependa del archivo “b”  
 Considere un escenario donde se implementa un editor estándar “A” para el tipo de archivo “a”, y cada archivo del tipo “a” tiene una referencia \(o dependencias con\) en un archivo de tipo “b”.  Un editor estándar “b” existe para los archivos de tipo “b”.  Cuando se abre el editor “A” archivo “a” recupera la referencia al archivo correspondiente “b”.  El archivo “b” no se muestra, pero el editor “A” puede modificarlo.  El editor “A” obtiene una referencia a los datos del documento del archivo “b” del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> y también mantiene un bloqueo de edición en el archivo “b”.  Después de que el editor “A” es archivo de modificación listo “b” puede disminuir el recuento de bloqueo de edición en el archivo “b” llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> .  Puede omitir este paso si hubiera llamado al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> con el parámetro `dwRDTLockType` establecido en <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### El archivo “b” está abierto en un editor diferente  
 En caso que el archivo “b” esté abierto en el editor “b” cuando el editor “A” intentar abrirlo, hay dos escenarios independientes administrar:  
  
-   Si el archivo “b” está abierto en un editor compatible, debe tener registro de editor “A” un bloqueo de edición del documento en el archivo “b” utilizando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> .  Después de que el editor “A” es archivo de modificación listo “b”, O.N.U\-registro el bloqueo de la edición del documento utilizando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> .  
  
-   Si el archivo “b” está abierto de una manera incompatible, puede o permite la apertura deseada del archivo “b” por errores de editor “A”, o puede dejar la vista asociado con el editor “A” parcialmente abrir y mostrar un mensaje de error adecuado.  El mensaje de error debe indicar al usuario para cerrar el archivo “b” en el editor incompatible y a continuación volver a abrir el archivo “a” utilizando el editor “A”.  También puede implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> del método de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] para solicitar al usuario cerrar el archivo “b” que está abierto en el editor incompatible.  Si el usuario cierra archivo “b”, apertura de archivos “a” en el editor “A” realizará normalmente.  
  
## Consideraciones adicionales sobre el bloqueo de la edición del documento  
 Se obtiene un comportamiento diferente si el editor “A” es el único editor que tiene un bloqueo de edición del documento en el archivo “b” que se si el editor “b” también tiene un bloqueo de edición del documento en el archivo “b”.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Diseñador de clases** es un ejemplo de un diseñador visual que no contiene un bloqueo de edición en el archivo de código asociado.  Es decir, si el usuario tiene un diagrama de clases abre en la vista de diseño y el archivo de código asociado abiertos simultáneamente y, si el usuario se modifica el archivo de código pero no guarda los cambios, los cambios también se pierden al archivo de diagrama de clases \(.cd\).  Si **Diseñador de clases** tiene el único bloqueo de edición del documento en el archivo de código, no se pide al usuario guardar los cambios al cerrar el archivo de código.  El IDE pide al usuario guardar los cambios una vez que el usuario cierra **Diseñador de clases**.  Los cambios guardados se reflejarán en ambos archivos.  Si **Diseñador de clases** y el editor del archivo de código contenían la edición del documento bloqueos en el archivo de código, después se pedirá al usuario guardar al cerrar el archivo de código o el formulario.  en ese momento los cambios guardados se reflejan en el formulario y el archivo de código.  Para obtener más información sobre los diagramas de clases, vea [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Observe que si necesita colocar un bloqueo de edición en el documento para un no\-editor, debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> .  
  
 Muchas veces un diseñador de la interfaz de usuario que modifica los archivos de código mediante programación realiza cambios en más de un archivo.  En estos casos el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> controla el guardar de uno o más documentos mediante el cuadro de diálogo de **¿Desea guardar los cambios en los elementos siguientes?** .  
  
## Vea también  
 [Tabla de documentos de ejecución](../extensibility/internals/running-document-table.md)   
 [Persistencia y la tabla Document de ejecución](../extensibility/internals/persistence-and-the-running-document-table.md)