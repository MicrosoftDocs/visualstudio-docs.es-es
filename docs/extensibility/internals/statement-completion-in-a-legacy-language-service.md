---
title: Finalización de instrucciones en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4c813052892c21a6a3e04560452b503205df117
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723220"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Finalización de instrucciones en un servicio de lenguaje heredado
La finalización de instrucciones es el proceso por el que el servicio de lenguaje ayuda a los usuarios a finalizar una palabra clave o un elemento del lenguaje que han empezado a escribir en el editor básico. En este tema se describe cómo funciona la finalización de instrucciones y cómo implementarla en el servicio de lenguaje.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar la finalización de instrucciones, vea [Tutorial: Mostrar la finalización de instrucciones](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementing-statement-completion"></a>Implementación de la finalización de instrucciones
 En el editor principal, la finalización de instrucciones activa una interfaz de usuario especial que ayuda interactivamente a escribir código de forma más fácil y rápida. La finalización de instrucciones ayuda a mostrar objetos o clases relevantes cuando son necesarios, lo que evita tener que recordar elementos específicos o tener que buscarlos en un tema de referencia de la ayuda.

 Para implementar la finalización de instrucciones, el lenguaje debe tener un desencadenador de finalización de instrucciones, que se puede analizar. Por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usa un operador punto (.), mientras que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] usa un operador de flecha (->). Un servicio de lenguaje puede utilizar más de un desencadenador para iniciar la finalización de instrucciones. Estos desencadenadores se programan en el filtro de comandos.

## <a name="command-filters-and-triggers"></a>Desencadenadores y filtros de comandos
 Los filtros de comandos interceptan las repeticiones de los desencadenadores o desencadenadores. Para agregar el filtro de comandos a la vista, implemente la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> y adjúntela a la vista llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Puede usar el mismo filtro de comandos (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) para todos los aspectos del servicio de lenguaje, como la finalización de instrucciones, los marcadores de error y las sugerencias de método. Para obtener más información, consulte [interceptar comandos de servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Cuando el desencadenador se especifica en el editor, en concreto, el búfer de texto, el servicio de lenguaje llama entonces al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>. Esto hace que el editor muestre la interfaz de usuario para que el usuario pueda elegir entre los candidatos para completar la instrucción. Este método requiere la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> y las marcas de <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> como parámetros. La lista de elementos de finalización aparece en un cuadro de lista desplazable. A medida que el usuario sigue escribiendo, la selección en el cuadro de lista se actualiza para reflejar la coincidencia más cercana a los caracteres más recientes escritos. El editor principal implementa la interfaz de usuario para la finalización de instrucciones, pero el servicio de lenguaje debe implementar la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> para definir un conjunto de elementos de finalización candidata para la instrucción.

## <a name="see-also"></a>Vea también
- [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)