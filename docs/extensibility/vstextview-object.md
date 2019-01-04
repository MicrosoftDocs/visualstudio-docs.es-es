---
title: VSTextView (objeto) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac87435175b0959e371af24438926f838971d02
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866275"
---
# <a name="vstextview-object"></a>VSTextView (objeto)
La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. Básicamente, la vista es lo que hacen referencia la mayoría de los usuarios como el editor. Dado que la vista está separada del búfer por diversas capas de texto (ajuste de palabra, esquematización de texto etc.), la vista no garantiza que sea una representación exacta del texto en el búfer. Para obtener más información acerca de la vista de texto, consulte [acceso a Text vista mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 En la tabla siguiente se muestra las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestas (es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y tener acceso a la vista. `IVsTextView` no se subproceso seguro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con las capas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|  
  
## <a name="see-also"></a>Vea también  
 [Edición de cifras](https://www.microsoft.com/download/details.aspx?id=55984)   
 [VSTextBuffer (objeto)](../extensibility/vstextbuffer-object.md)   
 [Acceso a la vista Text mediante el uso de la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)