---
title: "Finalización de instrucciones en un servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7208d38966e2caa9f9510c48c34952742d06c1b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Finalización de instrucciones en un servicio de lenguaje heredado
Finalización de instrucciones es el proceso por el que el servicio de lenguaje ayuda a los usuarios finalizar una palabra clave de lenguaje o el elemento que se hayan iniciado escribiéndolos en el editor principal. Este tema describe cómo funciona la finalización de instrucciones y cómo se implementa en el servicio de lenguaje.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar la finalización de instrucciones, consulte [Tutorial: mostrar la finalización de instrucciones](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="implementing-statement-completion"></a>Implementación de la finalización de instrucciones  
 En el editor principal, la finalización de instrucciones activa una interfaz de usuario especial que interactivamente le ayuda a más fácilmente y escribe rápidamente código. Le ayuda la finalización de instrucciones mostrando objetos relevantes o clases cuando son necesarias, se evita tener que recordar elementos concretos o tener que buscarlos en un tema de referencia de ayuda.  
  
 Para implementar la finalización de instrucciones, el lenguaje debe tener un desencadenador de finalización de la instrucción, que se puede analizar. Por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usa un operador de punto (.), mientras que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] usa una flecha (->) (operador). Un servicio de lenguaje puede utilizar más de un desencadenador para iniciar la finalización de instrucciones. Estos desencadenadores se programan en el filtro de comandos.  
  
## <a name="command-filters-and-triggers"></a>Filtros de comandos y los desencadenadores  
 Comandos filtros interceptan las apariciones del desencadenador o desencadenadores. Para agregar el filtro de comandos a la vista, implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y adjuntarlo a la vista mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Puede usar el mismo filtro de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) para todos los aspectos de su servicio de lenguaje, como la finalización de instrucciones, los marcadores de error y sugerencias de método. Para obtener más información, consulte [interceptando comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Cuando el desencadenador se registran en el editor: en concreto, el búfer de texto: el servicio de lenguaje, a continuación, llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método. Esto hace que el editor para que aparezca la interfaz de usuario para que el usuario puede elegir entre los candidatos de finalización de la instrucción. Este método exige que implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> y <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> marcas como parámetros. Aparece la lista de elementos de la finalización en un cuadro de lista desplegable. Como el usuario continúa escribiendo, la selección en el cuadro de lista se actualiza para reflejar que la coincidencia más cercana a los caracteres más reciente con tipo. El editor de núcleo implementa la interfaz de usuario para la finalización de instrucciones, pero debe implementar el servicio de lenguaje el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz para definir un conjunto de elementos de la finalización de candidato para la instrucción.  
  
## <a name="see-also"></a>Vea también  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)