---
title: "Obtener acceso a las capas de texto mediante la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados: capas de texto"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Obtener acceso a las capas de texto mediante la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una capa de texto encapsula normalmente algún aspecto de la apariencia de diseño de texto.  Por ejemplo, oculta de un nivel de “función\-en\-uno\-Tiempo” texto antes y después de una función que contiene el símbolo de intercalación \(punto de inserción de texto\).  
  
 Una capa de texto se encuentra entre un búfer y una vista, y modifica la manera en que la vista vea el contenido del búfer.  
  
## información de la capa de texto  
 la lista siguiente describe cómo las capas de texto funcionan en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   El texto en una capa de texto se puede decorar con el color y marcadores de sintaxis.  
  
-   No puede implementar actualmente dispone los niveles.  
  
-   un nivel expone <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, que es derivado de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>.  El búfer propia de texto también se implementa como una capa, que permite a una vista para tratar polymorphically de los niveles subyacentes.  
  
-   Cualquier número de niveles puede mentir entre la vista y el búfer.  Cada capa se ocupa solo de nivel inferior, y la vista se ocupa en gran medida de nivel superior.  \(La vista se tiene alguna información sobre el búfer\).  
  
-   Una capa puede afectar solo los niveles situados por debajo de.  No puede afectar a los niveles superiores más allá de provoque eventos estándar.  
  
-   en el editor, el texto oculto, el texto sintetizado, y el ajuste de línea se implementan como niveles.  Puede implementar el texto oculto y sintetizado sin interactuar directamente con niveles.  Para obtener más información, vea [Esquematización en un servicio de lenguaje heredado](../extensibility/internals/outlining-in-a-legacy-language-service.md) y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Cada nivel de texto tiene su propio sistema de coordenadas local que se expone a través de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> .  El nivel de ajuste de línea, por ejemplo, podría contener dos líneas mientras el búfer de texto subyacente puede contener sólo una línea.  
  
-   La vista se comunica con los niveles a través de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> .  Utilice esta interfaz para reconciliar coordenadas de vista con coordenadas del búfer.  
  
-   No superpuestas como la capa de texto sintetizada que se origina el texto debe proporcionar una implementación local de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Además de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, una capa de texto debe implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y desencadenar los eventos de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> .  
  
## Vea también  
 [Colores en los editores personalizados de sintaxis](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizar menús y controles de Editor utilizando la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)