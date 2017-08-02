---
title: "Colores en un servicio de lenguaje heredado de sintaxis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colorear la sintaxis"
  - "Servicios de lenguaje, colorear la sintaxis"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Colores en un servicio de lenguaje heredado de sintaxis
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza un servicio de color para identificar los elementos del lenguaje y mostrarlos con los colores especificados en un editor.  
  
## modelo de Colorizer  
 El servicio de lenguaje implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> , que se usan los editores.  Esta implementación es un objeto independiente del servicio de lenguaje, como se muestra en la ilustración siguiente.  
  
 ![Gráfico del aplicador de color SVC](~/extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modelo simple de colorizer  
  
> [!NOTE]
>  El servicio de colorear la sintaxis es independiente del mecanismo general de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para colorear el texto.  Para obtener más información sobre el mecanismo general de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] que admite color, vea [Utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md).  
  
 Además de colorizer, el servicio de lenguaje puede proporcionar los elementos colorear personalizados utilizados por el editor haciendo anunciar que agrupa los elementos colorear personalizados de fuentes.  Esto se puede hacer implementando la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> en el mismo objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  Devuelve el número de elementos colorear personalizados cuando el editor llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> , y devuelve un elemento coloreable personalizado individual cuando el editor llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
 El método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> devuelve un objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  Si el servicio de lenguaje admite 24 bits o de color de gran densidad, debe implementar la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> en el mismo objeto que la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  
  
## cómo un VSPackage utiliza un lenguaje Service Colorizer  
  
1.  El Paquete debe obtener el servicio de lenguaje adecuado, que requiere el servicio de lenguaje VSPackage hacer lo siguiente:  
  
    1.  utilice un objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para obtener el texto que se coloreará.  
  
         El texto se muestra normalmente mediante un objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
    2.  Obtiene el servicio de lenguaje consultando el proveedor de servicios de VSPackage para el servicio de lenguaje GUID.  Los servicios se identifican en el registro mediante la extensión de archivo.  
  
    3.  Asociar el servicio de lenguaje con <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> llamando a su método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> .  
  
2.  El Paquete puede recopilar y utilizar el objeto de colorizer como sigue:  
  
    > [!NOTE]
    >  VSPackages que utiliza el editor básico no tiene que obtener objetos de colorizer de un servicio de lenguaje explícitamente.  Tan pronto como una instancia del editor básico obtenga un servicio de lenguaje adecuado, realiza todas las tareas del color que aquí.  
  
    1.  Obtiene el objeto de colorizer del servicio de lenguaje, que implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, e interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> en el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> del servicio de lenguaje.  
  
    2.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para obtener la información de colorizer para un intervalo de texto determinada.  
  
         el<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> devuelve una matriz de valores, uno por cada carácter en el intervalo de texto que es coloreada.  Los valores son índices en una lista de elementos plausible que es la lista de elementos plausible predeterminada mantenida por el editor básico o una lista de elementos coloreable personalizado mantenida por el servicio de lenguaje propio.  
  
    3.  Utilice la información del color devuelta por el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para mostrar el texto seleccionado.  
  
> [!NOTE]
>  Además de un colorizer del servicio de lenguaje, un Paquete puede usar el mecanismo de uso general de color del texto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Para obtener más información sobre este mecanismo, vea [Utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md).  
  
## En esta sección  
 [Implementación de colores de sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)  
 Explica cómo un editor tiene acceso a un color de la sintaxis del servicio de lenguaje y lo que debe implementar el servicio de lenguaje para admitir el colorear la sintaxis.  
  
 [Cómo: usar elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Muestra cómo utilizar elementos colorear integrados del servicio de lenguaje.  
  
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)  
 Describe cómo implementar elementos colorear personalizados.  
  
## Vea también  
 [Utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md)