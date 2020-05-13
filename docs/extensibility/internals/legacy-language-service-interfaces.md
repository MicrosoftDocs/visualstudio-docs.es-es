---
title: Interfaces de servicio de lenguaje heredados ? Microsoft Docs
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
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707379"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de servicio de lenguaje heredado
Para cualquier lenguaje de programación en particular, solo puede haber una instancia de un servicio de lenguaje a la vez. Sin embargo, un servicio de idioma único puede servir a más de un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]no asocia un servicio de lenguaje con ningún editor en particular. Por lo tanto, cuando solicite una operación de servicio de lenguaje, debe identificar el editor adecuado como parámetro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comunes asociadas con los servicios de idiomas
 El editor obtiene el servicio <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> de lenguaje llamando al VSPackage adecuado. El identificador de servicio (SID) pasado en esta llamada identifica el servicio de lenguaje que se solicita.

 Puede implementar las interfaces de servicio de lenguaje principal en cualquier número de clases independientes. Sin embargo, un enfoque común es implementar las siguientes interfaces en una sola clase:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)

  La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz debe implementarse en todos los servicios de lenguaje. Proporciona información sobre el servicio de lenguaje, como el nombre localizado del idioma, las extensiones de nombre de archivo asociadas con el servicio de lenguaje y cómo recuperar un colorante.

## <a name="additional-language-service-interfaces"></a>Interfaces de servicio de lenguaje adicionales
 Se pueden proporcionar otras interfaces con su servicio de lenguaje. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]solicita una instancia independiente de estas interfaces para cada instancia del búfer de texto. Por lo tanto, debe implementar cada una de estas interfaces en su propio objeto. En la tabla siguiente se muestran las interfaces que requieren una instancia por instancia de búfer de texto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Administra los adornos de ventanas de código, como la barra desplegable. Puede obtener esta interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> mediante el método. Hay uno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por ventana de código.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Coloriza las palabras clave y delimitadores de idioma. Puede obtener esta interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> mediante el método. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>se llama en el momento de la pintura. Evite el trabajo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> intensivo en computación dentro o el rendimiento podría sufrir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Proporciona información sobre herramientas de parámetros de IntelliSense. Cuando el servicio de lenguaje reconoce un carácter que indica que se deben mostrar los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> datos del método, como un paréntesis abierto, llama al método para notificar a la vista de texto que el servicio de lenguaje está listo para mostrar una información de parámetros. A continuación, la vista de texto vuelve a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> llamar al servicio de lenguaje mediante los métodos de la interfaz para obtener la información necesaria para mostrar la información sobre herramientas.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Proporciona la finalización de instrucciones intelliSense. Cuando el servicio de lenguaje está listo para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> mostrar una lista de finalización, llama al método en la vista de texto. A continuación, la vista de texto vuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> a llamar al servicio de lenguaje mediante métodos en el objeto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite modificar la vista de texto mediante el controlador de comandos. La clase en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la interfaz también debe implementar la interfaz. La vista de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> texto recupera el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto consultando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> el objeto que se pasa al método. Debe haber <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> un objeto para cada vista.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta comandos que el usuario escribe en la ventana de código. Supervise la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> salida de su implementación para proporcionar información de finalización personalizada y ver la modificación<br /><br /> Para pasar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> el objeto a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>la vista de texto, llame a .|

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista de comprobación: creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
