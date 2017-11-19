---
title: "Finalización de palabras en un servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c24765450d0bf8ffdab479bb28c822602892b595
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>Finalización automática de palabras en un servicio de lenguaje heredado
Finalización automática de palabras rellena los caracteres que faltan en una palabra escrita parcialmente. Si hay solo una finalización posibles, la palabra se completa cuando se escribe el carácter de finalización. Si la palabra parcial coincide con más de una posibilidad, se muestra una lista de finalizaciones posibles. Una terminación de carácter puede ser cualquier carácter que no se utiliza para los identificadores.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información, consulte [extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="implementation-steps"></a>Pasos de implementación  
  
1.  Cuando el usuario selecciona **palabra completa** desde el **IntelliSense** menú, el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando se envía al servicio de lenguaje.  
  
2.  El <xref:Microsoft.VisualStudio.Package.ViewFilter> clase detecta el comando y llama el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con la razón para el análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  El <xref:Microsoft.VisualStudio.Package.Source> llamadas de clase y después la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para obtener la lista de finalizaciones de word posible y, a continuación, muestra las palabras en una información sobre herramientas lista usando el <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.  
  
     Si no hay sólo una palabra de búsqueda de coincidencias, el <xref:Microsoft.VisualStudio.Package.Source> clase completa la palabra.  
  
 O bien, si el escáner devuelve el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> cuando se escribe el primer carácter de un identificador, el <xref:Microsoft.VisualStudio.Package.Source> clase lo detecta y llama a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con la razón para el análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. En este caso el analizador debe detectar la presencia de un carácter de la selección de miembro y proporcionar una lista de miembros.  
  
## <a name="enabling-support-for-the-complete-word"></a>Habilitar la compatibilidad para la palabra completa  
 Para habilitar la compatibilidad para el conjunto de finalizaciones de word el `CodeSense` con el nombre de parámetro pasado a la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado con el paquete de idioma. Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
 El analizador debe devolver una lista de declaraciones en respuesta al valor de la razón de análisis <xref:Microsoft.VisualStudio.Package.ParseReason>, para la finalización automática de palabras para que funcione.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementar la palabra completa en el método ParseSource  
 Finalización de palabras, el <xref:Microsoft.VisualStudio.Package.Source> clase llamadas el <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método en la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase para obtener una lista de coincidencias de palabras posible. La lista debe implementar en una clase que se deriva de la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Consulte la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información sobre los métodos que debe implementar.  
  
 Si la lista contiene solo una sola palabra, el <xref:Microsoft.VisualStudio.Package.Source> clase inserta automáticamente esa palabra en lugar de las palabras parciales. Si la lista contiene más de una palabra, el <xref:Microsoft.VisualStudio.Package.Source> clase presenta una lista de sugerencias de la herramienta desde el que el usuario puede seleccionar la opción adecuada.  
  
 Examine también el ejemplo de un <xref:Microsoft.VisualStudio.Package.Declarations> implementación de la clase en [finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).