---
title: Información rápida en un servicio de lenguaje heredado | Documentos de Microsoft
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
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ff6f4a29d194aaa5c9b868fffa19947a7321c77
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797213"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Información rápida en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Información rápida de IntelliSense muestra información acerca de un identificador en el origen cuando el usuario, ya sea coloca el símbolo de intercalación en el identificador y selecciona **información rápida** desde el **IntelliSense** menú o mantiene el mouse cursor sobre el identificador. Esto hace que una información sobre herramientas con información sobre el identificador. Esta información normalmente está formada por el tipo de identificador. Cuando el motor de depuración está activo, esta información puede incluir el valor actual. El motor de depuración proporciona valores de expresión, mientras que el servicio de lenguaje controla solo identificadores.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información, consulte [Tutorial: mostrar información rápida](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 Las clases de servicio de lenguaje de framework (MPF) de paquetes administrados proporcionan compatibilidad completa para mostrar la información sobre herramientas de información rápida de IntelliSense. Todo lo que debe hacer es proporcionar el texto para mostrarse y habilitar la característica información rápida.  
  
 El texto que se mostrará se obtiene mediante una llamada a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de método con un valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Ello informa al analizador para obtener la información de tipo (o lo que sea necesario que se mostrará en la información sobre herramientas de información rápida) para el identificador en la ubicación especificada en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. El <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es lo que se pasó a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método.  
  
 El analizador debe analizar todo hasta la posición de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto con el fin de determinar los tipos de todos los identificadores. A continuación, el analizador debe obtener el identificador en la ubicación de la solicitud de análisis. Por último, el analizador debe pasar los datos de la sugerencia de herramienta asociados con ese identificador para el <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto para que ese objeto pueda devolver el texto de la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> método.  
  
## <a name="enabling-the-quick-info-feature"></a>Habilitar la característica información rápida  
 Para habilitar la característica información rápida, debe establecer el `CodeSense` y `QuickInfo` denominado parámetros de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Estos atributos establecen el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> y <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> propiedades.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementación de la característica información rápida  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase controla la operación de información rápida de IntelliSense. Cuando el <xref:Microsoft.VisualStudio.Package.ViewFilter> clase recibe el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la clase llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> y la ubicación del símbolo de intercalación en el momento en el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> se envió el comando. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador del método debe, a continuación, analizar el origen hasta la ubicación especificada y, a continuación, analizar el identificador en la ubicación especificada para determinar qué se debe mostrar en la información rápida sobre herramientas.  
  
 La mayoría de los analizadores hacer un análisis inicial del archivo de código fuente completo y almacenan los resultados en un árbol de análisis. Cuando se realiza el análisis completo <xref:Microsoft.VisualStudio.Package.ParseReason> se pasa a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Otros tipos de análisis, a continuación, pueden usar el árbol de análisis para obtener la información deseada.  
  
 Por ejemplo, el valor de motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> puede encontrar el identificador en la ubicación de origen y buscar en el árbol de análisis para obtener la información de tipo. Esta información de tipo, a continuación, se pasa a la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase y es devuelto por la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> método.

