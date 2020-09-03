---
title: Acceso a capas de texto mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148022"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Acceso a las capas de texto mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente, un nivel de texto encapsula algún aspecto del diseño del texto. Por ejemplo, una capa de "función a hora" oculta el texto antes y después de una función que contiene el símbolo de intercalación (punto de inserción de texto).  
  
 Una capa de texto reside entre un búfer y una vista, y modifica el modo en que la vista ve el contenido del búfer.  
  
## <a name="text-layer-information"></a>Información de la capa de texto  
 En la siguiente lista se describe cómo funcionan las capas de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- El texto de una capa de texto se puede adornar con colores y marcadores de sintaxis.  
  
- Actualmente no puede implementar sus propias capas.  
  
- Una capa expone <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , que se deriva de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . El propio búfer de texto también se implementa como una capa, lo que permite que una vista se trate polimórficamente con capas subyacentes.  
  
- Puede haber cualquier número de capas entre la vista y el búfer. Cada capa solo trata el nivel que se encuentra debajo y la vista se centra en gran medida en la capa de nivel superior. (La vista tiene información sobre el búfer).  
  
- Una capa solo puede afectar a las capas que están debajo. No puede afectar a las capas situadas más allá de los eventos estándar de origen.  
  
- En el editor, el texto oculto, el texto sintético y el ajuste de palabras se implementan como capas. Puede implementar texto oculto y sintético sin interactuar directamente con las capas. Para obtener más información, vea [esquematización en un servicio de lenguaje heredado](../extensibility/internals/outlining-in-a-legacy-language-service.md) y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Cada capa de texto tiene su propio sistema de coordenadas local que se expone a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaz. Por ejemplo, la capa de ajuste de línea puede contener dos líneas, mientras que el búfer de texto subyacente podría contener una sola línea.  
  
- La vista se comunica con las capas a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaz. Utilice esta interfaz para conciliar las coordenadas de la vista con las coordenadas del búfer.  
  
- Cualquier capa como el nivel de texto sintético que origina el texto debe proporcionar una implementación local de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Además <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , una capa de texto debe implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y desencadenar los eventos en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaz.  
  
## <a name="see-also"></a>Consulte también  
 [Colores de la sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalización de los controles y los menús del editor mediante la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
