---
title: Obtener acceso a las capas de texto mediante la API heredada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d7c47bea12dc4057cfb106f269532601e291310
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313653"
---
# <a name="access-text-layers-by-using-the-legacy-api"></a>Niveles de acceso a texto mediante el uso de la API heredada
Una capa de texto suele encapsula algún aspecto del diseño de texto. Por ejemplo, una capa de "una función de una vez" oculta el texto antes y después de una función que contiene el símbolo de intercalación (punto de inserción de texto).

 Una capa de texto se encuentra entre un búfer y una vista, y modifica la manera en que la vista ve el contenido del búfer.

## <a name="text-layer-information"></a>Información de la capa de texto
 La lista siguiente describe cómo funcionan las capas de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:

- Puede adornar el texto en una capa de texto con marcadores y colorear la sintaxis.

- Actualmente no se puede implementar sus propios niveles.

- Expone una capa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, que se deriva de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. El propio búfer de texto también se implementa como una capa, lo que permite una vista tratar de manera polimórfica con las capas subyacentes.

- Puede haber cualquier número de capas entre la vista y el búfer. Cada capa sólo afecta a la capa debajo de él, y la vista que se trata en gran medida con la capa superior. (La vista tiene cierta información sobre el búfer).

- Una capa puede afectar a únicamente las capas que están debajo de él. No afectan a las capas por encima de él más allá de que se origina eventos estándar.

- En el editor de texto oculto texto sintético y ajuste de línea se implementan como capas. Puede implementar el texto oculto y sintético sin interactuar directamente con las capas. Para obtener más información, consulte [esquematización en un servicio de lenguaje heredado](../extensibility/internals/outlining-in-a-legacy-language-service.md) y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.

- Cada capa de texto tiene su propio sistema de coordenadas local que se expone a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaz. La capa de ajuste de línea, por ejemplo, podría contener dos líneas mientras que el búfer de texto subyacente podría contener una única línea.

- La vista se comunica con capas a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaz. Utilice esta interfaz para conciliar las coordenadas de la vista con las coordenadas de búfer.

- Cualquiera de capas, como la capa de texto sintético que origina texto debe proporcionar una implementación local de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.

- Además <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, debe implementar una capa de texto <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y activar los eventos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaz.

## <a name="see-also"></a>Vea también
- [Colores de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)
- [Utilice marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)
- [Personalizar menús y controles de editor mediante el uso de la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)