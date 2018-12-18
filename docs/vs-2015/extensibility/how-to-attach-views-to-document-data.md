---
title: 'Cómo: adjuntar las vistas de datos de documentos | Microsoft Docs'
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
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a872cf3ebfebf68c01256a0a8c42ebfcfeb02dd5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781548"
---
# <a name="how-to-attach-views-to-document-data"></a>Cómo: adjuntar las vistas de datos de documentos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si tiene una nueva vista de documento, puede asociarlo a un objeto de datos del documento existente.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar si una vista se puede asociar a un objeto de datos del documento existente  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  En la implementación de `IVsEditorFactory::CreateEditorInstance`, llame a `QueryInterface` en el objeto de datos de documento existente cuando el IDE llama a su `CreateEditorInstance` implementación.  
  
     Una llamada a `QueryInterface` permite examinar el objeto de datos de documento existente, que se especifica en el `punkDocDataExisting` parámetro.  
  
     Las interfaces exactas que debe consultar, sin embargo, depende del editor que se está abriendo el documento, tal como se describe en el paso 4.  
  
3.  Si no encuentra las interfaces adecuadas en el objeto de datos existente, a continuación, devolver un código de error en el editor que indica que el objeto de datos es incompatible con su editor.  
  
     En la implementación del IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, un cuadro de mensaje le notifica que el documento está abierto en otro editor y le pregunta si desea cerrarlo.  
  
4.  Si cierra este documento, Visual Studio llama el generador de editores por segunda vez. En esta llamada, el `DocDataExisting` parámetro es igual a NULL. Su implementación del generador de editor, a continuación, puede abrir el objeto de datos en su propio editor.  
  
    > [!NOTE]
    >  Para determinar si puede trabajar con un objeto de datos del documento existente, también puede usar el conocimiento privado de la implementación de interfaz al convertir un puntero a los datos reales [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] clase de la implementación privada. Por ejemplo, se implementan todos los editores estándares `IVsPersistFileFormat`, que hereda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Por lo tanto, puede llamar a `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, y si el identificador de clase en el objeto de datos del documento existente coincide con la implementación de Id. de clase y, después, puede trabajar con el objeto de datos.  
  
## <a name="robust-programming"></a>Programación sólida  
 Cuando Visual Studio llama a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, pasa atrás un puntero para el objeto de datos existente en el `punkDocDataExisting` parámetro, si existe alguno. Examinar el objeto de datos de documento devuelto en `punkDocDataExisting` para determinar si el objeto de datos es adecuado para el editor, tal como se describe en la nota en el paso 4 del procedimiento de este tema. Si es adecuado y, después, el generador de editores debe proporcionar una segunda vista para los datos tal como se describe en [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md). Si no es así, a continuación, debe mostrar un mensaje de error adecuado.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con varias vistas de documento](../extensibility/supporting-multiple-document-views.md)   
 [Datos de documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)

