---
title: "Objeto objeto VSCodeWindow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSCodeWindow"
helpviewer_keywords: 
  - "vistas [Visual Studio SDK] objeto objeto VSCodeWindow"
  - "Objeto objeto VsCodeWindow"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Objeto objeto VSCodeWindow
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una ventana de código es una ventana de documento especializado que puede incluir una o varias vistas de texto, normalmente la <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 Su arquitectura, la ventana de código es una ventana de documento que está dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de múltiples documentos \(MDI\), la ventana de código es el marco secundario MDI. Para obtener más información, consulta [Personalización de Windows de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 En la tabla siguiente incluye las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.  
  
|Método|Descripción|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para buscar un servicio que identifica un identificador único global \(GUID\).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa a una secundaria de varios documentos MDI \(interfaz\) que contiene una o más vistas de código.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/es-es/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)