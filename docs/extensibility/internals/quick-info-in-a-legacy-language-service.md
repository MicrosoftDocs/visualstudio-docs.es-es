---
title: Información rápida en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705940"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Información rápida en un servicio de lenguaje heredado
Información rápida de IntelliSense muestra información sobre un identificador en el origen cuando el usuario coloca el intercalador en el identificador y selecciona **Información rápida** en el menú **IntelliSense** o mantiene el cursor del mouse sobre el identificador. Esto hace que aparezca una información sobre herramientas con información sobre el identificador. Esta información normalmente consta del tipo de identificador. Cuando el motor de depuración está activo, esta información puede incluir el valor actual. El motor de depuración proporciona valores de expresión, mientras que el servicio de lenguaje solo controla los identificadores.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Tutorial: Visualización](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)de información sobre herramientas quickinfo .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 Las clases de servicio de lenguaje de marco de paquetes administrados (MPF) proporcionan compatibilidad completa para mostrar la información rápida de IntelliSense. Todo lo que tiene que hacer es proporcionar el texto que se mostrará y habilitar la función de información rápida.

 El texto que se va a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> mostrar se obtiene llamando al <xref:Microsoft.VisualStudio.Package.ParseReason>analizador de métodos con un valor de motivo de análisis de . Este motivo indica al analizador que obtenga la información de tipo (o lo que sea apropiado que se muestre <xref:Microsoft.VisualStudio.Package.ParseRequest> en la información rápida de la herramienta) para el identificador en la ubicación especificada en el objeto. El <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es lo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que se pasó al método.

 El analizador debe analizar todo hasta <xref:Microsoft.VisualStudio.Package.ParseRequest> la posición en el objeto para determinar los tipos de todos los identificadores. A continuación, el analizador debe obtener el identificador en la ubicación de la solicitud de análisis. Por último, el analizador debe pasar los datos <xref:Microsoft.VisualStudio.Package.AuthoringScope> de información sobre herramientas asociados <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> a ese identificador al objeto para que el objeto pueda devolver el texto del método.

## <a name="enabling-the-quick-info-feature"></a>Habilitación de la función de información rápida
 Para habilitar la función Información `CodeSense` rápida, debe establecer los parámetros con nombre del `QuickInfo` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>archivo . Estos atributos <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> establecen las propiedades y.

## <a name="implementing-the-quick-info-feature"></a>Implementación de la función de información rápida
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase controla la operación de información rápida de IntelliSense. Cuando <xref:Microsoft.VisualStudio.Package.ViewFilter> la clase <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> recibe el comando, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> la clase llama <xref:Microsoft.VisualStudio.Package.ParseReason> al método con el motivo <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> de análisis y la ubicación del símbolo de intercalación en el momento en que se envió el comando. A <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> continuación, el analizador de métodos debe analizar el origen hasta la ubicación dada y, a continuación, analizar el identificador en la ubicación dada para determinar qué mostrar en la información rápida de la información.

 La mayoría de los analizadores realizan un análisis inicial de todo el archivo de origen y almacenan los resultados en un árbol de análisis. El análisis completo <xref:Microsoft.VisualStudio.Package.ParseReason> se lleva <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> a cabo cuando se pasa al método. Otros tipos de análisis pueden utilizar el árbol de análisis para obtener la información deseada.

 Por ejemplo, el valor <xref:Microsoft.VisualStudio.Package.ParseReason> de motivo de análisis de puede encontrar el identificador en la ubicación de origen y buscarlo en el árbol de análisis para obtener la información de tipo. A continuación, esta información <xref:Microsoft.VisualStudio.Package.AuthoringScope> de tipo se <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> pasa a la clase y la devuelve el método.
