---
title: Objeto VSCodeWindow ? Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697956"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Una ventana de código es una ventana de documento especializada <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> que puede incluir una o varias vistas de texto, normalmente el objeto.

 Arquitectónicamente, la ventana de código es una ventana de documento que está dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de varios documentos (MDI), la ventana de código es el marco secundario MDI. Para obtener más información, consulte Personalización de ventanas de [código mediante la API heredada.](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)

 En la tabla siguiente se <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> incluyen las interfaces del objeto.

|Método|Descripción|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para buscar un servicio que identifica un identificador único global (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa un elemento secundario de interfaz de varios documentos (MDI) que contiene una o varias vistas de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
