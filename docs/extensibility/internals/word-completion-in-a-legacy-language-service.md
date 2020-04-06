---
title: Finalización de palabras en un servicio de lenguaje heredado ? Microsoft Docs
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
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703174"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Finalización de palabras en un servicio de lenguaje heredado
La finalización de la palabra rellena los caracteres que faltan en una palabra con tipo parcial. Si solo hay una posible finalización, la palabra se completa cuando se introduce el carácter de finalización. Si la palabra parcial coincide con más de una posibilidad, se muestra una lista de posibles terminaciones. Un carácter de finalización puede ser cualquier carácter que no se utilice para los identificadores.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Ampliación del editor y](../../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementation-steps"></a>Pasos de implementación

1. Cuando el usuario selecciona **Palabra completa** en el menú **IntelliSense,** el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando se envía al servicio de lenguaje.

2. La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase detecta el comando <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> y llama al <xref:Microsoft.VisualStudio.Package.ParseReason>método con el motivo de análisis de .

3. A <xref:Microsoft.VisualStudio.Package.Source> continuación, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> la clase llama al método para obtener la lista de posibles <xref:Microsoft.VisualStudio.Package.CompletionSet> terminaciones de palabras y, a continuación, muestra las palabras en una lista de información sobre herramientas mediante la clase.

    Si solo hay una palabra <xref:Microsoft.VisualStudio.Package.Source> coincidente, la clase completa la palabra.

   Como alternativa, si el analizador <xref:Microsoft.VisualStudio.Package.TokenTriggers> devuelve el valor del desencadenador cuando <xref:Microsoft.VisualStudio.Package.Source> se escribe el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> primer carácter <xref:Microsoft.VisualStudio.Package.ParseReason>de un identificador, la clase lo detecta y llama al método con el motivo de análisis de . En este caso, el analizador debe detectar la presencia de un carácter de selección de miembro y proporcionar una lista de miembros.

## <a name="enabling-support-for-the-complete-word"></a>Habilitación de soporte para la palabra completa
 Para habilitar la compatibilidad `CodeSense` con la finalización de palabras, establezca el parámetro con nombre pasado al <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado al paquete de idioma. Esto establece <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propiedad en la clase.

 El analizador debe devolver una lista de declaraciones <xref:Microsoft.VisualStudio.Package.ParseReason>en respuesta al valor de motivo de análisis, para que funcione la finalización de palabras.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementación de Word Completa en el Método ParseSource
 Para la finalización de palabras, la <xref:Microsoft.VisualStudio.Package.Source> clase llama al <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase para obtener una lista de posibles coincidencias de palabras. Debe implementar la lista en una clase <xref:Microsoft.VisualStudio.Package.Declarations> que se deriva de la clase. Consulte <xref:Microsoft.VisualStudio.Package.Declarations> la clase para obtener más información sobre los métodos que debe implementar.

 Si la lista contiene una sola <xref:Microsoft.VisualStudio.Package.Source> palabra, la clase inserta automáticamente esa palabra en lugar de la palabra parcial. Si la lista contiene más <xref:Microsoft.VisualStudio.Package.Source> de una palabra, la clase presenta una lista de información sobre herramientas de la que el usuario puede seleccionar la opción adecuada.

 Consulte también el ejemplo <xref:Microsoft.VisualStudio.Package.Declarations> de una implementación de clase en [Finalización de miembros en un servicio](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)de lenguaje heredado .
