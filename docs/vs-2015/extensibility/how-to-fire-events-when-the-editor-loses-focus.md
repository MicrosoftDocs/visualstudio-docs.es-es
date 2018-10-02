---
title: 'Cómo: desencadenar eventos cuando el Editor pierde el foco | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2462e41470b72c63f5c96a69d2776af2a640c372
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575651"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Cómo: desencadenar eventos cuando el Editor pierde el foco
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: Fire eventos cuando el Editor pierde el foco](https://docs.microsoft.com/visualstudio/extensibility/how-to-fire-events-when-the-editor-loses-focus).  
  
A veces es necesario saber cuándo un editor pierde el foco en el marco de ventana. Por ejemplo, es posible que necesita extraer el código de una ventana de código después de que el editor ya no se centra en él. El procedimiento siguiente proporciona los pasos a seguir para recibir una notificación del editor pierde el foco.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Para desencadenar un evento en respuesta a un editor pierde el foco  
  
1.  Supervisar los eventos de selección mediante la obtención de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objeto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> y proporcionarla el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objeto.  
  
3.  En la llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, busque `elementid==SEID_WindowFrame`.  
  
4.  Prueba la `varValueNew` parámetro por dos cosas:  
  
    1.  El marco de ventana que está buscando.  
  
    2.  El punto en el que el programa pierde la selección para ese marco de ventana.

