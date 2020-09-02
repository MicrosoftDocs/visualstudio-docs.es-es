---
title: 'Cómo: registrar eventos de búfer de texto con la API heredada | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204088"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Cómo: Registrarse para eventos de búfer de texto con la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si tiene acceso al búfer de texto mediante la API heredada, debe registrarse para los eventos de búfer de texto, tal y como se muestra en el procedimiento siguiente.  
  
### <a name="to-advise-text-buffer-events"></a>Para notificar eventos de búfer de texto  
  
1. Desde un puntero a una de las interfaces en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , llame a `QueryInterface` para obtener un puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Llame al <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> método y pase el identificador de interfaz de los eventos que desea registrar.  
  
     Por ejemplo, si desea registrarse para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , pase un identificador de interfaz de IID_IVsTextLinesEvents.  
  
     El búfer de texto devuelve un puntero a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz para el objeto de punto de conexión adecuado.  
  
3. Con este puntero, llame al <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> método, pasando un puntero a la implementación de la interfaz de eventos para la que desea registrar, por ejemplo, la `IVsTextLinesEvents` interfaz.  
  
     El entorno devuelve una cookie que se puede usar para dejar de escuchar eventos llamando al <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> método.  
  
## <a name="see-also"></a>Consulte también  
 [Eventos de búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)
