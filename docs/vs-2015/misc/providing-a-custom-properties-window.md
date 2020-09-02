---
title: Proporcionar una ventana Propiedades personalizadas | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810712"
---
# <a name="providing-a-custom-properties-window"></a>Proporcionar una ventana de propiedades personalizadas
Es posible proporcionar su propia ventana **propiedades** para un sistema de proyectos determinado, en lugar de extender la ventana **propiedades** que proporciona el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE). El escenario más frecuente es cuando se implementa el objeto que se encuentra en el marco de la ventana.  
  
 En el caso de que no implemente el objeto que se encuentra en el marco de la ventana, pero que todavía tenga acceso a él por otros medios, hay varias formas de obtener acceso a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz como se muestra en el último procedimiento de esta página.  
  
### <a name="to-provide-your-properties-window"></a>Para proporcionar el ventana Propiedades  
  
1. Defina un GUID que represente la implementación de la ventana **propiedades** .  
  
2. En la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación, use el <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> servicio para ofrecer la ventana **propiedades** como servicio en el entorno de Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Para llamar a la ventana Propiedades  
  
1. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
2. `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> desde que <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> se pasa al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> método.  
  
3. Obtener <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> del <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servicio.  
  
4. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> con el primer parámetro establecido en `SEID_PropertyBrowserSID` (tomado de la <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumeración) y el tercer parámetro, `varValue` , que representa una forma de cadena del GUID que representa la ventana de **propiedades** . Realice esta llamada solo una vez en la primera creación de la ventana de documento de la ventana de **propiedades** . Después de la llamada, esta ventana de **propiedades** se asocia con el marco de la ventana.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Para obtener el objeto de marco de ventana cuando no es el implementador  
  
- Puede `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> con el parámetro `propid` establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Puede obtener la ventana de documento activa mediante una llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> a través del servicio SVsMonitorSelection. Establezca el parámetro `elementid` en `SEID_WindowFrame` , tomado de la <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumeración.  
  
## <a name="see-also"></a>Consulte también  
 [Extender propiedades](../extensibility/internals/extending-properties.md)   
 [Interfaces y campos de la ventana Propiedades](../extensibility/internals/properties-window-fields-and-interfaces.md)