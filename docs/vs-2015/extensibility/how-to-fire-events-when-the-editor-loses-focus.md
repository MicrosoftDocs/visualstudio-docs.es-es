---
title: Procedimiento Desencadenar eventos cuando el Editor pierde el foco | Documentos de Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204190"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procedimiento Desencadenamiento de eventos cuando el editor pierde el enfoque
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A veces es necesario saber cuándo un editor pierde el foco en el marco de ventana. Por ejemplo, es posible que necesita extraer el código de una ventana de código después de que el editor ya no se centra en él. El procedimiento siguiente proporciona los pasos a seguir para recibir una notificación del editor pierde el foco.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Para desencadenar un evento en respuesta a un editor pierde el foco  
  
1. Supervisar los eventos de selección mediante la obtención de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objeto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> y proporcionarla el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objeto.  
  
3. En la llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, busque `elementid==SEID_WindowFrame`.  
  
4. Prueba la `varValueNew` parámetro por dos cosas:  
  
    1. El marco de ventana que está buscando.  
  
    2. El punto en el que el programa pierde la selección para ese marco de ventana.
