---
title: Objeto objeto VsTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a52b1d480aaef11296517f1b9c5bb049f2488a8d
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413936"
---
# <a name="vstextview-object"></a>Objeto objeto VsTextView

La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. En esencia, la vista es lo que la mayoría de los usuarios hace referencia como editor. Dado que la vista está separada del búfer por varias capas de texto (ajuste de línea, texto de esquematización, etc.), no se garantiza que la vista sea una representación exacta del texto en el búfer. Para obtener más información sobre la vista de texto, consulte [acceso a la vista de texto mediante la API heredada](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

En la tabla siguiente se muestran las interfaces en el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.

|Interfaz|Descripción|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestas (es decir, acciones agrupadas en una sola unidad de deshacer/rehacer).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y tener acceso a la vista. `IVsTextView` no es seguro para subprocesos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con capas de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|

## <a name="see-also"></a>Consulte también

- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objeto objeto vstextbuffer](../extensibility/vstextbuffer-object.md)