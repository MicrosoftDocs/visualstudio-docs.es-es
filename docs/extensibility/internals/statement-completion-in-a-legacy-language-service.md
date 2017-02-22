---
title: "Finalizaci&#243;n de instrucciones en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "finalización de instrucciones"
  - "Servicios de lenguaje, finalización de instrucciones"
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Finalizaci&#243;n de instrucciones en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Finalización de instrucciones es el proceso por el que el servicio de lenguaje ayuda a los usuarios finalizar una palabra clave o un elemento que se haya iniciado escribiendo en el editor principal. Este tema describe cómo funciona la finalización de instrucciones y cómo se implementa en el servicio de lenguaje.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma para implementar la finalización de instrucciones, consulte [Tutorial: Mostrar la finalización de instrucciones](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## Finalización de instrucciones de implementación  
 Finalización de instrucciones en el editor principal, activa una interfaz de usuario especial que ayuda interactiva más fácilmente y escribe rápidamente código. Ayuda de finalización de instrucciones mostrando objetos relevantes o clases cuando son necesarias, lo que evita tener que recordar elementos específicos o tener que buscarlos en un tema de referencia de ayuda.  
  
 Para implementar la finalización de instrucciones, su lenguaje debe tener un desencadenador de finalización de la instrucción, que se puede analizar. Por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utiliza un punto \(.\) operador, mientras [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] usa una flecha \(\-\>\) \(operador\). Un servicio de lenguaje puede utilizar más de un desencadenador para iniciar la finalización de instrucciones. Estos desencadenadores se programan en el filtro de comandos.  
  
## Filtros de comandos y desencadenadores  
 Comandos filtros interceptan las apariciones del desencadenador o desencadenadores. Para agregar el filtro de comandos a la vista, implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de la interfaz y adjuntarlo a la vista mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> \(método\). Puede usar el mismo filtro de comando \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) para todos los aspectos de su servicio de lenguaje, como la finalización de instrucciones, los marcadores de error y sugerencias de método. Para obtener más información, consulta [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Cuando se especifica el desencadenador en el editor: en concreto, el búfer de texto: el servicio de lenguaje, a continuación, llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> \(método\). Esto hace que el editor para que aparezca la interfaz de usuario para que el usuario puede elegir entre los candidatos de finalización de la instrucción. Este método exige que implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> y la <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> marcas como parámetros. La lista de elementos de finalización aparece en un cuadro de lista desplegable. Como el usuario continúa escribiendo, la selección dentro del cuadro de lista se actualiza para reflejar que la coincidencia más cercana a los caracteres más reciente escrito. El editor principal implementa la interfaz de usuario para completar la instrucción, pero debe implementar el servicio de lenguaje el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz para definir un conjunto de elementos de la finalización de candidato para la instrucción.  
  
## Vea también  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)