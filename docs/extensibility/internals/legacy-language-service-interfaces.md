---
title: Interfaces de servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre las interfaces disponibles en el SDK Visual Studio que proporcionan características de servicio de lenguaje heredado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75697e1d212b24b743fed62284b384985749fe7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898609"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de servicio de lenguaje heredado
Para cualquier lenguaje de programación determinado, solo puede haber una instancia de un servicio de lenguaje a la vez. Sin embargo, un solo servicio de lenguaje puede servir a más de un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no asocia un servicio de lenguaje a ningún editor determinado. Por lo tanto, cuando solicite una operación de servicio de lenguaje, debe identificar el editor adecuado como parámetro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comunes asociadas a Language Services
 El editor obtiene el servicio de lenguaje mediante una <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> llamada a en el VSPackage adecuado. El identificador de servicio (SID) pasado en esta llamada identifica el servicio de lenguaje que se solicita.

 Puede implementar las interfaces principales del servicio de lenguaje en cualquier número de clases independientes. Sin embargo, un enfoque común es implementar las siguientes interfaces en una sola clase:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)

  La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz debe implementarse en todos los servicios de lenguaje. Proporciona información sobre el servicio de lenguaje, como el nombre localizado del idioma, las extensiones de nombre de archivo asociadas al servicio de lenguaje y cómo recuperar un colorizador.

## <a name="additional-language-service-interfaces"></a>Interfaces de servicio de lenguaje adicionales
 Se pueden proporcionar otras interfaces con el servicio de lenguaje. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita una instancia independiente de estas interfaces para cada instancia del búfer de texto. Por lo tanto, debe implementar cada una de estas interfaces en su propio objeto . En la tabla siguiente se muestran las interfaces que requieren una instancia por instancia de búfer de texto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Administra los adornos de la ventana de código, como la barra desplegable. Puede obtener esta interfaz mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método . Hay una por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> ventana de código.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Coloriza las palabras clave y los delimitadores del lenguaje. Puede obtener esta interfaz mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se llama en el momento de la pintura. Evite el trabajo intensivo de cálculo dentro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> de o el rendimiento podría sufrir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Proporciona información sobre herramientas de parámetros de IntelliSense. Cuando el servicio de lenguaje reconoce un carácter que indica que se deben mostrar los datos del método, como un paréntesis abierto, llama al método para notificar a la vista de texto que el servicio de lenguaje está listo para mostrar una información sobre herramientas de información de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> parámetros. A continuación, la vista de texto vuelve a llamar al servicio de lenguaje mediante los métodos de la interfaz para obtener la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> información necesaria para mostrar la información sobre herramientas.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Proporciona la finalización de instrucciones de IntelliSense. Cuando el servicio de lenguaje está listo para mostrar una lista de finalización, llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en la vista de texto. A continuación, la vista de texto vuelve a llamar al servicio de lenguaje mediante métodos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objeto .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite modificar la vista de texto mediante el controlador de comandos. La clase en la que se implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaz también debe implementar la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . La vista de texto recupera el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto consultando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que se pasa al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> . Debe haber un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto para cada vista.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta los comandos que el usuario tipos en la ventana de código. Supervisar la salida de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación para proporcionar información de finalización personalizada y ver la modificación<br /><br /> Para pasar el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto a la vista de texto, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Consulta también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista de comprobación: Creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
