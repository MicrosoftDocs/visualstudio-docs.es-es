---
title: Objeto objeto vscodewindow | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36b7e0e6806f88efe373dffa3f21ba79baefb281
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189056"
---
# <a name="vscodewindow-object"></a>Objeto objeto vscodewindow
Una ventana de código es una ventana de documento especializada que puede incluir una o varias vistas de texto, normalmente el objeto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 En la arquitectura, la ventana de código es una ventana de documento que se encuentra dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco secundario MDI. Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 En la tabla siguiente se incluyen las interfaces del objeto <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>.

|Método|Descripción|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para ubicar un servicio que identifica un identificador único global (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa un elemento secundario de la interfaz de múltiples documentos (MDI) que contiene una o varias vistas de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)