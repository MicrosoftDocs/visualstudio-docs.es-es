---
title: Colores de sintaxis en editores personalizados | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f82902ebcb82ea311617d3a7a767c5dabaedd311
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886655"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colores de sintaxis en editores personalizados
Editores visuales de SDK de entorno de Studio, incluido el editor principal, usan servicios de lenguaje para identificar elementos sintácticos específicos y mostrarlas con los colores especificados para obtener una vista de documento determinado.

## <a name="colorization-requirements"></a>Requisitos de coloración
 Todos los editores de implementación Coloreador de un servicio de lenguaje deben:

1.  Usar un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para administrar el texto que se coloreará y un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para proporcionar una vista de documento del texto.

2.  Obtener una interfaz a un servicio de lenguaje determinado mediante la consulta de proveedor de servicios de VSPackage mediante el GUID que identifica del servicio idiomas.

3.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método del objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Este método asocia el servicio de lenguaje con el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementación de que el paquete VSPackage que se usa para administrar el texto que se coloreará.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso del Editor principal de Coloreador de un servicio de lenguaje
 Cuando se obtiene un servicio de lenguaje con un Coloreador por una instancia de que el editor básico, el análisis y la representación de texto por el Coloreador de un servicio de lenguaje se produce automáticamente sin necesidad de ninguna intervención por parte del usuario.

 El IDE de manera transparente:

-   Llama el Coloreador según sea necesario para analizar y analizar texto a medida que se agrega o modifica en la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Garantiza que la presentación proporcionada por la vista de documento proporcionada por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementación se actualice y vuelva a dibujar utilizando la información devuelta por el Coloreador.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso del Editor no esenciales de Coloreador de un servicio de lenguaje
 Las instancias del editor de núcleo no también pueden usar el servicio de coloración de sintaxis de un servicio de lenguaje, pero explícitamente debe recuperar y aplicar el Coloreador del servicio y volver a dibujar sus propias vistas de documento.

 Para ello, un editor de núcleo no debe:

1.  Obtener el objeto de Coloreador de un servicio de lenguaje (que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). El VSPackage hace una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en la interfaz del servicio de lenguaje.

2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para solicitar que un determinado intervalo de texto se coloreará.

     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método devuelve una matriz de valores, uno para cada letra en el texto del intervalo se colorea. También identifica el intervalo de texto como un tipo concreto de elemento coloreable, como un comentario, la palabra clave o el tipo de datos.

3.  Use la información de coloración devuelta por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para volver a dibujar y mostrar su texto.

> [!NOTE]
> Además de utilizar Coloreador de un servicio de lenguaje, un VSPackage puede elegir usar el mecanismo de color de texto de entorno de Visual Studio SDK uso general. Para obtener más información sobre este mecanismo, vea [utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Vea también

- [Colores de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementación de colores de la sintaxis](../extensibility/internals/implementing-syntax-coloring.md)
- [Cómo: Usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)