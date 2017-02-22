---
title: "Eventos del b&#250;fer de texto en la API heredada | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados - eventos del búfer de texto"
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Eventos del b&#250;fer de texto en la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El objeto de búfer de texto emite varios eventos que permiten responder a escenarios diferentes.  
  
 Cuando usa heredado API, debe implementar las interfaces siguientes para recibir la notificación de cambios en el búfer de texto.  Expone las interfaces al búfer de texto mediante la interfaz de `IConnectionPointContainer` en el búfer de texto para recibir notificación de los cambios de línea del búfer.  Para obtener más información, vea [Cómo: registrar eventos del búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md).  en el caso de `IVsTextStreamEvents` o de las interfaces de `IVsTextLinesEvents` , los cambios se devuelven en uno o bidimensionales coordenadas, respectivamente.  
  
## Interfaces del búfer de texto  
 Los siguientes son las interfaces implementadas por el objeto de búfer de texto.  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestos \(es decir, las acciones que se agrupan en una sola unidad de deshacer y rehacer\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de los datos de documento administrados por el búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|proporciona servicios básicos; utilizado por muchos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona funciones de lectura y escritura mediante coordenadas bidimensionales.  Hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona rápidamente, basado en secuencias, acceso secuencial al texto en el búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona funciones de lectura y escritura mediante coordenadas unidimensionales.  Hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades.  La propiedad más importante es el nombre, o moniker, del búfer.  Puede almacenar dispone de datos aleatorios en el búfer con esta interfaz creando GUID y usándolo como clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para los eventos.|  
  
## Interfaces de eventos del búfer de texto  
 Los siguientes son interfaces para la notificación de eventos del búfer de texto.  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica a clientes cuando un nuevo servicio de lenguaje es asociado a un búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica a clientes cuando se inicializa un búfer de texto y cuando se realizan cambios en los datos en el búfer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica a clientes de cambios al búfer de texto subyacente en coordenadas unidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica a clientes de cambios al búfer de texto subyacente en coordenadas bidimensionales.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica a clientes de cambios en los datos de usuario.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica a clientes de gestos último de confirmación para desencadenar el evento y proporciona el intervalo de texto cambiado.  La interfaz de `IVsPreliminaryTextChangeCommitEvents` no se desencadena en respuesta a comandos de deshacer o de rehacer.  Los eventos desencadenan sólo para los búferes que tienen un administrador de deshacer.  `IVsPreliminaryTextChangeCommitEvents` se desencadena antes de otros eventos, como lista descriptiva, para asegurarse de los otros eventos no modifica el texto antes de confirmar los cambios.  El Paquete debe controlar la interfaz de `IVsPreliminaryTextChangeCommitEvents` o la interfaz de `IVsFinalTextChangeCommitEvents` , pero no ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica a clientes de gestos último de confirmación para desencadenar el evento y proporciona el intervalo de texto cambiado.  La interfaz de `IVsFinalTextChangeCommitEvents` no se desencadena en respuesta a comandos de deshacer o de rehacer.  Los eventos desencadenan sólo para los búferes que tienen un administrador de deshacer.  `IVsFinalTextChangeCommitEvents` se ha diseñado para su uso con por los servicios u otros objetos que tienen control total sobre la edición.  El Paquete debe controlar la interfaz de `IVsPreliminaryTextChangeCommitEvents` o la interfaz de `IVsFinalTextChangeCommitEvents` , pero no ambos.|  
  
## Vea también  
 [Acceso al búfer de texto usando la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Cómo: registrar eventos del búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)