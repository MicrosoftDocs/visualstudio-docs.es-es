---
title: Personalización de Windows de código mediante la API heredada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ff4fb8a8a2e60b047361624ae805910906c19e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55022058"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>Personalizar las ventanas de código mediante el uso de la API heredada
Una ventana de código es un objeto de ventana de documento que admita una o varias vistas de texto. Las características exactas de una ventana de código dependen del servicio de lenguaje asociado. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco MDI secundario.  
  
 Ventanas de código se controlan mediante servicios de lenguaje, y cada servicio de lenguaje puede proporcionar su propio administrador de ventanas de código. Esto permite que el servicio de lenguaje agregar sus propios elementos gráficos a la ventana de código, como subrayados ondulados, colores y mucho más. Para obtener más información sobre cómo crear una ventana principal, consulte [una instancia el editor básico mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una ventana de código es un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que tiene una vista de texto y cualquier elemento gráfico situado en el objeto. Cuando se crea la ventana de código durante la creación de instancias del núcleo del editor, el servicio de lenguaje puede adjuntar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> a la ventana de código, como se muestra en la siguiente ilustración.  
  
 ![Gráfico de CodeWindow](../extensibility/media/vscodewindow.gif "objeto vscodewindow")  
Ventana Código  
  
 El servicio de lenguaje implementa el Administrador de ventanas de código y es responsable de administrar los elementos gráficos, como una barra desplegable. La ventana de código llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> método durante la inicialización de la ventana de código. Cuando se realiza esta llamada, el servicio de lenguaje puede agregar una barra desplegable o una barra de botones (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) a la ventana de código.  
  
## <a name="in-this-section"></a>En esta sección  
 `Customizing Code Windows by Using the Legacy API`  
 Explica cómo personalizar las ventanas de código mediante la API heredada.  
  
 [Cómo: Hospedar un editor en otro editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica cómo hospedar un segundo editor dentro de una ventana del editor.  
  
 [Cómo: Desencadenar eventos cuando el editor pierde el foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica cómo asociar una vista de documento a un objeto de datos del documento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Crear una instancia el editor básico mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Vista de acceso a Text mediante el uso de la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)