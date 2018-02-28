---
title: El color de los editores personalizados sintaxis | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8c40538b34c23e88b2c680db170b9d46b7b40f62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="syntax-coloring-in-custom-editors"></a>Sintaxis de color en los editores personalizados
Editores de Visual Studio SDK de entorno, incluidos el editor básico, use servicios de lenguaje para identificar elementos sintácticos específicos y mostrarlas con colores especificados para una vista de documento determinado.  
  
## <a name="colorization-requirements"></a>Requisitos de colores  
 Todos los editores de implementación aplicador de color de un servicio de lenguaje deben:  
  
1.  Usar un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para administrar el texto que se va a ser aparece con un color y un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para proporcionar una vista de documento del texto.  
  
2.  Obtener una interfaz a un servicio de lenguaje en particular consultando el proveedor de servicios de VSPackage con GUID de identificación del servicio de idiomas.  
  
3.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método del objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Este método asocia el servicio de lenguaje a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementación que el VSPackage que se usa para administrar el texto que se colorea.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso del Editor principal del aplicador de color de un servicio de lenguaje  
 Cuando un servicio de lenguaje con un aplicador de color se obtiene una instancia del editor de core, el análisis y la representación de texto mediante aplicador de color de un servicio de lenguaje se produce automáticamente sin requerir ninguna intervención por parte del usuario.  
  
 El IDE de manera transparente:  
  
-   Llama a la aplicador de color según sea necesario para analizar y analizar el texto al que se agregan o modifican en la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Garantiza que la presentación proporcionada por la vista de documento proporcionada por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementación se actualiza y se vuelve a dibujar utilizando la información devuelta por el aplicador de color.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso del Editor no es esencial del aplicador de color de un servicio de lenguaje  
 Instancias del editor no principal también pueden utilizar el servicio de colores de sintaxis de un servicio de lenguaje, pero explícitamente debe recuperar y aplicar aplicador de color del servicio y volver a dibujar sus vistas de documentos por sí mismos.  
  
 Para ello necesita un editor no es esencial para:  
  
1.  Obtener el objeto de aplicador de color de un servicio de lenguaje (que implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). El paquete de VS para ello mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en la interfaz del servicio de lenguaje.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para solicitar que un determinado intervalo de texto se colorea.  
  
     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método devuelve una matriz de valores, uno para cada letra del texto abarcan se colorea. También identifica el intervalo de texto como un tipo específico de elemento coloreable, como un comentario, la palabra clave o el tipo de datos.  
  
3.  Utilice la información de coloración devuelta por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para volver a dibujar y mostrar su texto.  
  
> [!NOTE]
>  Además de utilizar aplicador de color de un servicio de lenguaje, un VSPackage puede elegir usar el mecanismo de color de texto de uso general SDK de entorno de Visual Studio. Para obtener más información sobre este mecanismo, vea [utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Vea también  
 [Color de un servicio de lenguaje heredado sintaxis](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Color de la sintaxis de implementación](../extensibility/internals/implementing-syntax-coloring.md)   
 [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)