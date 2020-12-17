---
title: Finalización de palabras en un servicio de lenguaje heredado | Microsoft Docs
description: La finalización de palabras se puede admitir para un servicio de lenguaje heredado en el SDK de Visual Studio. Obtenga información sobre cómo se implementan los servicios de lenguaje heredados en un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 489b43c825e3512e1bd33bc732833de84aed54c3
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616280"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Finalización de palabras en un servicio de lenguaje heredado
La finalización de palabras rellena los caracteres que faltan en una palabra parcialmente tipada. Si solo hay una posible finalización, la palabra se completa cuando se escribe el carácter de finalización. Si la palabra parcial coincide con más de una posibilidad, se muestra una lista de posibles finalizaciones. Un carácter de finalización puede ser cualquier carácter que no se use para los identificadores.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [extender el editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementation-steps"></a>Pasos de implementación

1. Cuando el usuario selecciona **palabra completa** en el menú **IntelliSense** , el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando se envía al servicio de lenguaje.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase detecta el comando y llama al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. <xref:Microsoft.VisualStudio.Package.Source>A continuación, la clase llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para obtener la lista de posibles finalizaciones de palabras y, a continuación, muestra las palabras de una lista de información sobre herramientas mediante la <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.

    Si solo hay una palabra coincidente, la <xref:Microsoft.VisualStudio.Package.Source> clase completa la palabra.

   Como alternativa, si el analizador devuelve el valor del desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> cuando se escribe el primer carácter de un identificador, la <xref:Microsoft.VisualStudio.Package.Source> clase lo detecta y llama al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> . En este caso, el analizador debe detectar la presencia de un carácter de selección de miembro y proporcionar una lista de miembros.

## <a name="enabling-support-for-the-complete-word"></a>Habilitar la compatibilidad con la palabra completa
 Para habilitar la compatibilidad con la finalización de palabras, establezca el `CodeSense` parámetro con nombre pasado al <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado al paquete de idioma. Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.

 El analizador debe devolver una lista de declaraciones en respuesta al valor de motivo de análisis <xref:Microsoft.VisualStudio.Package.ParseReason> , para que la finalización de la palabra funcione.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementar palabra completa en el método ParseSource
 Para la finalización de palabras, la <xref:Microsoft.VisualStudio.Package.Source> clase llama al <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método en la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase para obtener una lista de posibles coincidencias de palabras. Debe implementar la lista en una clase que se deriva de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Vea la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información sobre los métodos que debe implementar.

 Si la lista contiene una sola palabra, la <xref:Microsoft.VisualStudio.Package.Source> clase inserta automáticamente esa palabra en lugar de la palabra parcial. Si la lista contiene más de una palabra, la <xref:Microsoft.VisualStudio.Package.Source> clase presenta una lista de información sobre herramientas en la que el usuario puede seleccionar la opción adecuada.

 Observe también el ejemplo de una <xref:Microsoft.VisualStudio.Package.Declarations> implementación de clase en la [finalización de miembros en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
