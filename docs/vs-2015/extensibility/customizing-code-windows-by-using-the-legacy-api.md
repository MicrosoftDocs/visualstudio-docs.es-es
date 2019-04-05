---
title: Personalización de Windows de código mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996059"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalización de Windows de código mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una ventana de código es un objeto de ventana de documento que admita una o varias vistas de texto. Las características exactas de una ventana de código dependen del servicio de lenguaje asociado. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco MDI secundario.  
  
 Ventanas de código se controlan mediante servicios de lenguaje, y cada servicio de lenguaje puede proporcionar su propio administrador de ventanas de código. Esto permite que el servicio de lenguaje agregar sus propios elementos gráficos a la ventana de código, como subrayados ondulados, colores y mucho más. Para obtener más información sobre cómo crear una ventana principal, consulte [crear instancias del Editor por Core con la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una ventana de código es un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que tiene una vista de texto y cualquier elemento gráfico situado en el objeto. Cuando se crea la ventana de código durante la creación de instancias del núcleo del editor, el servicio de lenguaje puede adjuntar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> a la ventana de código, como se muestra en la siguiente ilustración.  
  
 ![Gráfico de CodeWindow](../extensibility/media/vscodewindow.gif "objeto vscodewindow")  
Ventana Código  
  
 El servicio de lenguaje implementa el Administrador de ventanas de código y es responsable de administrar los elementos gráficos, como una barra desplegable. La ventana de código llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> método durante la inicialización de la ventana de código. Cuando se realiza esta llamada, el servicio de lenguaje puede agregar una barra desplegable o una barra de botones (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) a la ventana de código.  
  
## <a name="in-this-section"></a>En esta sección  
 `Customizing Code Windows by Using the Legacy API`  
 Explica cómo personalizar las ventanas de código mediante la API heredada.  
  
 [Cómo: Hospedar un Editor en otro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica cómo hospedar un segundo editor dentro de una ventana del editor.  
  
 [Cómo: Desencadenar eventos cuando el Editor pierde el foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica cómo asociar una vista de documento a un objeto de datos del documento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [El Editor básico de creación de instancias mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Acceso a la vista de texto mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
