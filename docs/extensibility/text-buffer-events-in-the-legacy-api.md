---
title: Eventos de búfer de texto de la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f147171d8af075029a4a763a84fd48c5209f8fe1
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080613"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventos del búfer de texto en la API heredada
El objeto de búfer de texto emite varios eventos distintos que le permiten dar respuesta a situaciones diferentes.  
  
 Cuando se usa la API heredada, debe implementar las interfaces siguientes con el fin de recibir una notificación de cambios en el búfer de texto. Expone las interfaces para el búfer de texto mediante el `IConnectionPointContainer` cambia de interfaz en el búfer de texto para recibir una notificación de línea del búfer. Para obtener más información, consulte [Cómo: registrar los eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). En el caso de `IVsTextStreamEvents` o `IVsTextLinesEvents` interfaces, se devuelven los cambios en una o dos dimensiones coordenadas, respectivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de búfer de texto  
 A continuación es las interfaces implementadas por el objeto de búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestas (es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de datos administrados por el búfer de texto del documento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; muchos clientes usan.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona de lectura y escritura mediante coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápido, proporciona acceso secuencial orientado a secuencias al texto en el búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o el moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y usarlo como clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para los eventos.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces de eventos del búfer de texto  
 A continuación es las interfaces de notificación de eventos del búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica a los clientes cuando un nuevo servicio de lenguaje se asocia con un búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica a los clientes cuando se inicializa un búfer de texto y cuando se realizan cambios a los datos en el búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica a los clientes los cambios en el búfer de texto subyacente en coordenadas unidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica a los clientes los cambios en el búfer de texto subyacente en coordenadas bidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica a los clientes los cambios a los datos de usuario.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica a los clientes del último gesto de confirmación para desencadenar el evento y proporciona el intervalo de texto cambiado. El `IVsPreliminaryTextChangeCommitEvents` interfaz no se activa en respuesta a deshacer o rehacer comandos. Los eventos se activan solo para los búferes que tienen un administrador de deshacer. `IVsPreliminaryTextChangeCommitEvents` se desencadena antes de otros eventos, como una lista descriptiva, con el fin de asegurarse de que los otros eventos no alteran el texto antes de confirmados los cambios. El VSPackage debe supervisar cualquiera el `IVsPreliminaryTextChangeCommitEvents` interfaz o `IVsFinalTextChangeCommitEvents` interfaz, pero no ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica a los clientes del último gesto de confirmación para desencadenar el evento y proporciona el intervalo de texto cambiado. El `IVsFinalTextChangeCommitEvents` interfaz no se activa en respuesta a deshacer o rehacer comandos. Los eventos se activan solo para los búferes que tienen un administrador de deshacer. `IVsFinalTextChangeCommitEvents` está pensado para su uso sólo por servicios de lenguaje u otros objetos que tienen control completo sobre la edición. El VSPackage debe supervisar cualquiera el `IVsPreliminaryTextChangeCommitEvents` interfaz o `IVsFinalTextChangeCommitEvents` interfaz, pero no ambos.|  
  
## <a name="see-also"></a>Vea también
 [Tener acceso al búfer de texto mediante el uso de la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) [Cómo: registrar los eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)