---
title: Obtener acceso a las capas de texto mediante la API heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d21b31940f1e1ebca767b9d3f0cf5ab802181bda
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Obtener acceso a las capas de texto mediante la API heredado
Normalmente, una capa de texto encapsula algún aspecto del diseño de texto. Por ejemplo, una capa de "una función a la vez" oculta el texto antes y después de una función que contiene el símbolo de intercalación (punto de inserción de texto).  
  
 Una capa de texto se encuentra entre un búfer y una vista, y modifica la forma en que la vista ve el contenido del búfer.  
  
## <a name="text-layer-information"></a>Información de la capa de texto  
 En la lista siguiente describe cómo funcionan las capas de texto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   El texto en una capa de texto puede ser complementado con marcadores y colorear la sintaxis.  
  
-   Actualmente no se puede implementar sus propia capas.  
  
-   Expone una capa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, que se deriva de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. El propio búfer de texto también se implementa como una capa, lo que permite una vista tratar de manera polimórfica con las capas subyacentes.  
  
-   Puede haber cualquier número de niveles entre la vista y el búfer. Cada capa sólo afecta a la capa inferior, y se ocupa de la vista en gran medida de la capa de nivel superior. (La vista tiene cierta información sobre el búfer).  
  
-   Una capa puede afectar únicamente las capas que están por debajo de él. No afectará a las capas superiores más allá de eventos estándar que se origina.  
  
-   En el editor, texto oculto, texto sintética y ajuste de línea se implementan como capas. Puede implementar texto oculto y sintético sin interactuar directamente con las capas. Para obtener más información, consulte [esquematización en un servicio de lenguaje heredado](../extensibility/internals/outlining-in-a-legacy-language-service.md) y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Cada capa de texto tiene su propio sistema de coordenadas local que se expone a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaz. La capa de ajuste de línea, por ejemplo, puede contener dos líneas y el búfer de texto subyacente podría contener una única línea.  
  
-   La vista se comunica con capas a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaz. Utilice esta interfaz para reconciliar las coordenadas de la vista con las coordenadas de búfer.  
  
-   Cualquiera de las capas, como la capa de texto sintéticos que se origina el texto debe proporcionar una implementación local de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Además <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, debe implementar una capa de texto <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y activar los eventos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Sintaxis de color en los editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Uso de marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizar menús y controles de Editor mediante la API heredado](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)