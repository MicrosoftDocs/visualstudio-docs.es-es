---
title: "Ventanas de documento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de Visual Studio, ventanas de documento"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Ventanas de documento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En Visual Studio, un *ventana de documento* es una ventana secundaria de tramas que está asociada a una ventana de interfaz de múltiples documentos \(MDI\). Ventanas de documento se utilizan normalmente para la visualización y modificación de código fuente o de texto, pero también pueden alojar otros tipos funcionales. Ventanas de documento:  
  
-   Se pueden organizar en grupos de pestañas independientes de horizontal o vertical en el elemento primario MDI para que se puedan ver varios archivos al mismo tiempo.  
  
-   Se puede acoplar en cualquier orden en el elemento primario MDI.  
  
-   Puede flotar libremente.  
  
-   Se vinculan en el orden de tabulación a otras ventanas MDI.  
  
 Comandos para la agrupación, acoplar y desacoplar pueden encontrarse en el menú contextual de una ficha de la ventana de documento.  
  
 Para obtener más información sobre el comportamiento de las ventanas en Visual Studio, consulte [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## Implementación de la ventana de documento  
 Ventanas de documento se crean mediante la implementación de un editor. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz crea ventanas de documento como parte de una instancia de un editor. Para obtener más información, consulta [Interfaces heredadas en el Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Para proporcionar hacia atrás y reenviar los puntos en una ventana de navegación, implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaz. El editor de texto usa marcadores de texto para identificar puntos de navegación en el documento.  
  
## La tabla Document de ejecución  
 El IDE utiliza la tabla de documentos en ejecución \(RDT\) para el seguimiento del estado de cada ventana de documento. El RDT es el mecanismo a través del documento que windows notificación de eventos, como cuando se cierra una solución, o cuando se ha editado un archivo. Para obtener más información, consulta [Tabla de documentos de ejecución](../../extensibility/internals/running-document-table.md).  
  
## Vea también  
 [Documento carga retrasada](../../extensibility/internals/delayed-document-loading.md)