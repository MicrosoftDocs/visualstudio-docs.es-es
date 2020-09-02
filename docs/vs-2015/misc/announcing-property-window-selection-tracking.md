---
title: Anuncio del seguimiento de selección de la ventana de propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002457"
---
# <a name="announcing-property-window-selection-tracking"></a>Anuncio del seguimiento de selección de la ventana de propiedades
Si desea trabajar con la ventana **propiedades** o **las páginas de propiedades (** por ejemplo, un formulario, texto o una selección para la que desea ver las propiedades), debe tener conocimientos completos sobre cómo coordinar la selección. Por ejemplo, debe saber si tiene selección única o varias selecciones. A continuación, debe anunciar el tipo de selección (uno o varios) al IDE mediante la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz. Esta interfaz proporciona la información necesaria para la ventana **propiedades** .  
  
### <a name="to-announce-selection-to-the-environment"></a>Para anunciar la selección al entorno  
  
1. Llame a `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. Para ello, utilice el puntero de sitio que se pasa a la vista cuando se creó.  
  
    2. Llame a `QueryService` desde la vista para el `SID_STrackSelection` servicio.  
  
         Esto devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> método cada vez que cambie la selección y pase un puntero a un objeto que implemente <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     El objeto contenedor de selección puede utilizar selecciones únicas o múltiples y contiene la información de selección en un `IDispatch` objeto. Al llamar al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> método, se notifica a la ventana de **propiedades** que la selección ha cambiado. A continuación, la ventana **propiedades** utiliza los objetos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para determinar si se han producido una o varias selecciones y cuáles son las selecciones de objetos reales.  
  
     Si especifica una selección múltiple, la ventana **propiedades** busca la intersección entre las propiedades comunes de los objetos. Si especifica una selección de un solo objeto, en la ventana **propiedades** se muestran todas las propiedades de un objeto.  
  
## <a name="see-also"></a>Consulte también  
 [Extender propiedades](../extensibility/internals/extending-properties.md)   
 [Páginas de propiedades](../extensibility/internals/property-pages.md)