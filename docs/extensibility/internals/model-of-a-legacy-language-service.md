---
title: "Modelo de un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje, modelo"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Modelo de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servicio de lenguaje define elementos y características para un idioma concreto, y se utiliza para proporcionar el editor con información específica del lenguaje.  Por ejemplo, el editor necesita conocer los elementos y las palabras clave del lenguaje para admitir el colorear la sintaxis.  
  
 El servicio de lenguaje funciona estrechamente con el búfer de texto administrado por el editor y la vista que contiene el editor.  La opción de Microsoft IntelliSense **información rápida** es un ejemplo de una característica proporcionada por un servicio de lenguaje.  
  
## Un servicio de lenguaje mínimo  
 El servicio de lenguaje más básico contiene los dos objetos siguientes:  
  
-   *El servicio de lenguaje* implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  Un servicio de lenguaje tiene información sobre el lenguaje, incluida su nombre, extensiones de nombre de archivo, administrador de ventana de código, y colorizer.  
  
-   *el colorizer* implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  
  
 El gráfico conceptual siguiente muestra un modelo de un servicio de básico.  
  
 ![Gráfico del modelo de servicio de lenguaje](~/docs/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Modelo básico del servicio de lenguaje  
  
 Los hosts de la ventana de documento *la vista del documento* del editor, en cuyo caso el publicador de la base de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  La vista del documento y el búfer de texto pertenecen al editor.  Estos objetos ejecutan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de una ventana de documento especializada denominada *una ventana de código*.  La ventana de códigos se contiene en un objeto de<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> creado y controla el IDE.  
  
 Cuando un archivo con una extensión dada cargado, el editor encuentra el servicio de lenguaje asociado a esa extensión y pasa a la ventana de código llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> .  El servicio de lenguaje devuelve *un administrador de ventana de código*, que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  
  
 La tabla siguiente se proporciona información general sobre los objetos del modelo.  
  
|Componente|Objeto.|Función|  
|----------------|-------------|-------------|  
|Búfer de texto|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Una secuencia de texto de la escritura de Unicode.  es posible que el texto utilice otras codificaciones.|  
|Ventana de código|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|una ventana de documento que contiene una o más vistas de texto.  Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en modo \(MDI\) de interfaz de múltiples documentos, la ventana de código es un elemento secundario de MDI.|  
|vista de texto|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Una ventana que permite al usuario navegar y ver el texto mediante el teclado y el mouse.  Una vista de texto aparece al usuario como editor.  Puede utilizar las vistas de texto en las ventanas normales del editor, la ventana de salida, y la ventana Inmediato.  Además, puede configurar una o más vistas de texto dentro de una ventana de código.|  
|Administrador de texto|Administrado por el servicio de <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> , del que se obtiene un puntero de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>|Un componente que mantiene la información bursátil compartida por todos los componentes descritos previamente.|  
|Servicio de lenguaje|Dependiente de implementación; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Objeto que proporciona el editor con información más específica como resaltado de sintaxis, finalización de instrucciones, y coincidencia de llaves.|  
  
## Vea también  
 [Datos del documento y vista de documento en editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)