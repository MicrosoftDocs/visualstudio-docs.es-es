---
title: "Personalizaci&#243;n de Windows de c&#243;digo mediante la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - ventanas de código"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Personalizaci&#243;n de Windows de c&#243;digo mediante la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una ventana de código es un objeto de ventana de documento que admite una o varias vistas de texto. Las funciones de una ventana de código dependen del servicio de idioma asociado. En el modo de interfaz de múltiples documentos \(MDI\), la ventana de código es el marco secundario MDI.  
  
 Ventanas de código se controlan mediante servicios de lenguaje y cada servicio de lenguaje puede proporcionar su propio administrador de la ventana de código. Esto permite que el servicio de lenguaje agregar sus propios elementos gráficos a la ventana de código, como líneas de subrayado, colores y mucho más. Para obtener más información sobre cómo crear una ventana principal, consulte [Crear una instancia del Editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una ventana de código es un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que tiene una vista de texto y los elementos gráficos ubicados en el objeto. Al crear la ventana de código durante la creación de instancias del núcleo del editor, el servicio de lenguaje puede adjuntar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> a la ventana de código, como se muestra en la siguiente ilustración.  
  
 ![Gráfico CodeWindow](~/docs/extensibility/media/vscodewindow.gif "vscodewindow")  
Ventana Código  
  
 El servicio de lenguaje implementa el Administrador de ventanas de código y es responsable de administrar los elementos gráficos, como una barra de la lista desplegable. La ventana de código llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> durante la inicialización de la ventana de código. Cuando se realiza esta llamada, el servicio de lenguaje puede agregar una barra de la lista desplegable o una barra de botones \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) en la ventana de código.  
  
## En esta sección  
 `Customizing Code Windows by Using the Legacy API`  
 Explica cómo personalizar windows de código mediante la API heredada.  
  
 [Cómo: hospedar un Editor en otro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica cómo hospedar un segundo editor dentro de una ventana del editor.  
  
 [Cómo: desencadenar eventos cuando el Editor pierde el foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica cómo asociar una vista de documento a un objeto de datos del documento.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Crear una instancia del Editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Acceso a Text vista usando la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)