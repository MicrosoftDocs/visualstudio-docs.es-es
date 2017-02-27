---
title: "Finalizaci&#243;n de palabras en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje [managed package framework], palabra completa de IntelliSense"
  - "IntelliSense, palabra completa"
  - "Palabra completa"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Finalizaci&#243;n de palabras en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Finalización de Word rellena los caracteres que faltan en una palabra escrita parcialmente. Si hay sólo una finalización posibles, la palabra se completa cuando se escribe el carácter de finalización. Si la palabra parcial coincide con más de una posibilidad, se muestra una lista de finalizaciones posibles. Una terminación de carácter puede ser cualquier carácter que no se usa para los identificadores.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## Pasos de implementación  
  
1.  Cuando el usuario selecciona **palabra completa** desde el **IntelliSense** menú, el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando se envía al servicio de lenguaje.  
  
2.  La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase detecta el comando y llama el <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con la razón para el análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  La <xref:Microsoft.VisualStudio.Package.Source> clase, a continuación, llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método para obtener la lista de finalizaciones de posibles palabras y, a continuación, muestra las palabras en una información sobre herramientas mostrar mediante el <xref:Microsoft.VisualStudio.Package.CompletionSet> clase.  
  
     Si hay sólo una palabra coincidente, la <xref:Microsoft.VisualStudio.Package.Source> clase completa de la palabra.  
  
 Como alternativa, si el analizador devuelve el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> cuando se escribe el primer carácter de un identificador, la <xref:Microsoft.VisualStudio.Package.Source> clase lo detecta y llama a la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método con la razón para el análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. En este caso el analizador debe detectar la presencia de un carácter de la selección de miembro y proporcionar una lista de miembros.  
  
## Habilitar la compatibilidad para la palabra completa  
 Para habilitar la compatibilidad para el conjunto de finalizaciones de word el `CodeSense` con el nombre de parámetro se pasa a la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo de usuario asociado con el paquete de idioma. Esto establece el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
 El analizador debe devolver una lista de declaraciones en respuesta al valor de la razón de análisis <xref:Microsoft.VisualStudio.Package.ParseReason>, finalización de word funcionar.  
  
## Implementación de palabra completa en el método ParseSource  
 Finalización de word, la <xref:Microsoft.VisualStudio.Package.Source> clase llamadas el <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método en la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase para obtener una lista de posibles coincidencias. La lista debe implementar en una clase que se deriva la <xref:Microsoft.VisualStudio.Package.Declarations> clase. Consulte la <xref:Microsoft.VisualStudio.Package.Declarations> clase para obtener más información sobre los métodos que debe implementar.  
  
 Si la lista contiene una sola palabra, la <xref:Microsoft.VisualStudio.Package.Source> clase inserta automáticamente esa palabra en lugar de la palabra parcial. Si la lista contiene más de una palabra, el <xref:Microsoft.VisualStudio.Package.Source> clase presenta una lista de sugerencias de la herramienta desde el que el usuario puede seleccionar la opción adecuada.  
  
 Examine también el ejemplo de un <xref:Microsoft.VisualStudio.Package.Declarations> la implementación de clase en [Finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).