---
title: Colores de la sintaxis en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa3dcadfc7774766c0e76617ce133d2c30ba2aa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186323"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Colores de la sintaxis en un servicio de lenguaje heredado

Visual Studio usa un servicio de color para identificar elementos del lenguaje y mostrarlos con los colores especificados en un editor.

## <a name="colorizer-model"></a>Modelo de coloreador
 El servicio de lenguaje implementa la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, que a continuación la usan los editores. Esta implementación es un objeto independiente del servicio de lenguaje, tal como se muestra en la siguiente ilustración:

 ![Gráfico del aplicador de color SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> El servicio de color de sintaxis es independiente del mecanismo general de Visual Studio para colorear texto. Para obtener más información sobre el mecanismo de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] general que admite la coloración, vea [usar fuentes y colores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Además del coloreador, el servicio de lenguaje puede proporcionar elementos coloreables personalizados que utiliza el editor, anunciando que proporciona elementos coloreables personalizados. Puede hacerlo implementando la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> en el mismo objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Devuelve el número de elementos coloreables personalizados cuando el editor llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> y devuelve un elemento coloreable personalizado individual cuando el editor llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

 El método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> devuelve un objeto que implementa la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>. Si el servicio de lenguaje admite valores de color de 24 bits o alto, debe implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> en el mismo objeto que la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Cómo un VSPackage usa un coloreador de servicio de lenguaje

1. El VSPackage debe obtener el servicio de lenguaje adecuado, que requiere que el VSPackage del servicio de lenguaje haga lo siguiente:

    1. Use un objeto que implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para obtener el texto que se va a colorear.

         El texto se muestra normalmente mediante un objeto que implementa la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

    2. Obtenga el servicio de lenguaje consultando el proveedor de servicios del VSPackage para el GUID del servicio de lenguaje. Los servicios de idioma se identifican en el registro mediante la extensión de archivo.

    3. Asocie el servicio de lenguaje con el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> llamando a su método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>.

2. El VSPackage ahora puede obtener y usar el objeto de coloreador como se indica a continuación:

    > [!NOTE]
    > Los VSPackages que usan el editor principal no tienen que obtener explícitamente los objetos de coloreador del servicio de lenguaje. En cuanto una instancia del editor principal obtiene un servicio de lenguaje adecuado, realiza todas las tareas de color que se muestran aquí.

    1. Obtenga el objeto de coloreador del servicio de lenguaje, que implementa las interfaces <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>, llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> en el objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> del servicio de lenguaje.

    2. Llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para obtener la información del coloreador para un intervalo de texto determinado.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> devuelve una matriz de valores, uno por cada carácter del intervalo de texto que se va a colorear. Los valores son índices en una lista de elementos coloreables que es la lista de elementos coloreables predeterminada mantenida por el editor principal o una lista de elementos coloreables personalizados mantenida por el propio servicio de lenguaje.

    3. Utilice la información de color devuelta por el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para mostrar el texto seleccionado.

> [!NOTE]
> Además de usar un coloreador de servicio de lenguaje, un VSPackage también puede usar el mecanismo de color de texto de Visual Studio de uso general. Para obtener más información sobre este mecanismo, vea [usar fuentes y colores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>En esta sección
- [Implementación de colores de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)

 Describe cómo un editor tiene acceso al color de la sintaxis de un servicio de lenguaje y qué debe implementar el servicio de lenguaje para admitir el color de la sintaxis.

- [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Muestra cómo usar elementos coloreables integrados del servicio de lenguaje.

- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)

 Describe cómo implementar elementos coloreables personalizados.