---
title: "Interfaces de servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IVsLanguageInfo"
  - "Servicios de lenguaje, objetos"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Interfaces de servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para cualquier lenguaje de programación determinado, solo puede haber una instancia de un servicio de al mismo tiempo.  Sin embargo, un servicio solo lenguaje puede servir más de un editor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no asocia un servicio de con ningún editor determinado.  Por consiguiente, cuando se solicita una operación del servicio de lenguaje, debe identificar el editor correspondiente como parámetro.  
  
## interfaces comunes asociado con el lenguaje Services  
 El editor obtiene el servicio de lenguaje llamando a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> en el paquete VSPackage adecuado.  El identificador de servicio \(SID\) pasado a esta llamada identifica el servicio de lenguaje que se está solicitando.  
  
 Puede implementar las interfaces básicas del servicio de lenguaje en cualquier número de clases independientes.  Sin embargo, un enfoque común es implementar las siguientes interfaces en una sola clase:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(opcional\)  
  
 La interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> se debe implementar en todos los servicios.  Proporciona información sobre el servicio de lenguaje, como el nombre adaptado del lenguaje, las extensiones de nombre de archivo asociado al servicio de lenguaje, y cómo recuperar un colorizer.  
  
## Interfaces adicionales del servicio de lenguaje  
 Otras interfaces se pueden proporcionar el servicio de lenguaje.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita una instancia independiente de estas interfaces para cada instancia del búfer de texto.  Por consiguiente, debe implementar cada una de estas interfaces en el propio objeto.  La tabla siguiente se muestran las interfaces que requieran una instancia por la instancia del búfer de texto.  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Administra los elementos gráficos de la ventana de código, como la barra desplegable.  Puede obtener esta interfaz utilizando el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> .  Hay un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por la ventana de código.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorea palabras clave y los delimitadores de lenguaje.  Puede obtener esta interfaz utilizando el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> .  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se llama en el tiempo de dibujo.  evite el trabajo cálculo\-intensivo dentro de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o el rendimiento podría sufrir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Proporciona información sobre herramientas del parámetro de IntelliSense.  Cuando el servicio de lenguaje reconoce un carácter que indica que los datos de método se deben mostrar, por ejemplo un paréntesis de apertura, llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> para notificar a la vista de texto que el servicio de lenguaje está listo para mostrar una información sobre herramientas de la información de parámetros.  Las llamadas de la vista de texto después de nuevo con el servicio de lenguaje mediante los métodos de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> para obtener la información necesaria para mostrar la información sobre herramientas.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Proporciona la finalización de instrucciones de IntelliSense.  Cuando el servicio de lenguaje está listo para mostrar una lista de finalización, llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en la vista de texto.  Las llamadas de la vista de texto después de nuevo con el servicio de lenguaje mediante los métodos del objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite modificar la vista de texto utilizando el controlador de comandos.  La clase a la que se implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> también debe implementar la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  La vista de texto recupera el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> consultando el objeto de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> que se pasa al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  Debe haber un objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> para cada vista.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta los comandos esos tipos de usuario en la ventana de código.  Controla la salida de la implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para proporcionar información personalizada de finalización y modificar la vista<br /><br /> Para pasar el objeto de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a la vista de texto, asigne al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## Vea también  
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista de comprobación: Crear un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)