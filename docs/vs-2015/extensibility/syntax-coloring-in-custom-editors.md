---
title: Colores de sintaxis en editores personalizados | Documentos de Microsoft
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
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62fd407bdb377c490d26287701cf989a64484773
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305700"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colores de sintaxis en editores personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 Para hacer esto requiere un editor no esenciales para:  
  
1.  Obtener el objeto de Coloreador de un servicio de lenguaje (que implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). El VSPackage hace una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en la interfaz del servicio de lenguaje.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para solicitar que un determinado intervalo de texto se coloreará.  
  
     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método devuelve una matriz de valores, uno para cada letra en el texto del intervalo se colorea. También identifica el intervalo de texto como un tipo concreto de elemento coloreable, como un comentario, la palabra clave o el tipo de datos.  
  
3.  Use la información de coloración devuelta por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para volver a dibujar y mostrar su texto.  
  
> [!NOTE]
>  Además de utilizar Coloreador de un servicio de lenguaje, un VSPackage puede elegir usar el mecanismo de color de texto de entorno de Visual Studio SDK uso general. Para obtener más información sobre este mecanismo, vea [utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Vea también  
 [Colores de sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementación de colores de sintaxis](../extensibility/internals/implementing-syntax-coloring.md)   
 [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)

