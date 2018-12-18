---
title: VSTextBuffer (objeto) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 987514f20746b8480391a35d7a9c9a9d3663cac2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728782"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer (Objeto)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El objeto de búfer de texto representa una secuencia de texto Unicode, que suele estar asociado con un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto puede utilizarse fuera del contexto del editor de núcleo, como en el caso de un asistente.  
  
 En la tabla siguiente se muestra las interfaces de `VSTextBuffer`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interfaz OLE estándar. Se utiliza principalmente para el control en el búfer de deshacer y rehacer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interfaz OLE estándar.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interfaz OLE estándar.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestos (es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de datos administrados por el búfer de texto del documento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; muchos clientes usan.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se usa para buscar un búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona de lectura y escritura mediante coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápido, proporciona acceso secuencial orientado a secuencias al texto en el búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o el moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y usarlo como clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para los eventos.|  
  
## <a name="remarks"></a>Comentarios  
 El `VSTextBuffer` se encuentra normalmente por un `QueryInterface` llamar en `IVsTextBuffer`. Para obtener más información, consulte [búfer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edición de cifras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)

