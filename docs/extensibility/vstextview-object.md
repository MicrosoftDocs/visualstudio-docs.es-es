---
title: Objeto VSTextView | Microsoft Docs
description: El objeto VSTextView es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90fad54be26c11db31d649d0ae6b25c108a6b361
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905168"
---
# <a name="vstextview-object"></a>Objeto VSTextView

La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. Básicamente, la vista es a la que la mayoría de los usuarios hacen referencia como editor. Dado que la vista está separada del búfer por varias capas de texto (ajuste de palabras, texto de línea, entre otras), no se garantiza que la vista sea una representación exacta del texto en el búfer. Para obtener más información sobre la vista de texto, vea Acceso a la vista [texto mediante la API heredada.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

En la tabla siguiente se muestran las interfaces del <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto .

|Interfaz|Descripción|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestas (es decir, acciones que se agrupan en una sola unidad de deshacer o rehacer).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y acceder a la vista. `IVsTextView` no es seguro para subprocesos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con las capas de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|

## <a name="see-also"></a>Consulta también

- [Edición de cifras](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)