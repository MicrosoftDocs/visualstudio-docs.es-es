---
title: Generadores de editores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 998aae3efed362e07c07ae1933f2a6858b4f54b5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887363"
---
# <a name="editor-factories"></a>Generadores de editores
Un generador de editores crea objetos de editor y los coloca en un marco de ventana que se conoce como una vista física. Crea los datos del documento y los objetos de vista de documento que son necesarios para crear editores y diseñadores. Un generador de editores debe crear el editor de núcleo de Visual Studio y en cualquier editor estándar. Opcionalmente, también se puede crear un editor personalizado con un generador de editores.  
  
 Crear un generador de editores implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz. El ejemplo siguiente muestra cómo implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> para crear un generador de editores:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Un editor se carga la primera vez que abre un tipo de archivo controlado por ese editor. Puede abrir un editor específico o el editor predeterminado. Si selecciona el editor predeterminado, el entorno de desarrollo integrado (IDE) determina el editor correcto para abrir y, a continuación, lo abre. Para obtener más información, consulte [determinar qué editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="register-editor-factories"></a>Registrar generadores de editores  
 Para poder usar un editor que haya creado, primero debe registrar información sobre ella, incluidas las extensiones de archivo que puede controlar.  
  
 Si el paquete de VS está escrito en código administrado, puede usar el método de Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para registrar el generador de editores después de carga el VSPackage. Si el paquete de VS está escrito en código no administrado, debe registrar el generador de editores mediante el <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> service.  
  
### <a name="register-an-editor-factory-by-using-managed-code"></a>Registrar un generador de editores mediante código administrado  
 El generador de editores debe registrar en el VSPackage el `Initialize` método. Llamar primero a `base.Initialize`y, a continuación, llame a <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para cada generador de editores  
  
 En código administrado, no hay ninguna necesidad de anular el registro de un generador de editores, porque el VSPackage controlará esto por usted. Además, si implementa el generador de editores <xref:System.IDisposable>, se elimina automáticamente cuando no está registrado.  
  
### <a name="register-an-editor-factory-by-using-unmanaged-code"></a>Registrar un generador de editores con código no administrado  
 En el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación para el paquete del editor, use el `QueryService` método para llamar a `SVsRegisterEditors`. Esto devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método pasando la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz. Debe Faces <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> en una clase independiente.  
  
## <a name="the-editor-factory-registration-process"></a>El proceso de registro del generador de editor  
 El siguiente proceso se produce cuando el editor mediante el generador de editores de carga de Visual Studio:  
  
1. El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llamadas del sistema del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2. Este método devuelve el generador de editores. Retrasos visuales Studio carga el paquete del editor, sin embargo, hasta que un sistema de proyectos realmente necesita el editor.  
  
3. Cuando un sistema de proyectos, necesita el editor, Visual Studio llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, un método especializado que devuelve los objetos de datos de la vista del documento y el documento.  
  
4. Si llama a Visual Studio en el generador de editor con <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> devuelve un objeto de datos de documento y un objeto de vista de documento, Visual Studio, a continuación, crea la ventana de documento, coloca el objeto de vista de documento en él y realiza una entrada en el documento en ejecución tabla (RDT) para el objeto de datos.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)