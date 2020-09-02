---
title: Objeto objeto vscodewindow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690773"
---
# <a name="vscodewindow-object"></a>VSCodeWindow (Objeto)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una ventana de código es una ventana de documento especializada que puede incluir una o varias vistas de texto, normalmente el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 En la arquitectura, la ventana de código es una ventana de documento que se encuentra dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco secundario MDI. Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 En la tabla siguiente se incluyen las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.  
  
|Método|Descripción|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para ubicar un servicio que identifica un identificador único global (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa un elemento secundario de la interfaz de múltiples documentos (MDI) que contiene una o varias vistas de código.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edición de figuras](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
