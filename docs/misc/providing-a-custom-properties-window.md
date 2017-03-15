---
title: "Proporcionar una ventana de propiedades personalizadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exploradores de propiedades, proporcionar"
  - "ventana Propiedades, proporcionar una propia"
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Proporcionar una ventana de propiedades personalizadas
Es posible proporcionar su propia ventana de **Propiedades** para un sistema determinado del proyecto, en lugar de ampliar la ventana de **Propiedades** proporcionada por el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(IDE\).  El escenario encontró con mayor frecuencia es cuando el propio implementan el objeto se encuentra en el marco de la ventana.  
  
 En el evento no implementa el objeto situado en el marco de la ventana, pero todavía tiene acceso a por otros medios, hay varias maneras de tener acceso a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> enumerados en el último procedimiento en esta página.  
  
### Para proporcionar la ventana Propiedades  
  
1.  Defina un GUID que representa la implementación de la ventana de **Propiedades** .  
  
2.  En su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , use el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> para mostrar la ventana de **Propiedades** como servicio al entorno de Visual Studio.  
  
### Para llamar a la ventana propiedades  
  
1.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>.  
  
2.  `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pasado en el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
3.  Obtiene <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> .  
  
4.  Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> con el primer parámetro establecido en `SEID_PropertyBrowserSID` \(tomado de la enumeración de <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> \), y el tercer parámetro, `varValue`, que representa un formato de cadena del GUID que representa la ventana de **Propiedades** .  Hace que esta llamada solo una vez en la primera creación de la ventana de documento de la ventana de **Propiedades** .  Después de la llamada esta ventana de **Propiedades** es asociado al marco de la ventana.  
  
### Para obtener el objeto de la ventana cuando no es el implementador  
  
-   Puede `QueryService` para el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> con el parámetro `propid` establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
-   Puede obtener la ventana de documento activo llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> con el servicio de SVsMonitorSelection.  Establezca el parámetro `elementid` a `SEID_WindowFrame`, tomado de la enumeración de <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> .  
  
## Vea también  
 [Extender propiedades](../extensibility/internals/extending-properties.md)   
 [Interfaces y campos de la ventana de propiedades](../extensibility/internals/properties-window-fields-and-interfaces.md)