---
title: Finalización de instrucciones en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 163eb0f23716fa2f036d07612b741c0c9419b92e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842699"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Finalización de instrucciones en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La finalización de instrucciones es el proceso por el que el servicio de lenguaje ayuda a los usuarios a finalizar una palabra clave o un elemento del lenguaje que han empezado a escribir en el editor básico. En este tema se describe cómo funciona la finalización de instrucciones y cómo implementarla en el servicio de lenguaje.  
  
 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar la finalización de instrucciones, vea [Tutorial: Mostrar la finalización de instrucciones](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.  
  
## <a name="implementing-statement-completion"></a>Implementación de la finalización de instrucciones  
 En el editor principal, la finalización de instrucciones activa una interfaz de usuario especial que ayuda interactivamente a escribir código de forma más fácil y rápida. La finalización de instrucciones ayuda a mostrar objetos o clases relevantes cuando son necesarios, lo que evita tener que recordar elementos específicos o tener que buscarlos en un tema de referencia de la ayuda.  
  
 Para implementar la finalización de instrucciones, el lenguaje debe tener un desencadenador de finalización de instrucciones, que se puede analizar. Por ejemplo, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] usa un operador punto (.), mientras que [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] utiliza un operador de flecha (->). Un servicio de lenguaje puede utilizar más de un desencadenador para iniciar la finalización de instrucciones. Estos desencadenadores se programan en el filtro de comandos.  
  
## <a name="command-filters-and-triggers"></a>Desencadenadores y filtros de comandos  
 Los filtros de comandos interceptan las repeticiones de los desencadenadores o desencadenadores. Para agregar el filtro de comandos a la vista, implemente la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y adjúntela a la vista mediante una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Puede usar el mismo filtro de comandos ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) para todos los aspectos del servicio de lenguaje, como la finalización de instrucciones, los marcadores de error y las sugerencias de método. Para obtener más información, consulte [interceptar comandos de servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Cuando el desencadenador se especifica en el editor, en concreto, el búfer de texto, el servicio de lenguaje llama entonces al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método. Esto hace que el editor muestre la interfaz de usuario para que el usuario pueda elegir entre los candidatos para completar la instrucción. Este método requiere la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> y las <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> marcas como parámetros. La lista de elementos de finalización aparece en un cuadro de lista desplazable. A medida que el usuario sigue escribiendo, la selección en el cuadro de lista se actualiza para reflejar la coincidencia más cercana a los caracteres más recientes escritos. El editor principal implementa la interfaz de usuario para la finalización de instrucciones, pero el servicio de lenguaje debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz para definir un conjunto de elementos de finalización candidata para la instrucción.  
  
## <a name="see-also"></a>Consulte también  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
