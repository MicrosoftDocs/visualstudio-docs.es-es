---
title: "Objeto objeto VSTextView | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextView"
helpviewer_keywords: 
  - "Objeto objeto VSTextView, referencia"
  - "hacer referencia a vistas [Visual Studio SDK]"
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Objeto objeto VSTextView
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. Básicamente, la vista es lo que hacen referencia la mayoría de los usuarios como el editor. Dado que la vista se separa de búfer por varias capas de texto \(ajuste de línea, esquematización de texto etc.\), la vista no se garantiza que una representación exacta del texto en el búfer. Para obtener más información acerca de la vista de texto, consulte [Acceso a Text vista usando la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 En la tabla siguiente se muestra las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestas \(es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único\).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y tener acceso a la vista.`IVsTextView` no es subprocesos seguros.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con las capas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|  
  
## Vea también  
 [Figures Edit](http://msdn.microsoft.com/es-es/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objeto objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Acceso a Text vista usando la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)