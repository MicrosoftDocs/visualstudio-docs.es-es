---
title: Objeto VSCodeWindow | Microsoft Docs
description: Obtenga información sobre las ventanas de código, que son ventanas de documentos especializadas que pueden incluir una o varias vistas de texto, normalmente el objeto VsTextView.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9803132605ee81c67785c8c0154861b26730ca5f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905337"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Una ventana de código es una ventana de documento especializada que puede incluir una o varias vistas de texto, normalmente el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto .

 Desde el punto de vista arquitectónico, la ventana de código es una ventana de documento que se encuentra dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco secundario MDI. Para más información, consulte [Personalización de ventanas de código mediante la API heredada.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

 En la tabla siguiente se incluyen las interfaces del <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto .

|Método|Descripción|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para localizar un servicio que identifica un identificador único global (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa un elemento secundario de varias interfaces de documento (MDI) que contiene una o varias vistas de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edición de cifras](https://www.microsoft.com/download/details.aspx?id=55984)