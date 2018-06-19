---
title: Información rápida en un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132162"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Información rápida en un servicio de lenguaje heredado
Información rápida de IntelliSense muestra información sobre un identificador en el origen cuando el usuario ya sea coloca el símbolo de intercalación en el identificador y selecciona **Quick Info** desde el **IntelliSense** menú o mantiene el mouse cursor sobre el identificador. Esto hace que una información sobre herramientas para que aparezca con información sobre el identificador. Esta información normalmente está formada por el tipo de identificador. Cuando el motor de depuración está activo, esta información puede incluir el valor actual. El motor de depuración proporciona valores de expresión, mientras que el servicio de lenguaje controla solo identificadores.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información, consulte [Tutorial: mostrar sobre herramientas de QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 Las clases de servicio de managed package framework (MPF) lenguaje proporcionan compatibilidad completa para mostrar la información sobre herramientas información rápida de IntelliSense. Todo lo que tiene que hacer es proporcionar el texto para mostrar y habilitar la característica información rápida.  
  
 El texto que se mostrará se obtiene mediante una llamada a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de método con un valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Ello indica el analizador para obtener la información de tipo (o lo que sea necesario que se mostrará en la información sobre herramientas información rápida) para el identificador en la ubicación especificada en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. El <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es lo que se pasa a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método.  
  
 El analizador debe analizar todos los elementos hasta la posición en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto con el fin de determinar los tipos de todos los identificadores. A continuación, el analizador debe obtener el identificador en la ubicación de la solicitud de análisis. Por último, el analizador debe pasar los datos de información sobre herramienta asociados con ese identificador para la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto para ese objeto pueda devolver el texto de la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> método.  
  
## <a name="enabling-the-quick-info-feature"></a>Habilitar la característica información rápida  
 Para habilitar la característica información rápida, debe establecer el `CodeSense` y `QuickInfo` denominado parámetros de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Estos atributos establecen el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> y <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> propiedades.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementar la característica información rápida  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase administra la operación de información rápida de IntelliSense. Cuando el <xref:Microsoft.VisualStudio.Package.ViewFilter> clase recibe el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la clase llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método con la razón para el análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> y la ubicación del símbolo de intercalación en el momento de la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> se envió el comando. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de método debe, a continuación, analizar el origen hasta la ubicación especificada y, a continuación, analizar el identificador en la ubicación especificada para determinar qué se debe mostrar en la información sobre herramientas de información rápida.  
  
 La mayoría de los analizadores realice un análisis inicial del archivo de código fuente y almacenan los resultados en un árbol de análisis. El análisis completo se lleva a cabo cuando <xref:Microsoft.VisualStudio.Package.ParseReason> se pasa a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Otros tipos de análisis, a continuación, pueden utilizar el árbol de análisis para obtener la información deseada.  
  
 Por ejemplo, el valor de razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> puede encontrar el identificador en la ubicación de origen y buscar en el árbol de análisis para obtener la información de tipo. Esta información de tipo, a continuación, se pasa a la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase y devuelve el <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> método.