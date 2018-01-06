---
title: Generadores de editores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e0fb464d3eb9d7b39b853593c9458fe800296321
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="editor-factories"></a>Generadores de editores
Un generador de editores crea objetos de editor y los coloca en un marco de ventana, que se conoce como una vista física. Crea los datos del documento y los objetos de vista de documentos que son necesarios para crear editores y diseñadores. Se requiere un generador del editor para crear el editor de Visual Studio core y cualquier editor estándar. Opcionalmente, también puede crearse un editor personalizado con un generador de editores.  
  
 Crear un generador de editores implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz. En el ejemplo siguiente se muestra cómo implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> para crear un generador del editor:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Un editor se carga la primera vez que abre un tipo de archivo controlado por ese editor. Puede abrir un editor determinado o el editor predeterminado. Si selecciona el editor predeterminado, el entorno de desarrollo integrado (IDE) determina el editor correcto para abrir y, a continuación, lo abre. Para obtener más información, consulte [determinar qué Editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrar generadores de editores  
 Para poder usar un editor que ha creado, primero debe registrar información sobre él, incluidas las extensiones de archivo que puede controlar.  
  
 Si el paquete de VS está escrita en código administrado, puede utilizar el método de Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para registrar el generador de editores después de carga el paquete de VS. Si se escribe el VSPackage en código no administrado, debe registrar el generador del editor mediante el <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> service.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>El registro de un generador del Editor mediante código administrado  
 Debe registrar el generador del editor en el VSPackage la `Initialize` método. Llamar primero a `base.Initialize`y, a continuación, llame a <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para cada generador de editores  
  
 En código administrado, no hay ninguna necesidad de anular el registro de un generador de editores, porque el VSPackage controlan esto por usted. Además, si implementa el generador de editores <xref:System.IDisposable>, se elimina automáticamente cuando se anula el registro.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>El registro de un generador del editor mediante código no administrado  
 En el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación para el paquete de editor, use la `QueryService` método para llamar a `SVsRegisterEditors`. Esto devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método pasando la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz. Debe mplementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> en una clase independiente.  
  
## <a name="the-editor-factory-registration-process"></a>El proceso de registro de fábrica de Editor  
 El siguiente proceso se produce cuando el editor con el generador de editores de carga de Visual Studio:  
  
1.  El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llamadas al sistema del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Este método devuelve el generador de editores. Retrasos visuales Studio cargar el paquete del editor, sin embargo, hasta que un sistema de proyecto necesita realmente el editor.  
  
3.  Cuando un sistema de proyecto necesita el editor, Visual Studio llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, un método especializado que devuelve los objetos de datos de la vista de documento y el documento.  
  
4.  Si llama a Visual Studio al editor generador mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> devolver un objeto de datos de documento y un objeto de vista de documento, Visual Studio, a continuación, crea la ventana de documento, coloca el objeto de vista de documento en él y crea una entrada en el documento de ejecución tabla (RDT) para el objeto de datos del documento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)