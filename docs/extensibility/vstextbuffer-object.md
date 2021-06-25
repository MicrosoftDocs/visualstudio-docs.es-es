---
title: Objeto VSTextBuffer | Microsoft Docs
description: El objeto VSTextBuffer representa una secuencia de texto Unicode, que suele estar asociada a un archivo. En este artículo se enumeran las interfaces de VSTextBuffer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905181"
---
# <a name="vstextbuffer-object"></a>Objeto VSTextBuffer
El objeto de búfer de texto representa una secuencia de texto Unicode, que suele estar asociada a un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto se puede usar fuera del contexto del editor principal, como en, un asistente.

 En la tabla siguiente se muestran las interfaces de `VSTextBuffer` .

|Método|Descripción|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaz OLE estándar. Se usa para el control de deshacer y rehacer en el búfer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaz OLE estándar.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones compuestas (es decir, acciones que se agrupan en una sola unidad de deshacer/rehacer).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de los datos del documento administrados por el búfer de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; usado por muchos clientes.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se usa para buscar en un búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona funcionalidades de lectura y escritura mediante coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona funcionalidades de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona acceso rápido, orientado a secuencias y secuencial al texto en el búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y su uso como clave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para eventos.|

## <a name="remarks"></a>Observaciones
 normalmente `VSTextBuffer` se encuentra mediante una llamada en `QueryInterface` `IVsTextBuffer` . Para obtener más información, vea [Búfer de texto.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)