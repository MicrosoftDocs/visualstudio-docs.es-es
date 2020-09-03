---
title: Obtener acceso a la vista de texto mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184951"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Acceso a la vista de texto mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una vista de texto es una presentación del texto que se almacena en un búfer de texto. Puede tener acceso a la vista de texto mediante la API heredada, tal y como se muestra en la sección siguiente.  
  
## <a name="text-view-object"></a>Objeto de vista de texto  
 Cada vista está asociada a su propio búfer de texto y la vista es una ventana de los datos en el búfer. En el diagrama siguiente se muestran las interfaces clave del objeto de vista de texto, que se representa mediante <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Objeto de vista de texto de Visual Studio](../extensibility/media/vstextview.gif "objeto VsTextView")  
Objeto de vista de texto  
  
 La vista es una forma de presentar el texto en el búfer. Incluye características como el ajuste de línea y la esquematización, de modo que lo que se ve en la vista no sea una representación exacta del texto en el búfer.  
  
 Una vista permite que otros servicios o procesos intercepten los comandos de entrada y actúen en ellos antes de que la vista actúe sobre ellos. El servicio más común para ello es un servicio de lenguaje. Es posible que un servicio de lenguaje necesite, por ejemplo, interceptar el comando para que la tecla entrar proporcione un comportamiento personalizado de sangría o información sobre herramientas.  
  
## <a name="adding-functionality-to-the-text-view"></a>Agregar funcionalidad a la vista de texto  
 Puede personalizar el comportamiento de la vista de texto mediante el control de pulsaciones de teclas específicas. Para interceptar las pulsaciones de teclas, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> en el objeto y proporcione un destino de comando ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) para supervisar e interceptar comandos.  
  
 La vista de texto utiliza una arquitectura secuencial para los filtros de comandos. Los nuevos filtros de comandos ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos) se agregan a la secuencia mediante una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método.  
  
 La notificación de eventos para la vista de texto se proporciona mediante la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfaz. Implemente esta interfaz en el objeto de cliente para recibir la notificación de cambios en la vista de texto. Exponga esta interfaz a la vista de texto mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz de la vista de texto para recibir la notificación de los cambios de la vista.  
  
## <a name="see-also"></a>Consulte también  
 [Cambiar la configuración de vista mediante la API heredada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Uso del administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
