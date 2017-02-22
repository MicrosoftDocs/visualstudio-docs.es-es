---
title: "C&#243;mo: adjuntar vistas de datos de documentos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - adjuntar vistas a los datos de documentos"
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: adjuntar vistas de datos de documentos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tiene una nueva vista de documento, puede adjuntar a un objeto de datos de documento existente.  
  
### Para determinar si se puede asociar una vista a un objeto de datos de documento existente  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  En la implementación de `IVsEditorFactory::CreateEditorInstance`, llame a `QueryInterface` en el objeto de datos de documento existente cuando el IDE se llama su `CreateEditorInstance` implementación.  
  
     Llamar a `QueryInterface` le permite examinar el objeto de datos de documentos existentes, que se especifica en el `punkDocDataExisting` parámetro.  
  
     Las interfaces exactas que se debe consultar, depende del editor que se está abriendo el documento, sin embargo, tal como se describe en el paso 4.  
  
3.  Si no encuentra las interfaces adecuadas en el objeto de datos de documento existente, a continuación, devolver un código de error al editor que indica que el objeto de datos de documento es incompatible con su editor.  
  
     En la implementación del IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, un cuadro de mensaje le notifica que el documento está abierto en otro editor y le pregunta si desea cerrar.  
  
4.  Si cierra este documento, Visual Studio llama el generador de editores por segunda vez. En esta llamada, el `DocDataExisting` parámetro es igual a NULL. Su implementación del generador de editor, a continuación, puede abrir el objeto de datos del documento en su propio editor.  
  
    > [!NOTE]
    >  Para determinar si puede trabajar con un objeto de datos de documento existente, también puede utilizar información privada de la implementación de interfaz al convertir un puntero a los datos reales [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] clase de la implementación privada. Por ejemplo, implementan todos los editores estándares `IVsPersistFileFormat`, que hereda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Por lo tanto, puede llamar a `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, y si el identificador de clase en el objeto de datos de documento existente coincide con la implementación de Id. de clase, a continuación, puede trabajar con el objeto de datos del documento.  
  
## Programación eficaz  
 Cuando Visual Studio llama a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método pasa atrás un puntero al objeto de datos de documento existente en el `punkDocDataExisting` parámetro, si existe alguno. Examinar el objeto de datos de documentos devuelto en `punkDocDataExisting` para determinar si el objeto de datos del documento es adecuado para el editor, como se describe en la nota en el paso 4 del procedimiento de este tema. Si es adecuado, el generador del editor debe proporcionar una segunda vista para los datos como se describe en [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md). Si no es así, a continuación, debe mostrar un mensaje de error adecuado.  
  
## Vea también  
 [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md)   
 [Datos del documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)