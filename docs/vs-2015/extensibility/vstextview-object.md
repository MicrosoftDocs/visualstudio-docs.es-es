---
title: VSTextView (objeto) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690695"
---
# <a name="vstextview-object"></a>VSTextView (Objeto)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. Básicamente, la vista es lo que hacen referencia la mayoría de los usuarios como el editor. Dado que la vista está separada del búfer por diversas capas de texto (ajuste de palabra, esquematización de texto etc.), la vista no garantiza que sea una representación exacta del texto en el búfer. Para obtener más información acerca de la vista de texto, consulte [acceso a Text vista mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 En la tabla siguiente se muestra las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestas (es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y tener acceso a la vista. `IVsTextView` no es seguro para subprocesos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con las capas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|  
  
## <a name="see-also"></a>Vea también  
 [Edición de cifras](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer (objeto)](../extensibility/vstextbuffer-object.md)   
 [Acceso a la vista de texto mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
