---
title: "C&#243;mo: proporcionar automatizaci&#243;n para Windows | Microsoft Docs"
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
  - "automatización [Visual Studio SDK], ventanas de herramientas"
  - "ventanas de herramientas, automatización"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: proporcionar automatizaci&#243;n para Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede proporcionar automatización para el documento y las ventanas de herramientas.  Proporcionar la automatización es aconsejable siempre que desee crear objetos de automatización disponibles en una ventana, y el entorno no ya proporciona un objeto confeccionado de automatización, como haría con una lista de tareas.  
  
## Automatización de las ventanas de herramientas  
 el entorno proporciona la automatización en una ventana de herramientas devolviendo un objeto estándar de <xref:EnvDTE.Window> como se explica en el procedimiento siguiente:  
  
#### Para proporcionar la automatización de las ventanas de herramientas  
  
1.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> mediante el entorno con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> como parámetro de `VSFPROPID` para obtener el objeto de `Window` .  
  
2.  Cuando un llamador solicita un objeto VSPackage\-específico de automatización para la ventana de herramientas con <xref:EnvDTE.Window.Object%2A>, el entorno llama `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o las interfaces de `IDispatch` .  `IExtensibleObject` y `IVsExtensibleObject` proporcionan un método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> .  
  
3.  Cuando el entorno llama al método de `GetAutomationObject` que pasa `NULL`, responde pasando la reproducción del objeto VSPackage\-específico.  
  
4.  Si llama `QueryInterface` para `IExtensibleObject` y los errores de `IVsExtensibleObject` , el entorno llama `QueryInterface` para `IDispatch`.  
  
## Automatización de las ventanas de documento  
 Un objeto de <xref:EnvDTE.Document> standard también está disponible en el entorno, aunque un editor puede tener su propia implementación del objeto de `T:EnvDTE.Document` implementando la interfaz de `IExtensibleObject` y respuesta a `GetAutomationObject`.  
  
 Además, un editor puede proporcionar un objeto VSPackage\-específico de automatización, recuperado con el método de <xref:EnvDTE.Document.Object%2A> , implementando las interfaces de `IVsExtensibleObject` o de `IExtensibleObject` .  [Muestras de VSSDK](../../misc/vssdk-samples.md) contribuye un objeto documento\-específico de automatización RTF.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>