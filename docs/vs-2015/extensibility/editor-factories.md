---
title: Generadores de editores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197766"
---
# <a name="editor-factories"></a>Generadores del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un generador de editores crea objetos de editor y los coloca en un marco de ventana, conocido como vista física. Crea los datos de documento y los objetos de vista de documento necesarios para crear editores y diseñadores. Se requiere un generador de editores para crear el editor principal de Visual Studio y cualquier editor estándar. Opcionalmente, también se puede crear un editor personalizado con un generador de editores.  
  
 Puede crear un generador de editores implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz. En el ejemplo siguiente se muestra cómo implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> para crear un generador de editores:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Se carga un editor la primera vez que se abre un tipo de archivo administrado por ese editor. Puede optar por abrir un editor específico o el editor predeterminado. Si selecciona el editor predeterminado, el entorno de desarrollo integrado (IDE) determina el editor correcto para abrirlo y, a continuación, lo abre. Para obtener más información, vea [determinar qué editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registro de generadores de editores  
 Antes de poder usar un editor que haya creado, primero debe registrar información, incluidas las extensiones de archivo que puede administrar.  
  
 Si el VSPackage está escrito en código administrado, puede usar el método de Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para registrar el generador de editores una vez cargado el VSPackage. Si el VSPackage está escrito en código no administrado, debe registrar el generador de editores mediante el <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> servicio.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrar un generador de editores mediante código administrado  
 Debe registrar el generador de editores en el método del VSPackage `Initialize` . Primera llamada `base.Initialize` y, a continuación, llame a <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> para cada generador de editores  
  
 En código administrado, no es necesario anular el registro de un generador de editores, ya que el VSPackage lo controlará automáticamente. Además, si el generador de editores implementa <xref:System.IDisposable> , se elimina automáticamente cuando se anula el registro.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrar un generador de editores mediante código no administrado  
 En la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación del paquete del editor, use el `QueryService` método para llamar a `SVsRegisterEditors` . Si lo hace, se devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método pasando su implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz. Debe mplementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> en una clase independiente.  
  
## <a name="the-editor-factory-registration-process"></a>El proceso de registro del generador de editores  
 El siguiente proceso se produce cuando Visual Studio carga el editor mediante el generador de editores:  
  
1. El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistema del proyecto llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Este método devuelve el generador de editores. Sin embargo, Visual Studio retrasa la carga del paquete del editor hasta que un sistema del proyecto realmente necesita el editor.  
  
3. Cuando un sistema de proyectos necesita el editor, Visual Studio llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , un método especializado que devuelve tanto la vista de documento como los objetos de datos de documento.  
  
4. Si las llamadas de Visual Studio al generador de editores mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> devuelven un objeto de datos de documento y un objeto de vista de documento, Visual Studio crea la ventana de documento, coloca el objeto de vista de documento en ella y crea una entrada en la tabla de documentos en ejecución (RDT) para el objeto de datos de documento.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabla de documentos en ejecución](../extensibility/internals/running-document-table.md)
