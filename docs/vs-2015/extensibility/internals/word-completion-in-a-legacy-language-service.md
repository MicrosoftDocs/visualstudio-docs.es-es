---
title: Finalización de palabras en un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd176c232bafd0d5a7a2b6735ba71b2bb490781d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581741"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Finalización de palabras en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [finalización de palabras en un servicio de lenguaje heredado](https://docs.microsoft.com/visualstudio/extensibility/internals/word-completion-in-a-legacy-language-service).  
  
Finalización de palabras rellena los caracteres que faltan en una palabra escrita parcialmente. Si hay solo una finalización posibles, la palabra se completa cuando se escribe el carácter de finalización. Si la palabra parcial coincide con más de una posibilidad, se muestra una lista de finalizaciones posibles. Un carácter de finalización puede ser cualquier carácter que no se usa para los identificadores.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información, consulte [ampliación del Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="implementation-steps"></a>Pasos de implementación  
  
1.  Cuando el usuario selecciona **palabra completa** desde el **IntelliSense** menú, el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando se envía al servicio de lenguaje.  
  
2.  El <xref:Microsoft.VisualStudio.Package.ViewFilter> clase detecta el comando y llama el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  El <xref:Microsoft.VisualStudio.Package.Source> clase, a continuación, llama a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para obtener la lista de finalizaciones posibles palabras y, a continuación, muestra las palabras en una información sobre herramientas lista utilizando el <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.  
  
     Si no hay solo una palabra coincidente, el <xref:Microsoft.VisualStudio.Package.Source> clase completa de la palabra.  
  
 Como alternativa, si el analizador devuelve el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> cuando se escribe el primer carácter de un identificador, el <xref:Microsoft.VisualStudio.Package.Source> clase lo detecta y llama a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con el motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. En este caso el analizador debe detectar la presencia de un carácter de la selección de miembro y proporcionar una lista de miembros.  
  
## <a name="enabling-support-for-the-complete-word"></a>Habilitar la compatibilidad para la palabra completa  
 Para habilitar la compatibilidad para el conjunto de finalizaciones de word la `CodeSense` con el nombre de parámetro pasado a la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado con el paquete de idioma. Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
 El analizador debe devolver una lista de declaraciones en respuesta al análisis motivo valor <xref:Microsoft.VisualStudio.Package.ParseReason>, para la finalización de palabras para que funcione.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementación de la palabra completa en el método ParseSource  
 Para la finalización de palabras, el <xref:Microsoft.VisualStudio.Package.Source> clase llama a la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase para obtener una lista de coincidencias de palabras posible. Debe implementar la lista en una clase que se deriva el <xref:Microsoft.VisualStudio.Package.Declarations> clase. Consulte la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información sobre los métodos que debe implementar.  
  
 Si la lista contiene una sola palabra, el <xref:Microsoft.VisualStudio.Package.Source> clase inserta automáticamente esa palabra en lugar de las palabras parciales. Si la lista contiene más de una palabra, el <xref:Microsoft.VisualStudio.Package.Source> clase presenta una lista de sugerencias de la herramienta desde el que el usuario puede seleccionar la opción más adecuada.  
  
 Examine también el ejemplo de un <xref:Microsoft.VisualStudio.Package.Declarations> implementación de la clase en [finalizaciones de miembros en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).

