---
title: "Generadores de editores | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - generadores de editores"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Generadores de editores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un generador del editor crea objetos editor y los coloca en un marco de ventana, conocido como vista física.  Crea los objetos de datos y de vista de documentos de documento que son necesarios para crear editores y diseñadores.  Un generador del editor se requiere crear el editor básico de Visual Studio y cualquier editor estándar.  Un editor personalizado se pueden crear opcionalmente con un generador del editor.  
  
 Crea un generador del editor implementando la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  El ejemplo siguiente se muestra cómo implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> para crear un generador del editor:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Un editor se carga la primera vez que abra un tipo de archivo controlado por el editor.  Puede elegir para abrir un editor específico o el editor predeterminado.  Si selecciona el editor predeterminado, el entorno de desarrollo \(IDE\) integrado \(IDE\) determina el editor correcto para abrir y lo abre.  Para obtener más información, vea [Determinar qué Editor se abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## Registrar generadores de editor  
 Antes de poder utilizar un editor que ha creado, primero debe registrar información sobre él, incluidas las extensiones de archivo que puede controlar.  
  
 Si el Paquete está escrita en código administrado, puede utilizar el método administrado <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> \(MPF\) de paquete para registrar el generador de editor después de que el Paquete se carga.  Si el Paquete está escrita en código no administrado, debe registrar el generador del editor mediante el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> .  
  
### Registrar un generador del editor utilizando código administrado  
 Debe registrar el generador del editor en el método de `Initialize` de VSPackage.  La primera llamada `base.Initialize`, y después llama a <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para cada generador del editor  
  
 En código administrado, no hay ningún registro de necesidad al generador del editor, porque el paquete VSPackage administrará esto.  Además, si el generador del editor implementa <xref:System.IDisposable>, automáticamente se elimina cuando no está registrado.  
  
### Registrar un generador del editor utilizando código no administrado  
 En la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> para el paquete de editor, utilice el método de `QueryService` para llamar a `SVsRegisterEditors`.  Esto devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> pasando la implementación de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  Debe mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> en una clase independiente.  
  
## El proceso de registro del generador del editor  
 El proceso siguiente aparece cuando Visual Studio carga el editor mediante el generador del editor:  
  
1.  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>del sistema de proyectos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
2.  Este método devuelve el generador del editor.  Visual Studio retrasa la carga del paquete de editor, sin embargo, hasta un sistema de proyecto necesita realmente el editor.  
  
3.  Cuando un sistema de proyecto necesita el editor, Visual Studio llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, un método especializado que devuelve la vista del documento y los objetos del documento.  
  
4.  Si las llamadas por Visual Studio al generador del editor mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> devuelven un objeto del documento y un objeto de vista del documento, Visual Studio creará la ventana de documento, coloca el objeto de vista del documento en él, y crea una entrada en la tabla en el \(RDT\) documento para el objeto del documento.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabla de documentos de ejecución](../extensibility/internals/running-document-table.md)