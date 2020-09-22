---
title: Colores de la sintaxis en editores personalizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0233873ba5d6ea2fca746f8e12f4bf693b79da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842971"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colores de sintaxis en editores personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los editores del SDK del entorno de Visual Studio, incluido el editor principal, usan servicios de lenguaje para identificar elementos sintácticos específicos y mostrarlos con los colores especificados para una vista de documento determinada.  
  
## <a name="colorization-requirements"></a>Requisitos de coloración  
 Todos los editores que implementan el coloreador de un servicio de lenguaje deben:  
  
1. Use un objeto que implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para administrar el texto que se va a colorear y un objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> que implementa para proporcionar una vista de documento del texto.  
  
2. Obtener una interfaz para un servicio de lenguaje determinado consultando el proveedor de servicios del VSPackage mediante el GUID de identificación del servicio de lenguajes.  
  
3. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método del objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Este método asocia el servicio de lenguaje a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementación que el VSPackage utiliza para administrar el texto que se va a colorear.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso del editor principal del coloreador de un servicio de lenguaje  
 Cuando un servicio de lenguaje con un coloreador se obtiene mediante una instancia del editor principal, el análisis y la representación de texto por parte del coloreador de un servicio de lenguaje se produce automáticamente sin necesidad de ninguna intervención adicional.  
  
 El IDE de forma transparente:  
  
- Llama al coloreador según sea necesario para analizar y analizar el texto a medida que se agrega o modifica en la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
- Garantiza que la presentación proporcionada por la vista de documento proporcionada por la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementación se actualiza y se vuelve a dibujar con la información devuelta por el coloreador.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso del editor no principal del coloreador de un servicio de lenguaje  
 Las instancias de editor que no son de núcleo también pueden usar el servicio de coloración de sintaxis de un servicio de lenguaje, pero deben recuperar y aplicar explícitamente el coloreador del servicio y volver a pintar sus propias vistas de documento.  
  
 Para ello, es necesario un editor que no sea de núcleo para:  
  
1. Obtenga un objeto de coloreador del servicio de lenguaje (que implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Para ello, el VSPackage llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en la interfaz del servicio de lenguaje.  
  
2. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para solicitar la coloración de un intervalo de texto determinado.  
  
     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método devuelve una matriz de valores, uno para cada letra del intervalo de texto que se va a colorear. También identifica el intervalo de texto como un tipo determinado de elemento coloreable, como un comentario, una palabra clave o un tipo de datos.  
  
3. Utilice la información de color devuelta por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para volver a dibujar y mostrar su texto.  
  
> [!NOTE]
> Además de usar el coloreador de un servicio de lenguaje, un VSPackage puede elegir usar el mecanismo de color de texto del SDK de entorno de Visual Studio de uso general. Para obtener más información sobre este mecanismo, vea [usar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Consulte también  
 [Color de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementar el color de la sintaxis](../extensibility/internals/implementing-syntax-coloring.md)   
 [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)
