---
title: "C&#243;mo: registrar eventos del b&#250;fer de texto con la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - registrarse para eventos del búfer de texto"
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: registrar eventos del b&#250;fer de texto con la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tiene acceso al búfer de texto mediante heredado API, debe registrarse para los eventos del búfer de texto tal y como se muestra en el procedimiento siguiente.  
  
### Notificárselo eventos del búfer de texto  
  
1.  De un puntero a una de las interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, llame a `QueryInterface` para un puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Llame al método de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> , y pase el identificador de la interfaz de eventos para los que desea registrar.  
  
     Por ejemplo, si desea registrar para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, después pase un identificador de interfaz de IID\_IVsTextLinesEvents.  
  
     El búfer de texto devuelve un puntero a la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para el objeto correspondiente de punto de conexión.  
  
3.  Mediante este puntero, llame al método de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> , pasando un puntero a la implementación de la interfaz de eventos para la que desea registrar, por ejemplo, la interfaz de `IVsTextLinesEvents` .  
  
     El entorno devuelve una cookie que puede utilizar para detener el escuchar los eventos llamando al método de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> .  
  
## Vea también  
 [Eventos del búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)