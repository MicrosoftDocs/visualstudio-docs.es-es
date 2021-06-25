---
title: Finalización de palabras en un servicio de lenguaje heredado | Microsoft Docs
description: La finalización de palabras puede ser compatible con un servicio de lenguaje heredado en Visual Studio SDK. Obtenga información sobre cómo se implementan los servicios de lenguaje heredados en un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea386aea3a17b0fb0d93ff9872f92e86a166be5c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902636"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Finalización de palabras en un servicio de lenguaje heredado
La finalización de palabras rellena los caracteres que faltan en una palabra con tipo parcial. Si solo hay una posible finalización, la palabra se completa cuando se introduce el carácter de finalización. Si la palabra parcial coincide con más de una posibilidad, se muestra una lista de posibles finalizaciones. Un carácter de finalización puede ser cualquier carácter que no se utilice para los identificadores.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la manera más reciente de implementar características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, vea [Extending the Editor and Language Services](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Se recomienda empezar a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementation-steps"></a>Pasos de implementación

1. Cuando el usuario selecciona **Palabra completa en** el menú **IntelliSense,** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> el comando se envía al servicio de lenguaje.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase detecta el comando y llama al método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. A continuación, la clase llama al método para obtener la lista de posibles finalizaciones de palabras y, a continuación, muestra las palabras en una lista de información sobre <xref:Microsoft.VisualStudio.Package.Source> herramientas mediante la clase <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> .

    Si solo hay una palabra correspondiente, la <xref:Microsoft.VisualStudio.Package.Source> clase completa la palabra.

   Como alternativa, si el analizador devuelve el valor del desencadenador cuando se escribe el primer carácter de un identificador, la clase lo detecta y llama al método con el motivo de <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source> análisis de <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> . En este caso, el analizador debe detectar la presencia de un carácter de selección de miembro y proporcionar una lista de miembros.

## <a name="enabling-support-for-the-complete-word"></a>Habilitación de la compatibilidad con La palabra completa
 Para habilitar la compatibilidad con la finalización de palabras, establezca `CodeSense` el parámetro con nombre pasado al atributo de usuario asociado al paquete de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> idioma. Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en la clase <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

 El analizador debe devolver una lista de declaraciones en respuesta al valor de motivo del análisis <xref:Microsoft.VisualStudio.Package.ParseReason> para que funcione la finalización de palabras.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementación de Complete Word en el método ParseSource
 Para la finalización de palabras, la clase llama al método de la clase para <xref:Microsoft.VisualStudio.Package.Source> obtener una lista de <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> posibles coincidencias de palabras. Debe implementar la lista en una clase derivada de la <xref:Microsoft.VisualStudio.Package.Declarations> clase . Consulte la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información sobre los métodos que debe implementar.

 Si la lista contiene solo una palabra, la clase inserta automáticamente <xref:Microsoft.VisualStudio.Package.Source> esa palabra en lugar de la palabra parcial. Si la lista contiene más de una palabra, la clase presenta una lista de sugerencias de herramientas en la que el usuario <xref:Microsoft.VisualStudio.Package.Source> puede seleccionar la opción adecuada.

 Vea también el ejemplo de una implementación de <xref:Microsoft.VisualStudio.Package.Declarations> clase en Finalización de miembros en un servicio de lenguaje [heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
