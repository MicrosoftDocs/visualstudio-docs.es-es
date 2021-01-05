---
title: Información rápida en un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre la compatibilidad con la operación de información rápida de IntelliSense para mostrar información sobre un identificador.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 255022c2722104d3790d1c417eee644730ddc1e8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875081"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Información rápida en un servicio de lenguaje heredado
La información rápida de IntelliSense muestra información sobre un identificador en el origen cuando el usuario coloca el símbolo de intercalación en el identificador y selecciona **información rápida** en el menú **IntelliSense** o mantiene el cursor del mouse sobre el identificador. Esto hace que aparezca una información sobre herramientas con información sobre el identificador. Esta información normalmente se compone del tipo de identificador. Cuando el motor de depuración está activo, esta información puede incluir el valor actual. El motor de depuración proporciona valores de expresión, mientras que el servicio de lenguaje solo administra identificadores.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [Tutorial: Mostrar la información sobre herramientas de QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 Las clases de servicio de lenguaje de Managed Package Framework (MPF) proporcionan compatibilidad completa para mostrar la información rápida de IntelliSense. Todo lo que tiene que hacer es proporcionar el texto que se va a mostrar y habilitar la característica de información rápida.

 El texto que se va a mostrar se obtiene llamando al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de métodos con un valor de motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> . Este motivo indica al analizador que obtenga la información de tipo (o lo que sea adecuado para que se muestre en la información rápida de la herramienta de información rápida) del identificador en la ubicación especificada en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. El <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es lo que se pasó al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método.

 El analizador debe analizar todo hasta la posición en el objeto con el fin de <xref:Microsoft.VisualStudio.Package.ParseRequest> determinar los tipos de todos los identificadores. Después, el analizador debe obtener el identificador en la ubicación de la solicitud de análisis. Por último, el analizador debe pasar los datos de información sobre herramientas asociados a ese identificador al <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto para que el objeto pueda devolver el texto desde el <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> método.

## <a name="enabling-the-quick-info-feature"></a>Habilitar la característica de información rápida
 Para habilitar la característica de información rápida, debe establecer los `CodeSense` `QuickInfo` parámetros con nombre y de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Estos atributos establecen las <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> propiedades y.

## <a name="implementing-the-quick-info-feature"></a>Implementación de la característica de información rápida
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase controla la operación de información rápida de IntelliSense. Cuando la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase recibe el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la clase llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> y la ubicación del símbolo de intercalación en el momento en que <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> se envió el comando. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>A continuación, el analizador de métodos debe analizar el origen hasta la ubicación especificada y, a continuación, analizar el identificador en la ubicación especificada para determinar lo que se va a mostrar en la información rápida de la información sobre herramientas.

 La mayoría de los analizadores realizan un análisis inicial del archivo de código fuente completo y almacenan los resultados en un árbol de análisis. El análisis completo se realiza cuando <xref:Microsoft.VisualStudio.Package.ParseReason> se pasa al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Otros tipos de análisis pueden utilizar el árbol de análisis para obtener la información deseada.

 Por ejemplo, el valor del motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> puede encontrar el identificador en la ubicación de origen y buscarlo en el árbol de análisis para obtener la información de tipo. A continuación, esta información de tipo se pasa a la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase y el método lo devuelve <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .
