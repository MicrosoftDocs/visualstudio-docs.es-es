---
title: 'Cómo: registrar los eventos de búfer de texto con la API heredada | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e895f2d67c23454ad3f7481e558f6dde542867b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782783"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Cómo: registrar los eventos de búfer de texto con la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si tiene acceso al búfer de texto mediante el uso de la API heredada, debe registrar para eventos del búfer de texto tal como se muestra en el siguiente procedimiento.  
  
### <a name="to-advise-text-buffer-events"></a>Para avisar a los eventos del búfer de texto  
  
1.  De un puntero a una de las interfaces en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, llame a `QueryInterface` para un puntero a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> método y pase el identificador de interfaz de los eventos para el que desea registrar.  
  
     Por ejemplo, si desea registrar para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, a continuación, pasar una interfaz Id. de IID_IVsTextLinesEvents.  
  
     El búfer de texto devuelve un puntero a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz para el objeto de punto de conexión adecuado.  
  
3.  Con este puntero, llame a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> método, pasando un puntero a la implementación de la interfaz de eventos para el que desea registrar, por ejemplo, el `IVsTextLinesEvents` interfaz.  
  
     El entorno devuelve una cookie que, a continuación, puede usar para dejar de escuchar a los eventos mediante una llamada a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> método.  
  
## <a name="see-also"></a>Vea también  
 [Eventos de búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)

