---
title: Eventos de búfer de texto en la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186407"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventos de búfer de texto en la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El objeto de búfer de texto emite varios eventos diferentes que le permiten responder a distintas situaciones.  
  
 Cuando use la API heredada, debe implementar las siguientes interfaces para recibir una notificación de los cambios en el búfer de texto. Exponga las interfaces al búfer de texto utilizando la `IConnectionPointContainer` interfaz en el búfer de texto para recibir la notificación de cambios de línea del búfer. Para obtener más información, consulte [Cómo: registrar eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). En el caso de `IVsTextStreamEvents` las `IVsTextLinesEvents` interfaces o, los cambios se devuelven en coordenadas de una o dos dimensiones, respectivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de búfer de texto  
 A continuación se muestran las interfaces implementadas por el objeto de búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestas (es decir, acciones agrupadas en una sola unidad de deshacer/rehacer).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de los datos de documento administrados por el búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; lo usan muchos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona funciones de lectura y escritura que usan coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona acceso secuencial rápido y orientado a secuencias al texto del búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona capacidades de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre, o moniker, del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y su uso como clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para eventos.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces de eventos de búfer de texto  
 A continuación se muestran las interfaces para la notificación de eventos de búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica a los clientes el momento en que un nuevo servicio de lenguaje se asocia a un búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica a los clientes el momento en que se inicializa un búfer de texto y el momento en que se realizan cambios en los datos del búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica a los clientes los cambios realizados en el búfer de texto subyacente en coordenadas unidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica a los clientes los cambios realizados en el búfer de texto subyacente en coordenadas bidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica a los clientes los cambios realizados en los datos de usuario.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica a los clientes que el último gesto de confirmación va a desencadenar el evento y proporciona el intervalo de texto cambiado. La `IVsPreliminaryTextChangeCommitEvents` interfaz no se activa en respuesta a los comandos deshacer o rehacer. Los eventos solo se activan para los búferes que tienen un administrador de deshacer. `IVsPreliminaryTextChangeCommitEvents` se desencadena antes que otros eventos, como la lista descriptiva, para asegurarse de que los demás eventos no modifican el texto antes de que se confirmen los cambios. El VSPackage debe supervisar la `IVsPreliminaryTextChangeCommitEvents` interfaz o la `IVsFinalTextChangeCommitEvents` interfaz, pero no ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica a los clientes que el último gesto de confirmación va a desencadenar el evento y proporciona el intervalo de texto cambiado. La `IVsFinalTextChangeCommitEvents` interfaz no se activa en respuesta a los comandos deshacer o rehacer. Los eventos solo se activan para los búferes que tienen un administrador de deshacer. `IVsFinalTextChangeCommitEvents` está pensado para su uso únicamente por parte de servicios de lenguaje u otros objetos que tienen un control total sobre la edición. El VSPackage debe supervisar la `IVsPreliminaryTextChangeCommitEvents` interfaz o la `IVsFinalTextChangeCommitEvents` interfaz, pero no ambos.|  
  
## <a name="see-also"></a>Consulte también  
 [Acceso al búfer de texto mediante la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Cómo: Registrarse para eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
