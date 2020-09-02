---
title: Objeto objeto vstextbuffer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690641"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer (Objeto)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El objeto de búfer de texto representa una secuencia de texto Unicode, que generalmente está asociada a un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto se puede usar fuera del contexto del editor principal, como en el caso de un asistente.  
  
 En la tabla siguiente se muestran las interfaces de `VSTextBuffer` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaz OLE estándar. Se utiliza principalmente para el control de deshacer y rehacer en el búfer.|  
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
  
## <a name="remarks"></a>Observaciones  
 `VSTextBuffer`Normalmente, se encuentra en una `QueryInterface` llamada en `IVsTextBuffer` . Para obtener más información, vea [búfer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edición de figuras](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
