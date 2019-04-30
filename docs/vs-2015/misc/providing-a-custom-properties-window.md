---
title: Proporcionar una ventana de propiedades personalizadas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810712"
---
# <a name="providing-a-custom-properties-window"></a>Proporcionar una ventana de propiedades personalizadas
Es posible proporcionar su propia **propiedades** ventana para un sistema de proyecto dada, en lugar de ampliación del **propiedades** ventana proporcionada por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE). El escenario se ha encontrado con mayor frecuencia es cuando usted implementa el objeto situado en el marco de ventana.  
  
 En caso de que no implementan el objeto situado en el marco de ventana, pero todavía se tiene acceso a él por otros medios, hay varias maneras de obtener acceso a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz como se muestra en el último procedimiento en esta página.  
  
### <a name="to-provide-your-properties-window"></a>Para proporcionar la ventana Propiedades  
  
1. Definir un GUID que representa su **propiedades** implementación de la ventana.  
  
2. En su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación, use el <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> servicio ofrecer su **propiedades** ventana como un servicio en el entorno de Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Para llamar a la ventana Propiedades  
  
1. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>.  
  
2. `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> desde el <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pasó el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> método.  
  
3. Obtener <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> desde <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service.  
  
4. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> con el primer parámetro establecido en `SEID_PropertyBrowserSID` (procedente del <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumeración) y el tercer parámetro, `varValue`, que representa una forma de cadena del GUID que representa su **propiedades** ventana. Hacer esta llamada solo una vez en la primera creación de su **propiedades** ventana de documento. Después de la llamada esto **propiedades** ventana está asociada con el marco de ventana.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Para obtener el objeto de marco de ventana cuando no se encuentra el implementador  
  
- También puede `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> con el parámetro `propid` establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
- Puede obtener la ventana de documento activo mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> a través del servicio SVsMonitorSelection. Establezca el parámetro `elementid` a `SEID_WindowFrame`, tomada de la <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumeración.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de extensión](../extensibility/internals/extending-properties.md)   
 [Interfaces y campos de la ventana Propiedades](../extensibility/internals/properties-window-fields-and-interfaces.md)