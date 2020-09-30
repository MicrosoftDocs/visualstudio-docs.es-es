---
title: Colores de la sintaxis en un servicio de lenguaje heredado | Microsoft Docs
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
ms.openlocfilehash: 5d3b125737162146af954ad8561eb41e5ee8f2e8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584534"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colores de la sintaxis en un servicio de lenguaje heredado

Visual Studio usa un servicio de color para identificar elementos del lenguaje y mostrarlos con los colores especificados en un editor.

## <a name="colorizer-model"></a>Modelo de coloreador
 El servicio de lenguaje implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz, que se usa a continuación por los editores. Esta implementación es un objeto independiente del servicio de lenguaje, tal como se muestra en la siguiente ilustración:

 ![Gráfico del aplicador de color SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> El servicio de color de sintaxis es independiente del mecanismo general de Visual Studio para colorear texto. Para obtener más información sobre el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mecanismo general que admite la coloración, vea [usar fuentes y colores](../../vs-2015/extensibility/using-fonts-and-colors.md?view=vs-2015&preserve-view=true).

 Además del coloreador, el servicio de lenguaje puede proporcionar elementos coloreables personalizados que utiliza el editor, anunciando que proporciona elementos coloreables personalizados. Puede hacerlo implementando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaz en el mismo objeto que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz. Devuelve el número de elementos coloreables personalizados cuando el editor llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método y devuelve un elemento coloreable personalizado individual cuando el editor llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método.

 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método devuelve un objeto que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaz. Si el servicio de lenguaje admite valores de color de 24 bits o alto, debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz en el mismo objeto que la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaz.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Cómo un VSPackage usa un coloreador de servicio de lenguaje

1. El VSPackage debe obtener el servicio de lenguaje adecuado, que requiere que el VSPackage del servicio de lenguaje haga lo siguiente:

    1. Use un objeto que implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz para obtener el texto que se va a colorear.

         El texto se muestra normalmente mediante un objeto que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.

    2. Obtenga el servicio de lenguaje consultando el proveedor de servicios del VSPackage para el GUID del servicio de lenguaje. Los servicios de idioma se identifican en el registro mediante la extensión de archivo.

    3. Asocie el servicio de lenguaje a llamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> a su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método.

2. El VSPackage ahora puede obtener y usar el objeto de coloreador como se indica a continuación:

    > [!NOTE]
    > Los VSPackages que usan el editor principal no tienen que obtener explícitamente los objetos de coloreador del servicio de lenguaje. En cuanto una instancia del editor principal obtiene un servicio de lenguaje adecuado, realiza todas las tareas de color que se muestran aquí.

    1. Obtenga el objeto de coloreador del servicio de lenguaje, que implementa las <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaces, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en el objeto del servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

    2. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para obtener la información del coloreador para un intervalo de texto determinado.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Devuelve una matriz de valores, uno por cada carácter del intervalo de texto que se va a colorear. Los valores son índices en una lista de elementos coloreables que es la lista de elementos coloreables predeterminada mantenida por el editor principal o una lista de elementos coloreables personalizados mantenida por el propio servicio de lenguaje.

    3. Utilice la información de color devuelta por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para mostrar el texto seleccionado.

> [!NOTE]
> Además de usar un coloreador de servicio de lenguaje, un VSPackage también puede usar el mecanismo de color de texto de Visual Studio de uso general. Para obtener más información sobre este mecanismo, vea [usar fuentes y colores](../../vs-2015/extensibility/using-fonts-and-colors.md?view=vs-2015&preserve-view=true).

## <a name="in-this-section"></a>En esta sección
- [Implementación de colores de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)

 Describe cómo un editor tiene acceso al color de la sintaxis de un servicio de lenguaje y qué debe implementar el servicio de lenguaje para admitir el color de la sintaxis.

- [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Muestra cómo usar elementos coloreables integrados del servicio de lenguaje.

- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)

 Describe cómo implementar elementos coloreables personalizados.