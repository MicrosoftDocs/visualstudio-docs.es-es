---
title: "Cómo: registrar eventos de búfer de texto con la API heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fabdf30480666ee3bc24bf3d68af4cc0dcc1ccb6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Cómo: registrar eventos de búfer de texto con la API de heredado de
Si el búfer de texto que tiene acceso mediante el uso de la API heredada, se debe registrar para eventos de búfer de texto como se muestra en el siguiente procedimiento.  
  
### <a name="to-advise-text-buffer-events"></a>Para indicar que los eventos de búfer de texto  
  
1.  De un puntero a una de las interfaces en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, llame a `QueryInterface` para un puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> método y pase el identificador de interfaz de eventos para el que desea registrar.  
  
     Por ejemplo, si desea registrar para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, a continuación, pasar una interfaz Id. de IID_IVsTextLinesEvents.  
  
     El búfer de texto devuelve un puntero a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz para el objeto de punto de conexión adecuada.  
  
3.  Con este puntero, llame a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> método, pasando un puntero a la implementación de la interfaz de eventos para el que desea registrar, por ejemplo, el `IVsTextLinesEvents` interfaz.  
  
     El entorno devuelve una cookie que, a continuación, puede usar para dejar de escuchar a los eventos mediante una llamada a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> método.  
  
## <a name="see-also"></a>Vea también  
 [Eventos de búfer de texto de la API heredado](../extensibility/text-buffer-events-in-the-legacy-api.md)