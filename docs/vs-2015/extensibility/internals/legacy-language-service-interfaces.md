---
title: Las Interfaces de servicio de lenguaje heredado | Documentos de Microsoft
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
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d64ff7ec1aea24a5e98b3f37339639440e31bf42
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837248"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para cualquier lenguaje de programación determinado, puede haber solo una instancia de un servicio de lenguaje a la vez. Sin embargo, un servicio de lenguaje único puede servir a más de un editor.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no asocia un servicio de lenguaje con cualquier editor determinado. Por lo tanto, cuando se solicita una operación de servicio de lenguaje, debe identificar el editor adecuado como parámetro.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comunes asociadas con los servicios de lenguaje  
 El editor Obtiene el servicio de lenguaje mediante una llamada a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> en el VSPackage adecuado. El servicio pasa el identificador (SID) en esta llamada identifica el servicio de lenguaje que se solicita.  
  
 Puede implementar las interfaces de servicio de lenguaje principal en cualquier número de clases independientes. Sin embargo, un enfoque común consiste en implementar las interfaces siguientes en una sola clase:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)  
  
  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz debe implementarse en todos los servicios de lenguaje. Proporciona información sobre el servicio de lenguaje, como el nombre localizado del lenguaje, las extensiones de nombre de archivo asociadas con el servicio de lenguaje y cómo recuperar un Coloreador.  
  
## <a name="additional-language-service-interfaces"></a>Interfaces de servicio de idioma adicionales  
 Otras interfaces pueden proporcionarse con el servicio de lenguaje. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] solicita una instancia independiente de estas interfaces para cada instancia del búfer de texto. Por lo tanto, debe implementar cada una de estas interfaces en su propio objeto. La siguiente tabla muestra las interfaces que requieren una instancia por cada instancia del búfer de texto.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Administra los elementos gráficos de ventana de código, como la barra desplegable. Puede obtener esta interfaz mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método. Hay un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por ventana de código.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorea delimitadores y palabras clave del lenguaje. Puede obtener esta interfaz mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se llama en tiempo de dibujo. Evitar el trabajo de cálculo intensivo dentro de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o podría verse afectado el rendimiento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Proporciona información sobre herramientas de parámetro de IntelliSense. Cuando el servicio de lenguaje reconoce debe ser un carácter que indica que los datos método muestran, como un paréntesis de apertura, llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> vista de método para notificar el texto que el servicio de lenguaje está listo para mostrar una información sobre herramientas de información de parámetro. La vista de texto, a continuación, llama de nuevo mediante el servicio de lenguaje mediante los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz para obtener la información necesaria para mostrar la información sobre herramientas.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Proporciona la finalización de instrucciones de IntelliSense. Cuando el servicio de lenguaje está listo para mostrar una lista de finalización, llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en la vista de texto. La vista de texto, a continuación, llama de nuevo al servicio de lenguaje por uso de métodos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objeto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite la modificación de la vista de texto mediante el controlador de comandos. La clase en el que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> también debe implementar la interfaz de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Recupera la vista de texto el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto consultando la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que se pasa a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Debe haber un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto para cada vista.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta comandos que el usuario escribe en la ventana de código. Supervisar los resultados de su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación para proporcionar información de finalización personalizada y ver la modificación<br /><br /> Para pasar su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto a la vista de texto, llamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista de comprobación: creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

