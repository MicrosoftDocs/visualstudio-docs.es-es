---
title: "Personalización de ventanas de código mediante la API heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f0b00c31280b9471da99aea55118e25dd551ad96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalización de ventanas de código mediante la API heredado
Una ventana de código es un objeto de ventana de documento que admite una o varias vistas de texto. Las características exactas de una ventana de código dependen del servicio de idioma asociado. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco MDI secundario.  
  
 Ventanas de código se controlan mediante servicios de lenguaje, y cada servicio de lenguaje puede proporcionar su propio administrador de ventanas de código. Esto permite que el servicio de lenguaje agregar sus propios elementos gráficos a la ventana de código, como los subrayados ondulados, colores y mucho más. Para obtener más información sobre cómo crear una ventana principal, consulte [crear instancias de los núcleos Editor usando la API heredado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una ventana de código es un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que tiene una vista de texto y las opciones gráficas ubicados en el objeto. Al crear la ventana de código durante la creación de instancias del núcleo de editor, el servicio de lenguaje puede adjuntar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> a la ventana de código, como se muestra en la siguiente ilustración.  
  
 ![Gráfico CodeWindow](../extensibility/media/vscodewindow.gif "objeto vscodewindow")  
Ventana Código  
  
 El servicio de lenguaje implementa el Administrador de ventanas de código y es responsable de administrar elementos gráficos, como una barra de la lista desplegable. La ventana de código llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> método durante la inicialización de la ventana de código. Cuando se realiza esta llamada, el servicio de lenguaje puede agregar una barra de la lista desplegable o una barra de botones (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) a la ventana de código.  
  
## <a name="in-this-section"></a>En esta sección  
 `Customizing Code Windows by Using the Legacy API`  
 Explica cómo personalizar windows de código mediante la API heredada.  
  
 [Cómo: hospedar un Editor en otro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica cómo hospedar un segundo editor dentro de una ventana del editor.  
  
 [Cómo: desencadenar eventos cuando el Editor pierde el foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica cómo asociar una vista de documento a un objeto de datos del documento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Crear una instancia el Editor básico mediante la API heredado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Obtener acceso a Text vista mediante la API heredado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)