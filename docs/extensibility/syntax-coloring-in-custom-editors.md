---
title: "Colores en los editores personalizados de sintaxis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - colorear la sintaxis"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Colores en los editores personalizados de sintaxis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los editores de SDK del entorno de Visual Studio, incluido el editor básico, utilizan servicios para identificar elementos sintácticos específicos y mostrarlos con los colores especificados para una vista del documento determinada.  
  
## Requisitos del color  
 Todos los editores que implementan un colorizer del servicio de lenguaje debe:  
  
1.  Utilice un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para administrar el texto que se colorearán y un objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para proporcionar una vista del documento de texto.  
  
2.  Obtiene una interfaz a un servicio de lenguaje determinado consultando el proveedor de servicios de VSPackage utilizando el GUID del identificador del servicio de lenguaje.  
  
3.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> del objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  Este método asocia el servicio de lenguaje a la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que el Paquete utiliza para administrar el texto que debe ser coloreado.  
  
## Editor básico del uso de Colorizer de un Servicio de lenguaje  
 Cuando un servicio de con un colorizer se recopilan mediante una instancia del editor básico, el análisis y la representación de texto en un colorizer del servicio de lenguaje aparece automáticamente sin requerir ninguna otra intervención de la partición.  
  
 El IDE transparente:  
  
-   Llama al colorizer según sea necesario para analizar y analizar el texto cuando se agrega o se modifica en la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Garantiza que se actualicen y están a redibujar la pantalla proporcionada por la vista del documento proporcionada por la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> usando la información devuelta por el colorizer.  
  
## Editor no fundamental Uso de Colorizer de un Servicio de lenguaje  
 Las instancias no fundamentales del editor pueden utilizar un servicio de color de la sintaxis del servicio de lenguaje, pero deben recuperar explícitamente y aplicar el colorizer de servicio y vuelva a sus vistas de documento propios.  
  
 Para ello requiere un editor no fundamental:  
  
1.  Obtiene un objeto de colorizer de servicio de \(que implemente `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\).  El paquete VSPackage hacerlo llamando al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> en la interfaz del servicio de lenguaje.  
  
2.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para solicitar que un intervalo de texto determinada se coloreada.  
  
     El método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> devuelve una matriz de valores, uno para cada letra en el intervalo de texto que es coloreada.  También identifica el intervalo de texto como tipo concreto de elemento coloreable, como un comentario, una palabra clave, o un tipo de datos.  
  
3.  Utilice la información del color devuelta por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para que vuelva a y mostrar el texto.  
  
> [!NOTE]
>  Además de un colorizer del servicio de lenguaje, un Paquete puede utilizar el mecanismo de uso general de texto\-colorante de SDK del entorno de Visual Studio.  Para obtener más información sobre este mecanismo, vea [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
## Vea también  
 [Colores en un servicio de lenguaje heredado de sintaxis](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementación de colores de sintaxis](../extensibility/internals/implementing-syntax-coloring.md)   
 [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md)