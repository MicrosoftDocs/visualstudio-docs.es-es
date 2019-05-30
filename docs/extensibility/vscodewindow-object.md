---
title: VSCodeWindow (objeto) | Microsoft Docs
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
ms.openlocfilehash: 165855fc6f8e63c6c7ad84cb8432419258b7ba4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322374"
---
# <a name="vscodewindow-object"></a>VSCodeWindow (objeto)
Una ventana de código es una ventana de documento especializado que puede incluir una o varias vistas de texto, normalmente el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.

 Arquitectónicamente, la ventana de código es una ventana de documento que está dentro de un marco de ventana. Funcionalmente, la ventana de código es simplemente una ventana de documento con características adicionales. En el modo de interfaz de múltiples documentos (MDI), la ventana de código es el marco MDI secundario. Para obtener más información, consulte [personalización de ventanas de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).

 En la tabla siguiente incluye las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.

|Método|Descripción|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Proporciona un mecanismo de acceso genérico para localizar un servicio que identifica un identificador único global (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa a un secundario de varios documentos MDI (interfaz) que contiene una o varias vistas de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Rellena un marco de ventana.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edición de cifras](https://www.microsoft.com/download/details.aspx?id=55984)