---
title: Presentación de seguimiento de selección de ventana de propiedad | Documentos de Microsoft
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
ms.openlocfilehash: 1ef6984a21099bfad013ef97534d9984fa81d10d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989123"
---
# <a name="announcing-property-window-selection-tracking"></a>Anuncio del seguimiento de selección de la ventana de propiedades
Si desea trabajar con el **propiedades** ventana o el **propiedad** páginas, por ejemplo, un formulario, texto o una selección para el que desea ver las propiedades, a continuación, debe tener un conocimiento completo de cómo se coordinar la selección. Por ejemplo, debe conocer si tienen selección única o selecciones múltiples. A continuación, deberá anunciar el tipo de selección (uno o varios) en el IDE mediante el <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz. Esta interfaz proporciona información que necesita la **propiedades** ventana.  
  
### <a name="to-announce-selection-to-the-environment"></a>Anunciar la selección en el entorno  
  
1.  Llame a `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  Para ello, use el puntero de sitio que se pasa a la vista cuando se creó.  
  
    2.  Llame a `QueryService` desde la vista de la `SID_STrackSelection` service.  
  
         Esto devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> método cada vez que cambia la selección y pase un puntero a un objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     El objeto de contenedor de selección puede utilizar sola o selecciones múltiples y contiene la información de selección de un `IDispatch` objeto. Una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> método notifica el **propiedades** ventana que ha cambiado la selección. El **propiedades** ventana, a continuación, utiliza los objetos en <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para determinar si se han producido uno o varios, y cuáles son las selecciones del objeto real.  
  
     Si especifica una selección múltiple, el **propiedades** ventana busca la intersección entre las propiedades comunes para los objetos. Si especifica una selección de objetos único, el **propiedades** ventana muestra todas las propiedades para el objeto.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de extensión](../extensibility/internals/extending-properties.md)   
 [Páginas de propiedades](../extensibility/internals/property-pages.md)