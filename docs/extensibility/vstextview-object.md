---
title: Objeto del objeto VSTextView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f169c3302b3e6fd72e5017193e34836ed3e5340e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vstextview-object"></a>Objeto del objeto VSTextView
La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. En esencia, la vista es lo que hacen referencia mayoría de los usuarios como el editor. Dado que la vista se separa de búfer por varias capas de texto (ajuste de línea, esquematización de texto etc.), la vista no se garantiza que una representación exacta del texto en el búfer. Para obtener más información acerca de la vista de texto, consulte [obtener acceso a Text vista mediante la API heredado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 En la tabla siguiente se muestra las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestas (es decir, las acciones que se agrupan en una unidad de deshacer/rehacer único).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y tener acceso a la vista. `IVsTextView`no es subproceso seguro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con las capas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|  
  
## <a name="see-also"></a>Vea también  
 [Edición de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objeto del objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Obtener acceso a Text vista mediante la API heredado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)