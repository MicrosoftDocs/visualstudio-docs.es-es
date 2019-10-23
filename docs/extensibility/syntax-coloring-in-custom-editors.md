---
title: Colores de la sintaxis en editores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302f463d93776d17be0251e6194375c15adc19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718767"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colores de sintaxis en editores personalizados
Los editores del SDK del entorno de Visual Studio, incluido el editor principal, usan servicios de lenguaje para identificar elementos sintácticos específicos y mostrarlos con los colores especificados para una vista de documento determinada.

## <a name="colorization-requirements"></a>Requisitos de coloración
 Todos los editores que implementan el coloreador de un servicio de lenguaje deben:

1. Use un objeto que implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para administrar el texto que se va a colorear y un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para proporcionar una vista de documento del texto.

2. Obtener una interfaz para un servicio de lenguaje determinado consultando el proveedor de servicios del VSPackage mediante el GUID de identificación del servicio de lenguajes.

3. Llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> del objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Este método asocia el servicio de lenguaje a la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que el VSPackage utiliza para administrar el texto que se va a colorear.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso del editor principal del coloreador de un servicio de lenguaje
 Cuando un servicio de lenguaje con un coloreador se obtiene mediante una instancia del editor principal, el análisis y la representación de texto por parte del coloreador de un servicio de lenguaje se produce automáticamente sin necesidad de ninguna intervención adicional.

 El IDE de forma transparente:

- Llama al coloreador según sea necesario para analizar y analizar el texto a medida que se agrega o modifica en la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Garantiza que la presentación proporcionada por la vista de documento proporcionada por la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> se actualiza y se vuelve a dibujar con la información devuelta por el coloreador.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso del editor no principal del coloreador de un servicio de lenguaje
 Las instancias de editor que no son de núcleo también pueden usar el servicio de coloración de sintaxis de un servicio de lenguaje, pero deben recuperar y aplicar explícitamente el coloreador del servicio y volver a pintar sus propias vistas de documento.

 Para ello, un editor que no sea de núcleo debe:

1. Obtenga un objeto de coloreador del servicio de lenguaje (que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Para ello, el VSPackage llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> de la interfaz del servicio de lenguaje.

2. Llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para solicitar que se colorea un intervalo de texto determinado.

     El método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> devuelve una matriz de valores, uno para cada letra del intervalo de texto que se va a colorear. También identifica el intervalo de texto como un tipo determinado de elemento coloreable, como un comentario, una palabra clave o un tipo de datos.

3. Utilice la información de color devuelta por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para volver a dibujar y mostrar su texto.

> [!NOTE]
> Además de usar el coloreador de un servicio de lenguaje, un VSPackage puede elegir usar el mecanismo de color de texto del SDK de entorno de Visual Studio de uso general. Para obtener más información sobre este mecanismo, vea [usar fuentes y colores](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Vea también

- [Colores de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementación de colores de la sintaxis](../extensibility/internals/implementing-syntax-coloring.md)
- [Uso de elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)