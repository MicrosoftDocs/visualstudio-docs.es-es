---
title: Objeto objeto vstextbuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1895efa9ef10e1e554b98844619507224f09126
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189027"
---
# <a name="vstextbuffer-object"></a>Objeto objeto vstextbuffer
El objeto de búfer de texto representa una secuencia de texto Unicode, que generalmente está asociada a un archivo. Un objeto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> se puede usar fuera del contexto del editor principal, como en, un asistente.

 En la tabla siguiente se muestran las interfaces de `VSTextBuffer`.

|Método|Descripción|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaz OLE estándar. Se utiliza para el control de deshacer y rehacer en el búfer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaz OLE estándar.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones de compuestos (es decir, acciones agrupadas en una sola unidad de deshacer/rehacer).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de los datos de documento administrados por el búfer de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; lo usan muchos clientes.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se usa para buscar en un búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona funciones de lectura y escritura que usan coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona capacidades de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona acceso secuencial rápido y orientado a secuencias al texto del búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre, o moniker, del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y su uso como clave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para eventos.|

## <a name="remarks"></a>Comentarios
 El `VSTextBuffer` suele encontrarse en una llamada `QueryInterface` en `IVsTextBuffer`. Para obtener más información, vea [búfer de texto](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)