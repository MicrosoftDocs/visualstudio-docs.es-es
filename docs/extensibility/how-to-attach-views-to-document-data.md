---
title: "Cómo: adjuntar vistas para datos de documentos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bcbb3e6b475a9dcd22d012073d3197013da337c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-views-to-document-data"></a>Cómo: adjuntar vistas para datos de documentos
Si tiene una nueva vista de documento, es posible que pueda conectar a un objeto de datos del documento existente.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar si se puede asociar una vista a un objeto de datos del documento existente  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  En la implementación de `IVsEditorFactory::CreateEditorInstance`, llame a `QueryInterface` en el objeto de datos de documento existente cuando el IDE llama su `CreateEditorInstance` implementación.  
  
     Al llamar a `QueryInterface` permite examinar el objeto de datos de documentos existentes, que se especifica en el `punkDocDataExisting` parámetro.  
  
     Las interfaces exactas que debe consultar, sin embargo, depende del editor que se abre el documento, tal como se describe en el paso 4.  
  
3.  Si no encuentra las interfaces adecuadas en el objeto de datos del documento existente, a continuación, devolver un código de error en el editor que indica que el objeto de datos de documento es incompatible con su editor.  
  
     En la implementación del IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, un cuadro de mensaje le notifica que el documento esté abierto en otro editor y le pregunta si desea cerrarlo.  
  
4.  Si cierra este documento, Visual Studio llama el generador de editores por segunda vez. En esta llamada, el `DocDataExisting` parámetro es igual a NULL. Su implementación del generador de editor, a continuación, puede abrir el objeto de datos del documento en su propio editor.  
  
    > [!NOTE]
    >  Para determinar si puede trabajar con un objeto de datos del documento existente, también puede utilizar información privada de la implementación de interfaz al convertir un puntero a los datos reales [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] clase de la implementación privada. Por ejemplo, se implementan todos los editores estándares `IVsPersistFileFormat`, que hereda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Por lo tanto, puede llamar a `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, y si el identificador de clase en el objeto de datos del documento existente coincide con la implementación de Id. de clase, a continuación, puede trabajar con el objeto de datos del documento.  
  
## <a name="robust-programming"></a>Programación sólida  
 Cuando Visual Studio llama a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, pasa volver un puntero al objeto de datos del documento existente en el `punkDocDataExisting` parámetro, si existe uno. Examinar el objeto de datos de documento devuelto en `punkDocDataExisting` para determinar si el objeto de datos de documento es adecuado para el editor tal como se describe en la nota en el paso 4 del procedimiento en este tema. Si es adecuado, el generador de editores debe proporcionar una segunda vista para los datos tal como se describe en [admitir varias vistas de documento](../extensibility/supporting-multiple-document-views.md). De lo contrario, a continuación, debe mostrar un mensaje de error adecuado.  
  
## <a name="see-also"></a>Vea también  
 [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md)   
 [Datos de documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)