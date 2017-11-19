---
title: El color de un servicio de lenguaje heredado sintaxis | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88af397feba9b06eabd73ec23dcf1204ebe755e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Color de un servicio de lenguaje heredado sintaxis
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utiliza un servicio de color para identificar los elementos del lenguaje y mostrarlas con los colores especificados en un editor.  
  
## <a name="colorizer-model"></a>Modelo de aplicador de color  
 El servicio de lenguaje implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz, que, a continuación, se usa el Editor. Esta implementación es un objeto independiente desde el servicio de lenguaje, como se muestra en la siguiente ilustración.  
  
 ![Gráfico del aplicador de color SVC](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modelo simple aplicador de color  
  
> [!NOTE]
>  El servicio de color de sintaxis es independiente de la ficha general [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo para colorear texto. Para obtener más información acerca de la ficha general [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mecanismo admitir colorear, consulte [utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md).  
  
 Además del aplicador de color, el servicio de lenguaje puede proporcionar elementos coloreables personalizados son utilizados por el editor, publicidad que proporciona elementos coloreables personalizados. Puede hacerlo mediante la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaz en el mismo objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz. Devuelve el número de elementos coloreables personalizados cuando el editor llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (método) y devuelve un elemento coloreable personalizado individual cuando se llama el editor de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método.  
  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método devuelve un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaz. Si el servicio de lenguaje es compatible con los valores de color de 24 bits o alta, debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz en el mismo objeto que la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaz.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Cómo un paquete VSPackage usa un aplicador de color del servicio de lenguaje  
  
1.  El paquete VSPackage debe obtener el servicio de idioma correspondiente, lo que requiere el servicio de lenguaje VSPackage para hacer lo siguiente:  
  
    1.  Usar un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz para obtener el texto que se colorea.  
  
         Texto se muestra normalmente mediante un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.  
  
    2.  Obtener el servicio de lenguaje consultando el proveedor de servicios de VSPackage para el GUID del servicio de lenguaje. Servicios de lenguaje se identifican en el registro por extensión de archivo.  
  
    3.  Asociar el servicio de lenguaje con el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> mediante una llamada a su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método.  
  
2.  El VSPackage ahora puede obtener y usar el objeto de aplicador de color como sigue:  
  
    > [!NOTE]
    >  VSPackages que use el editor básico no es necesario que obtener un idioma explícitamente objetos del aplicador de color del servicio. Tan pronto como una instancia del editor principal obtiene un servicio de lenguaje correspondiente, realiza todas las tareas de colores se muestra aquí.  
  
    1.  Obtener el objeto de aplicador de color del servicio de lenguaje, que implementa el `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfaces, mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en el servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.  
  
    2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para obtener la información del aplicador de color para un determinado intervalo de texto.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Devuelve una matriz de valores, uno para cada carácter en el intervalo de texto que se colorea. Los valores son índices en una lista de elemento coloreable es la lista de elemento coloreable predeterminada mantenida por el editor principal o una lista de elemento coloreable personalizado mantenida por el propio servicio de lenguaje.  
  
    3.  Use la información de colores devuelta por la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para mostrar el texto seleccionado.  
  
> [!NOTE]
>  Además de utilizar un aplicador de color del servicio de lenguaje, un VSPackage también puede utilizar el uso general [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo de color de texto. Para obtener más información sobre este mecanismo, vea [utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de colores de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)  
 Describe cómo un editor tiene acceso a un servicio de lenguaje colorear la sintaxis y qué el servicio de lenguaje debe implementar para admitir la sintaxis de color.  
  
 [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Muestra cómo utilizar elementos coloreables integrados desde el servicio de lenguaje.  
  
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)  
 Describe cómo implementar elementos coloreables personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md)