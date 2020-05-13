---
title: Objeto VSTextView ( VSTextView Object) Microsoft Docs
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
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697709"
---
# <a name="vstextview-object"></a>VSTextView objeto

La vista de texto es una ventana que permite a los usuarios ver y editar el texto Unicode del búfer de texto. Esencialmente, la vista es lo que la mayoría de los usuarios se refieren como el editor. Dado que la vista está separada del búfer por varias capas de texto (ajuste de palabras, texto de esquematización, etc.), no se garantiza que la vista sea una representación exacta del texto en el búfer. Para obtener más información acerca de la vista de texto, consulte [Acceso a la vista de texto mediante la API heredada.](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015)

En la tabla siguiente se <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> muestran las interfaces del objeto.

|Interfaz|Descripción|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestas (es decir, acciones que se agrupan en una sola unidad de deshacer/rehacer).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Proporciona los métodos básicos para administrar y tener acceso a la vista. `IVsTextView`no es seguro enhebrado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea y administra un panel de ventana.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interactúa con capas de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Realiza operaciones en la vista desde un subproceso diferente.|

## <a name="see-also"></a>Vea también

- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)
