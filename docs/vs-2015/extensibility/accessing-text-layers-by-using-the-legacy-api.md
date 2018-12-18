---
title: Obtener acceso a las capas de texto mediante la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5eb9d92e3604224f3806cf64f2dd8d4529e8d01
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729076"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Obtener acceso a las capas de texto mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una capa de texto suele encapsula algún aspecto del diseño de texto. Por ejemplo, una capa de "una función de una vez" oculta el texto antes y después de una función que contiene el símbolo de intercalación (punto de inserción de texto).  
  
 Una capa de texto se encuentra entre un búfer y una vista, y modifica la manera en que la vista ve el contenido del búfer.  
  
## <a name="text-layer-information"></a>Información de la capa de texto  
 La lista siguiente describe cómo funcionan las capas de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
-   Puede adornar el texto en una capa de texto con marcadores y colorear la sintaxis.  
  
-   Actualmente no se puede implementar sus propios niveles.  
  
-   Expone una capa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, que se deriva de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. El propio búfer de texto también se implementa como una capa, lo que permite una vista tratar de manera polimórfica con las capas subyacentes.  
  
-   Puede haber cualquier número de capas entre la vista y el búfer. Cada capa sólo afecta a la capa debajo de él, y la vista que se trata en gran medida con la capa superior. (La vista tiene cierta información sobre el búfer).  
  
-   Una capa puede afectar a únicamente las capas que están debajo de él. No afectan a las capas por encima de él más allá de que se origina eventos estándar.  
  
-   En el editor de texto oculto texto sintético y ajuste de línea se implementan como capas. Puede implementar el texto oculto y sintético sin interactuar directamente con las capas. Para obtener más información, consulte [esquematización en un servicio de lenguaje heredado](../extensibility/internals/outlining-in-a-legacy-language-service.md) y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Cada capa de texto tiene su propio sistema de coordenadas local que se expone a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaz. La capa de ajuste de línea, por ejemplo, podría contener dos líneas mientras que el búfer de texto subyacente podría contener una única línea.  
  
-   La vista se comunica con capas a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaz. Utilice esta interfaz para conciliar las coordenadas de la vista con las coordenadas de búfer.  
  
-   Cualquiera de capas, como la capa de texto sintético que origina texto debe proporcionar una implementación local de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Además <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, debe implementar una capa de texto <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y activar los eventos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Colores de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalización de los controles y los menús del editor mediante la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)

