---
title: "Cómo: desencadenar eventos cuando el Editor pierde el foco | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb20adf3950e87c37e2ca64bcd78913839f89d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Cómo: desencadenar eventos cuando el Editor pierde el foco
A veces es necesario saber cuándo un editor pierde el foco en el marco de ventana. Por ejemplo, deberá extraer el código desde una ventana de código después de que el editor ya no se centra en ella. El procedimiento siguiente proporciona los pasos que deben seguirse para recibir una notificación del editor pierde el foco.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Para desencadenar un evento en respuesta a un editor pierde el foco  
  
1.  Supervisar los eventos de selección mediante la obtención de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objeto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> y proporcionarla el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objeto.  
  
3.  En la llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, busque `elementid==SEID_WindowFrame`.  
  
4.  Prueba la `varValueNew` parámetro para dos cosas:  
  
    1.  El marco de ventana que está buscando.  
  
    2.  El punto en el que el programa pierde la selección a ese marco de ventana.