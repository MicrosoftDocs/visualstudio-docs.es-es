---
title: "C&#243;mo: implementar la b&#250;squeda y reemplazo mecanismo | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados: buscar y reemplazar"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: implementar la b&#250;squeda y reemplazo mecanismo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio proporciona dos maneras de implementar buscar\/comando reemplazarlas.  Una consiste en pasar una imagen de texto al shell y lo permiten administrar buscar, resaltar, y reemplazar texto.  Esto permite a los usuarios especificar intervalos varias de texto.  O bien, el Paquete puede controlar esta funcionalidad propio.  En ambos casos debe notificar el shell sobre el destino actual y destinos para todos los documentos abiertos.  
  
### Para implementar la búsqueda y reemplace  
  
1.  Implemente la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> en uno de los objetos devueltos por las propiedades del cuadro <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  Si está creando un editor personalizado, debe implementar esta interfaz como parte de la clase de editor personalizado.  
  
2.  Utilice el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> para especificar las opciones que el editor permite e indicar si implementa buscar del texto.  
  
     Si el editor permite imagen de texto que busca, implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Si no, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> de implementan y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Si implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y los métodos de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> , puede simplificar las tareas que buscan llamando a la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> .  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>