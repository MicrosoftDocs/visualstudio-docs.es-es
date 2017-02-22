---
title: "Hospedaje de IntelliSense | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados - IntelliSense de hospedaje"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Hospedaje de IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio permite hospedar de IntelliSense.  El hospedaje de IntellSense permite proporcionar IntelliSense para el código que no está hospedado en el editor de texto de Visual Studio.  
  
## IntelliSense de hospedaje uso  
 En Visual Studio, cualquier código que tenga acceso a una finalización establecida y un búfer de texto pueden obtener las ventanas de IntelliSense en cualquier parte de la interfaz de usuario \(UI\).  Algunos escenarios de ejemplo de esto son finalización en la ventana de **Inspección** o en el campo de la condición de una ventana de propiedades de punto de interrupción.  
  
### Interfaces de implementación  
  
#### IVsIntellisenseHost  
 Cualquier componente de la interfaz de usuario que las ventanas emergentes de IntelliSense de hospeda deben admitir la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> .  La vista de texto básica predeterminada de editor incluye una implementación común de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> para conservar la funcionalidad actual de IntelliSense.  en general, los métodos de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> representan un subconjunto de qué se implementa en la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  El subconjunto incluye control de la interfaz de usuario de IntelliSense, manipulación del símbolo de intercalación y de selección, y funcionalidad simple de reemplazo de texto.  Además, la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> separan IntelliSense “sujetan” y “contexto” para poder proporcionar IntelliSense para los asuntos que no existen directamente en el búfer de texto que se utiliza para el contexto.  
  
#### IVsIntellisenseHost.GetHostFlags  
 un proveedor de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> debe implementar el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> para permitir a un cliente para determinar lo que admite el tipo de características de IntelliSense el host.  
  
 El host marcadores, definido en [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), se resume a continuación.  
  
|Indicador de host de IntelliSense|Descripción|  
|---------------------------------------|-----------------|  
|IHF\_READONLYCONTEXT|Establecer este marcador significa que el búfer de contexto es de sólo lectura y edición sólo se produce dentro del texto sujeto.|  
|IHF\_NOSEPERATESUBJECT|Establecer este marcador significa que no hay ningún asunto independiente de IntelliSense.  El objeto existe en el búfer de contexto, como en el sistema tradicional de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense.|  
|IHF\_SINGLELINESUBJECT|Establecer este marcador significa que el asunto no es capaz de varias líneas, como en una edición de una sola línea de la ventana de **Inspección** .|  
|IHF\_FORCECOMMITTOCONTEXT|Si este marcador está determinado y el búfer de contexto debe actualizarse, el host habilita la marca de solo lectura en el búfer de contexto que se omiten y ediciones para continuar.|  
|IHF\_OVERTYPE|La edición \(en asunto o contexto\) debe hacer en modo sobrescribirá.|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit e IVsIntellisenseHost.AfterCompletorCommit  
 Estos métodos de devolución de llamada llama la ventana de finalización antes y después de que el texto es de confianza, el proceso previo y el procesamiento posterior habilitados.  
  
#### IVsIntellisenseCompletor  
 La interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> es una versión co\-creatable de la ventana estándar de finalización usada por el entorno de desarrollo integrado \(IDE\).  Cualquier interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> puede implementar rápidamente IntelliSense utilizando esta interfaz completor.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>