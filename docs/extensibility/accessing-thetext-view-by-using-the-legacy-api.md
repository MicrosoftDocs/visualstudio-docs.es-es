---
title: "Acceso a Text vista usando la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - vista de texto"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Acceso a Text vista usando la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una vista de texto es una presentación de texto que se almacena en un búfer de texto.  Puede tener acceso a la vista de texto mediante heredado API como se muestra en la sección siguiente.  
  
## objeto de vista de texto  
 Cada vista es asociado al propio búfer de texto, y la vista es una ventana en los datos en el búfer.  El diagrama siguiente muestra las interfaces principales del objeto de vista de texto, representado por <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Objeto de vista de texto de Visual Studio](~/extensibility/media/vstextview.gif "vstextview")  
objeto de vista de texto  
  
 La vista es una manera de mostrar texto en el búfer.  Incluye características como ajuste de línea, y la esquematización, de modo que se ven en la vista no es una representación exacta de texto en el búfer.  
  
 Una vista permite a otros servicios o procesos para interceptar comandos de entrada y actuar en ellos antes de que la vista actúa en ellos.  El servicio más común para ello es un servicio de lenguaje.  Un servicio de lenguaje necesite, por ejemplo, interceptar el comando para que la tecla ENTRAR proporciona comportamiento personalizado o información sobre herramientas de sangría.  
  
## Agregar funcionalidad a la vista de texto  
 Puede personalizar el comportamiento de la vista de texto controlando pulsaciones de tecla concretas.  Para interceptar las pulsaciones de tecla, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> en el objeto, y proporciona un destino de comando \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) para controlar y para interceptar comandos.  
  
 La vista de texto utiliza la arquitectura secuencial de los filtros de comando.  Los nuevos filtros de comando \(objetos de<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \) se agregan a la secuencia llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  
  
 La notificación de eventos para la vista de texto se proporciona mediante la interfaz de `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` .  Implemente esta interfaz en el objeto de cliente para recibir notificación de cambios en la vista de texto.  Exponga esta interfaz a la vista de texto mediante la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> en la vista de texto para recibir notificación de cambios de la vista.  
  
## Vea también  
 [Cambiar la configuración de vista mediante la API heredada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Mediante el Administrador de texto para supervisar la configuración Global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)