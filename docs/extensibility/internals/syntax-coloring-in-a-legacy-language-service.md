---
title: Coloreación de sintaxis en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704757"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colores de la sintaxis en un servicio de lenguaje heredado

Visual Studio usa un servicio de colorear para identificar elementos del lenguaje y mostrarlos con los colores especificados en un editor.

## <a name="colorizer-model"></a>Modelo de colorante
 El servicio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> lenguaje implementa la interfaz, que luego usa los editores. Esta implementación es un objeto independiente del servicio de lenguaje, como se muestra en la siguiente ilustración:

 ![Gráfico del aplicador de color SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> El servicio de coloración de sintaxis es independiente del mecanismo general de Visual Studio para colorear texto. Para obtener más [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] información sobre el mecanismo general que admite la coloración, consulte Uso de [fuentes y colores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Además del colorante, el servicio de lenguaje puede proporcionar elementos coloreables personalizados que son utilizados por el editor, mediante la publicidad de que proporciona artículos coloreables personalizados. Puede hacerlo implementando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> la interfaz en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> mismo objeto que implementa la interfaz. Devuelve el número de elementos coloreables personalizados cuando el editor llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> y devuelve un elemento coloreable personalizado individual cuando el editor llama al método.

 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método devuelve un objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> que implementa la interfaz. Si el servicio de lenguaje admite valores de color <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> de 24 bits <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> o altos, debe implementar la interfaz en el mismo objeto que la interfaz.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Cómo un VSPackage utiliza un colorante de servicio de lenguaje

1. El VSPackage debe obtener el servicio de lenguaje adecuado, que requiere el servicio de lenguaje VSPackage para hacer lo siguiente:

    1. Utilice un objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que implemente la interfaz para obtener el texto que se va a colorear.

         Normalmente, el texto se muestra mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> un objeto que implementa la interfaz.

    2. Obtenga el servicio de lenguaje consultando el proveedor de servicios de VSPackage para el GUID del servicio de lenguaje. Los servicios de idioma se identifican en el registro por extensión de archivo.

    3. Asocie el servicio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> con el mediante una llamada a su método.

2. El VSPackage ahora puede obtener y usar el objeto colorizer de la siguiente manera:

    > [!NOTE]
    > VSPackages que usan el editor principal no tienen que obtener explícitamente los objetos de colorizador de un servicio de lenguaje. Tan pronto como una instancia del editor principal obtiene un servicio de lenguaje adecuado, realiza todas las tareas de coloración que se muestran aquí.

    1. Obtener el objeto colorizador del servicio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>lenguaje, que implementa el , y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> las interfaces, mediante una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en el objeto del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> servicio de lenguaje.

    2. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> al método para obtener la información del colorante para un intervalo determinado de texto.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>devuelve una matriz de valores, uno para cada carácter del intervalo de texto que se está coloreando. Los valores son índices en una lista de elementos coloreable que es la lista de elementos coloreables predeterminada que mantiene el editor principal o una lista de elementos coloreable sin formato personalizada mantenida por el propio servicio de lenguaje.

    3. Utilice la información de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> coloración devuelta por el método para mostrar el texto seleccionado.

> [!NOTE]
> Además de usar un colorizador de servicio de lenguaje, un VSPackage también puede usar el mecanismo de color de texto de Visual Studio de uso general. Para obtener más información acerca de este mecanismo, consulte Uso de [fuentes y colores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>En esta sección
- [Implementación de colores de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)

 Describe cómo un editor tiene acceso a la coloración de sintaxis de un servicio de lenguaje y lo que el servicio de lenguaje debe implementar para admitir el color de sintaxis.

- [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Muestra cómo usar elementos coloreables integrados del servicio de lenguaje.

- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)

 Describe cómo implementar elementos coloreables personalizados.
