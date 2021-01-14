---
title: Interfaces del servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre las interfaces disponibles en el SDK de Visual Studio que proporcionan características del servicio de lenguaje heredado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb694389bbf6f913db084dca29f7787c6283d3ad
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205034"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de servicio de lenguaje heredado
Para cualquier lenguaje de programación determinado, solo puede haber una instancia de un servicio de lenguaje a la vez. Sin embargo, un servicio de lenguaje único puede atender a más de un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no asocia un servicio de lenguaje a ningún editor determinado. Por lo tanto, cuando solicite una operación del servicio de lenguaje, debe identificar el editor adecuado como parámetro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comunes asociadas a los servicios de lenguaje
 El editor obtiene el servicio de lenguaje mediante una llamada a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> en el VSPackage adecuado. El identificador de servicio (SID) pasado en esta llamada identifica el servicio de lenguaje que se solicita.

 Puede implementar las interfaces principales del servicio de lenguaje en cualquier número de clases independientes. Sin embargo, un enfoque común consiste en implementar las siguientes interfaces en una sola clase:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)

  La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz debe implementarse en todos los servicios de lenguaje. Proporciona información sobre el servicio de lenguaje, como el nombre localizado del idioma, las extensiones de nombre de archivo asociadas con el servicio de lenguaje y cómo recuperar un coloreador.

## <a name="additional-language-service-interfaces"></a>Interfaces de servicio de lenguaje adicionales
 Se pueden proporcionar otras interfaces con el servicio de lenguaje. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita una instancia independiente de estas interfaces para cada instancia del búfer de texto. Por lo tanto, debe implementar cada una de estas interfaces en su propio objeto. En la tabla siguiente se muestran las interfaces que requieren una instancia por cada instancia de búfer de texto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Administra los elementos gráficos de la ventana de código, como la barra desplegable. Puede obtener esta interfaz mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método. Hay una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por cada ventana de código.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorea las palabras clave y los delimitadores del lenguaje. Puede obtener esta interfaz mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> se llama en el momento de la pintura. Evite el trabajo que consume muchos recursos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rendimiento o podría verse afectado.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Proporciona información sobre herramientas de parámetros de IntelliSense. Cuando el servicio de lenguaje reconoce un carácter que indica que se deben mostrar los datos del método, como un paréntesis de apertura, llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método para notificar a la vista de texto que el servicio de lenguaje está listo para mostrar la información sobre herramientas información sobre parámetros. La vista de texto vuelve a llamar al servicio de lenguaje mediante los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz para obtener la información necesaria para mostrar la información sobre herramientas.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Proporciona la finalización de instrucciones de IntelliSense. Cuando el servicio de lenguaje está listo para mostrar una lista de finalización, llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en la vista de texto. La vista de texto vuelve a llamar al servicio de lenguaje mediante el uso de métodos en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> objeto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite modificar la vista de texto mediante el controlador de comandos. La clase en la que se implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaz también debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. La vista de texto recupera el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto consultando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto que se pasa al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Debe haber un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> objeto para cada vista.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta los comandos que el usuario escribe en la ventana de código. Supervisar la salida de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación para proporcionar información de finalización personalizada y ver la modificación<br /><br /> Para pasar el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto a la vista de texto, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista de comprobación: Creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
