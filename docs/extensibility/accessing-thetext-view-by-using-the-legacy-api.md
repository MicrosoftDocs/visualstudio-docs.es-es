---
title: Obtener acceso a Text vista mediante la API heredado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bea908ee04913c5ec56678f1438229e045bf68c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Obtener acceso a Text vista mediante la API heredado
Una vista de texto es una presentación del texto que se almacena en un búfer de texto. Puede tener acceso a la vista de texto mediante el uso de la API heredada tal y como se muestra en la siguiente sección.  
  
## <a name="text-view-object"></a>Objeto de vista de texto  
 Cada vista está asociado a su propio búfer de texto y la vista es una ventana en los datos en el búfer. El siguiente diagrama muestra las interfaces del objeto de vista de texto, que se representa mediante clave <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Objeto de vista de texto de Visual Studio](../extensibility/media/vstextview.gif "objeto vstextview")  
Objeto de vista de texto  
  
 La vista es una manera de representar el texto en el búfer. Incluye características como el ajuste automático de línea y la esquematización, por lo que lo que ve en la vista no es una representación exacta del texto en el búfer.  
  
 Una vista permite a otros servicios o procesos para interceptar los comandos entrantes y actuar en ellos antes de la vista actúa sobre ellos. El servicio más común para ello es un servicio de lenguaje. Por ejemplo, un servicio de lenguaje podría necesario para interceptar el comando para la tecla ENTRAR proporcionar sugerencias personalizadas de comportamiento o la herramienta de sangría.  
  
## <a name="adding-functionality-to-the-text-view"></a>Agregar funcionalidad a la vista de texto  
 Puede personalizar el comportamiento de la vista de texto controlando pulsaciones de teclas específicas. Para interceptar las pulsaciones de teclas, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> en el objeto y proporcione un destino de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) a los comandos monitor y la intersección.  
  
 La vista de texto utiliza arquitectura secuencial para filtros de comandos. Nuevos filtros de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos) se agregan a la secuencia mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método.  
  
 Notificación de eventos para la vista de texto se proporciona mediante el uso de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfaz. Implemente esta interfaz en el objeto de cliente para recibir la notificación de cambios en la vista de texto. Exponer esta interfaz a la vista de texto mediante el uso de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz en la vista de texto para recibir la notificación de cambios de la vista.  
  
## <a name="see-also"></a>Vea también  
 [Cambiar la configuración de la vista mediante la API heredado](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Uso del Administrador de texto para supervisar la configuración Global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)