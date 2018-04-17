---
title: Interfaces de servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2861c4d6307442e1650b44d2b15f2a084ac7715
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de servicio de lenguaje heredado
Para cualquier lenguaje de programación determinado, puede haber solo una instancia de un servicio de lenguaje a la vez. Sin embargo, un servicio de lenguaje único puede servir a más de un editor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no asocia un servicio de lenguaje con cualquier editor determinado. Por lo tanto, cuando se solicita una operación de servicio de lenguaje, debe identificar el editor adecuado como parámetro.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Interfaces más habituales asociadas con los servicios de lenguaje  
 El editor Obtiene el servicio de lenguaje mediante una llamada a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> en el VSPackage adecuado. El servicio Id. (SID) que se pasan en esta llamada identifica el servicio de lenguaje que se solicita.  
  
 Puede implementar las interfaces de servicio de lenguaje principal en cualquier número de clases independientes. Sin embargo, un enfoque común consiste en implementar las interfaces siguientes en una sola clase:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)  
  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> debe implementar la interfaz en todos los servicios de lenguaje. Proporciona información acerca del servicio de lenguaje, como el nombre localizado del lenguaje, las extensiones de nombre de archivo asociadas con el servicio de lenguaje y cómo recuperar un aplicador de color.  
  
## <a name="additional-language-service-interfaces"></a>Interfaces de servicio de idioma adicionales  
 Otras interfaces pueden proporcionarse con el servicio de lenguaje. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita una instancia independiente de estas interfaces para cada instancia del búfer de texto. Por lo tanto, debe implementar cada una de estas interfaces en su propio objeto. La siguiente tabla muestra las interfaces que requieren una instancia por instancia de búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Administra las opciones gráficas de ventana de código, como la barra de la lista desplegable. Esta interfaz se puede obtener mediante la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método. Hay un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por la ventana de código.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorea delimitadores y palabras clave del lenguaje. Esta interfaz se puede obtener mediante la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se llama en tiempo de paint. Evitar el trabajo de cálculo intensivo dentro de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o podría verse afectado el rendimiento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Proporciona información sobre herramientas de parámetro de IntelliSense. Cuando el servicio de lenguaje reconoce debe ser un carácter que indica que los datos método muestra, por ejemplo, un paréntesis de apertura, se llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> vista de método para notificar el texto que el servicio de lenguaje está listo para mostrar un mensaje de información de parámetro. La vista de texto, a continuación, llama de nuevo en el servicio de lenguaje por con los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz para obtener la información necesaria para mostrar la información sobre herramientas.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Proporciona la finalización de instrucciones de IntelliSense. Cuando el servicio de lenguaje está listo para mostrar una lista de finalización, se llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en la vista de texto. La vista de texto, a continuación, llama de nuevo en el servicio de lenguaje por utilizando los métodos en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objeto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite la modificación de la vista de texto utilizando el controlador de comandos. La clase en la que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> también debe implementar la interfaz de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Recupera la vista de texto el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto consultando la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que se pasa en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Debe haber uno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto por cada vista.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta los comandos que el usuario escribe en la ventana de código. Supervisar los resultados de su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación para proporcionar información de finalización personalizada y ver modificación<br /><br /> Para pasar el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto a la vista de texto, llamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista de comprobación: creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)