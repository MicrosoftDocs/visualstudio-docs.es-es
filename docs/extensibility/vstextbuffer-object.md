---
title: VSTextBuffer Objeto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697724"
---
# <a name="vstextbuffer-object"></a>Objeto VSTextBuffer
El objeto de búfer de texto representa una secuencia de texto Unicode, que generalmente se asocia a un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto se puede utilizar fuera del contexto del editor principal, como en un asistente.

 En la tabla siguiente `VSTextBuffer`se muestran las interfaces de .

|Método|Descripción|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaz OLE estándar. Se utiliza para deshacer/rehacer el manejo en el búfer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaz OLE estándar.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestas (es decir, acciones que se agrupan en una sola unidad de deshacer/rehacer).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Permite la persistencia de los datos de documento administrados por el búfer de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; utilizado por muchos clientes.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se utiliza para buscar un búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona capacidades de lectura y escritura mediante coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona capacidades de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona acceso rápido, orientado a secuencias y secuencial al texto en el búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre, o moniker, del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz creando un GUID y utilizándolo como clave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para eventos.|

## <a name="remarks"></a>Observaciones
 El `VSTextBuffer` se encuentra `QueryInterface` generalmente `IVsTextBuffer`por una llamada en . Para obtener más información, consulte [Zona de influencia](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)de texto .

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edición de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
