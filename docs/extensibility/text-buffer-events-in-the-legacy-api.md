---
title: "Eventos de búfer de texto de la API heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5118fe29463368bcca90e21830e1418d41c18339
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventos de búfer de texto de la API heredado
El objeto de búfer de texto emite varios eventos diferentes que le permiten responder a distintas situaciones.  
  
 Cuando se usa la API heredada, debe implementar las interfaces siguientes para recibir la notificación de cambios en el búfer de texto. Exponer las interfaces en el búfer de texto mediante el `IConnectionPointContainer` interfaz en el búfer de texto para recibir una notificación de línea se cambia desde el búfer. Para obtener más información, consulte [Cómo: registrar eventos de búfer de texto con la API de heredado de](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). En el caso de `IVsTextStreamEvents` o `IVsTextLinesEvents` interfaces, se devuelven los cambios en cualquier uno o dos dimensiones coordenadas, respectivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de búfer de texto  
 A continuación es las interfaces implementadas por el objeto de búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestas (es decir, las acciones que se agrupan en una unidad de deshacer/rehacer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de datos administrados por el búfer de texto del documento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona los servicios básicos; utilizado por muchos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona leer y escribir funciones con coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona, orientado a secuencias y secuencial acceso rápido a texto en el búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona leer y escribir funciones con coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o el moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y lo usa como una clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión de eventos.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces de eventos del búfer de texto  
 A continuación es las interfaces de notificación de eventos del búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica a los clientes cuando un nuevo servicio de lenguaje está asociado a un búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica a los clientes cuando se inicializa un búfer de texto y cuando se realizan cambios a los datos en el búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica a los clientes de los cambios en el búfer de texto subyacente en coordenadas unidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica a los clientes de los cambios en el búfer de texto subyacente en coordenadas bidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica a los clientes de los cambios en los datos de usuario.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica a los clientes de la última gesto de confirmación para desencadenar el evento y proporciona el intervalo de texto cambia. El `IVsPreliminaryTextChangeCommitEvents` interfaz no se activa en respuesta a deshacer ni rehacer los comandos. Solo los eventos se desencadenan para los búferes que tienen un administrador de deshacer. `IVsPreliminaryTextChangeCommitEvents`se desencadena antes de otros eventos, como una lista descriptiva, para asegurarse de que los otros eventos de no alteran el texto antes de que se confirmen los cambios. El VSPackage debe supervisar cualquiera el `IVsPreliminaryTextChangeCommitEvents` interfaz o `IVsFinalTextChangeCommitEvents` interfaz, pero no ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica a los clientes de la última gesto de confirmación para desencadenar el evento y proporciona el intervalo de texto cambia. El `IVsFinalTextChangeCommitEvents` interfaz no se activa en respuesta a deshacer ni rehacer los comandos. Solo los eventos se desencadenan para los búferes que tienen un administrador de deshacer. `IVsFinalTextChangeCommitEvents`está diseñada para su uso únicamente servicios de lenguaje u otros objetos que tienen un control completo sobre la edición. El VSPackage debe supervisar cualquiera el `IVsPreliminaryTextChangeCommitEvents` interfaz o `IVsFinalTextChangeCommitEvents` interfaz, pero no ambos.|  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso al búfer de texto mediante la API heredado](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Cómo: registrar eventos de búfer de texto con la API de heredado de](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)