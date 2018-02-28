---
title: Objeto del objeto VSTextBuffer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 643bd434e058a24cc17936d9ab2f333489b8aa5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vstextbuffer-object"></a>Objeto del objeto VSTextBuffer
El objeto de búfer de texto representa una secuencia de texto Unicode, que suele estar asociado con un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto puede utilizarse fuera del contexto del editor principal, como en el caso de un asistente.  
  
 En la tabla siguiente se muestra las interfaces de `VSTextBuffer`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interfaz estándar de OLE. Se utiliza principalmente para controlar en el búfer de deshacer/rehacer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interfaz estándar de OLE.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita la creación de acciones de compuestos (es decir, las acciones que se agrupan en una unidad de deshacer/rehacer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de datos administrados por el búfer de texto del documento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona los servicios básicos; utilizado por muchos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se utiliza para buscar un búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona leer y escribir funciones con coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona leer y escribir funciones con coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona, orientado a secuencias y secuencial acceso rápido a texto en el búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o el moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y lo usa como una clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión de eventos.|  
  
## <a name="remarks"></a>Comentarios  
 El `VSTextBuffer` normalmente se encuentra por un `QueryInterface` llamar en `IVsTextBuffer`. Para obtener más información, consulte [búfer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edición de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)