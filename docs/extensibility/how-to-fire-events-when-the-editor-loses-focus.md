---
title: "C&#243;mo: desencadenar eventos cuando el Editor pierde el foco | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados: desencadenan eventos al perder el foco"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: desencadenar eventos cuando el Editor pierde el foco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A veces es necesario saber cuándo un editor pierde el foco del marco de la ventana.  Por ejemplo, puede que deba extraer código de una ventana de código después de que el editor se foco no más en él.  El procedimiento siguiente proporciona los pasos para seguir para recibir notificación de ejecuta el foco del editor.  
  
### Para desencadenar un evento en respuesta a un enfoque de ejecuta editor  
  
1.  Controlar los eventos de selección obtener un objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> y proporcionelo el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> .  
  
3.  En la llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, busque `elementid==SEID_WindowFrame`.  
  
4.  pruebe el parámetro de `varValueNew` para dos cosas:  
  
    1.  El marco de la ventana que está buscando.  
  
    2.  El punto en el que el programa pierde la selección a ese marco de la ventana.