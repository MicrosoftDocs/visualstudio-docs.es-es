---
title: Coloración de sintaxis en editores personalizados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699331"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colores de sintaxis en editores personalizados
Los editores del SDK de Visual Studio Environment, incluido el editor principal, usan servicios de lenguaje para identificar elementos sintácticos específicos y mostrarlos con colores especificados para una vista de documento determinada.

## <a name="colorization-requirements"></a>Requisitos de coloración
 Todos los editores que implementan el colorante de un servicio de lenguaje deben:

1. Utilice un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto que se implementa para administrar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> el texto que se va a colorear y un objeto que se va a implementar para proporcionar una vista de documento del texto.

2. Obtener una interfaz para un servicio de lenguaje determinado consultando el proveedor de servicios de VSPackage mediante el GUID de identificación del servicio de idiomas.

3. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> al método del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>objeto que implementa . Este método asocia el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> servicio de lenguaje con la implementación que el VSPackage usa para administrar el texto que se va a colorear.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Core Editor Uso del Colorizador de un Servicio de Lenguaje
 Cuando un servicio de lenguaje con un colorante se obtiene mediante una instancia del editor principal, el análisis y la representación de texto por el colorizador de un servicio de lenguaje se produce automáticamente sin necesidad de intervención adicional por su parte.

 El IDE de forma transparente:

- Llama al colorante según sea necesario para analizar y analizar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>el texto a medida que se agrega o modifica en la implementación de .

- Garantiza que la visualización proporcionada por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> la vista de documento proporcionada por la implementación se actualiza y se vuelve a pintar con la información devuelta por el colorante.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso no básico del editor de un servicio de lenguaje colorante
 Las instancias de editor no principales también pueden usar el servicio de coloración de sintaxis de un servicio de lenguaje, pero deben recuperar y aplicar explícitamente el colorante del servicio y volver a pintar sus propias vistas de documento.

 Para ello, un editor no principal debe:

1. Obtener el objeto colorizador de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> servicio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>de lenguaje (que implementa y ). El VSPackage hace esto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> mediante una llamada al método en la interfaz del servicio de lenguaje.

2. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> al método para solicitar que se coloree un intervalo determinado de texto.

     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método devuelve una matriz de valores, uno para cada letra en el intervalo de texto que se está coloreando. También identifica el intervalo de texto como un tipo determinado de elemento coloreable, como un comentario, una palabra clave o un tipo de datos.

3. Utilice la información de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> coloración devuelta para volver a pintar y mostrar su texto.

> [!NOTE]
> Además de usar el colorizador de un servicio de lenguaje, un VSPackage puede elegir usar el mecanismo de coloración de texto del SDK de entorno de Visual Studio de uso general. Para obtener más información sobre este mecanismo, consulte Uso de [fuentes y colores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Vea también

- [Colores de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementación de colores de la sintaxis](../extensibility/internals/implementing-syntax-coloring.md)
- [Uso de elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)
