---
title: Colores de sintaxis en un servicio de lenguaje heredado | Documentos de Microsoft
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
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f57d4c8b3c606fa5f954755d6a7f07c2ab00a89
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253848"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colores de la sintaxis en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utiliza un servicio de color para identificar los elementos del lenguaje y mostrarlas con los colores especificados en un editor.  
  
## <a name="colorizer-model"></a>Modelo de Coloreador  
 El servicio de lenguaje implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz, que se usa, a continuación, los editores. Esta implementación es un objeto independiente desde el servicio de lenguaje, como se muestra en la siguiente ilustración.  
  
 ![Gráfico del aplicador de color SVC](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modelo de Coloreador simple  
  
> [!NOTE]
>  El servicio de color de sintaxis es independiente del general [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mecanismo para colorear el texto. Para obtener más información sobre el general [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] mecanismo que admiten colorear, consulte [utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md).  
  
 Además el Coloreador, el servicio de lenguaje puede proporcionar elementos coloreables personalizados son utilizados por el editor, que proporciona elementos coloreables personalizados de publicidad. Puede hacerlo mediante la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaz en el mismo objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz. Devuelve el número de elementos coloreables personalizados cuando el editor llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método y devuelve un elemento coloreable personalizado individual cuando se llama el editor de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método.  
  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método devuelve un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaz. Si el servicio de lenguaje es compatible con los valores de color de 24 bits o alta, debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz en el mismo objeto que el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaz.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Cómo un paquete VSPackage usa un Coloreador del servicio de lenguaje  
  
1.  El VSPackage debe obtener el servicio de idioma correspondiente, lo que requiere el servicio de lenguaje VSPackage para hacer lo siguiente:  
  
    1.  Usar un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz para obtener el texto que se coloreará.  
  
         Texto se muestra normalmente mediante un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.  
  
    2.  Obtener el servicio de lenguaje si el proveedor de servicios de VSPackage para el GUID del servicio de lenguaje de consulta. Servicios de lenguaje se identifican en el registro mediante la extensión de archivo.  
  
    3.  Asociar el servicio de lenguaje con el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> mediante una llamada a su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método.  
  
2.  El VSPackage ahora puede obtener y usar el objeto de Coloreador como sigue:  
  
    > [!NOTE]
    >  Para obtener un lenguaje explícitamente los objetos de Coloreador del servicio no tiene VSPackages que use el editor básico. Tan pronto como una instancia del editor de núcleo Obtiene un servicio de lenguaje que corresponda, realiza todas las tareas de colores que se muestra aquí.  
  
    1.  Obtener el objeto de Coloreador del servicio de lenguaje, que implementa el `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfaces, mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en el servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.  
  
    2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para obtener la información de Coloreador para un determinado intervalo de texto.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Devuelve una matriz de valores, uno para cada carácter en el intervalo de texto se colorea. Los valores son índices en una lista de elementos coloreables que es la lista de elementos coloreables predeterminada mantenida por el editor principal o una lista de elemento coloreable personalizado mantenida por el propio servicio de lenguaje.  
  
    3.  Utilice la información de coloración devuelta por la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para mostrar el texto seleccionado.  
  
> [!NOTE]
>  Además de utilizar un Coloreador del servicio de lenguaje, un VSPackage también puede usar el uso general [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mecanismo de color de texto. Para obtener más información sobre este mecanismo, vea [utilizar fuentes y colores](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de colores de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)  
 Describe cómo accede a un editor de colores de sintaxis de un servicio de lenguaje y lo que el servicio de lenguaje debe implementar para admitir la sintaxis de color.  
  
 [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Muestra cómo utilizar elementos coloreables integrados desde el servicio de lenguaje.  
  
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)  
 Describe cómo implementar elementos coloreables personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Uso de fuentes y colores](../../extensibility/using-fonts-and-colors.md)

