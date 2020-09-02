---
title: 'Cómo: desencadenar eventos cuando el editor pierde el foco | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204190"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Cómo: Desencadenar eventos cuando el editor pierde el foco
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A veces, es necesario saber cuándo un editor pierde el foco en el marco de la ventana. Por ejemplo, puede que tenga que extraer código de una ventana de código después de que el editor ya no se Centre en él. El siguiente procedimiento proporciona los pasos que deben seguirse para recibir la notificación del editor que pierde el foco.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Para desencadenar un evento en respuesta a un editor que pierde el foco  
  
1. Supervise los eventos de selección obteniendo un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objeto de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> y proporcione el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objeto.  
  
3. En la llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> , busque `elementid==SEID_WindowFrame` .  
  
4. Pruebe el `varValueNew` parámetro para dos cosas:  
  
    1. Marco de ventana que está buscando.  
  
    2. Punto en el que el programa pierde la selección hasta el marco de la ventana.
