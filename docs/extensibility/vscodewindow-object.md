---
title: Objeto objeto vscodewindow | Microsoft Docs
description: Obtenga información sobre las ventanas de código, que son ventanas de documento especializadas que pueden incluir una o varias vistas de texto, normalmente el objeto objeto VsTextView.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b324c0b572f025b3733233d70cf36485f90524c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925860"
---
# <a name="vscodewindow-object"></a>Objeto objeto vscodewindow
Una ventana de código es una ventana de documento especializada que puede incluir una o varias vistas de texto, normalmente el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.

 En la arquitectura, la ventana de código es una ventana de documento que se encuentra dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco secundario MDI. Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 En la tabla siguiente se incluyen las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.

|Método|Descripción|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para ubicar un servicio que identifica un identificador único global (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa un elemento secundario de la interfaz de múltiples documentos (MDI) que contiene una o varias vistas de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)