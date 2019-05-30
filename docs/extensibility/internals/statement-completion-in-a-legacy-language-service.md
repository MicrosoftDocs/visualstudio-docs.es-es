---
title: Finalización de instrucciones en un servicio de lenguaje heredado | Documentos de Microsoft
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
ms.openlocfilehash: 5c6e157505b146b9c1ca37f508311c9e80958be6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322442"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Finalización de instrucciones en un servicio de lenguaje heredado
Finalización de instrucciones es el proceso por el que el servicio de lenguaje ayuda a los usuarios finalizar una palabra clave del lenguaje o el elemento que se haya iniciado escribiendo en el editor básico. Este tema describe cómo funciona la finalización de instrucciones y cómo implementarlo en su servicio de lenguaje.

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar la finalización de instrucciones, consulte [Tutorial: Mostrar la finalización de instrucciones](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.

## <a name="implementing-statement-completion"></a>Finalización de instrucciones de implementación
 Finalización de instrucciones en el editor básico, activa una interfaz de usuario especial que interactivamente le ayuda con más facilidad y escribe rápidamente código. Ayuda de finalización de instrucciones mostrando objetos relevantes o clases cuando se necesitan, lo que evita tener que recordar los elementos específicos o tener que buscarlos en un tema de referencia de ayuda.

 Para implementar la finalización de instrucciones, el lenguaje debe tener un desencadenador de finalización de instrucción, que se puede analizar. Por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usa un operador punto (.), mientras que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] usa una flecha (->) (operador). Un servicio de lenguaje puede usar más de un desencadenador para iniciar la finalización de instrucciones. Estos desencadenadores se programan en el filtro de comandos.

## <a name="command-filters-and-triggers"></a>Filtros de comandos y los desencadenadores
 Comando filtros interceptan las repeticiones del desencadenador o desencadenadores. Para agregar el filtro de comandos a la vista, implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y adjuntarlo a la vista mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Puede usar el mismo filtro de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) para todos los aspectos de su servicio de lenguaje, como la finalización de instrucciones, los marcadores de error y sugerencias de método. Para obtener más información, consulte [intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Cuando el desencadenador se escribe en el editor, en concreto, el búfer de texto: el servicio de lenguaje, a continuación, llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método. Esto hace que el editor para que aparezca la interfaz de usuario para que el usuario puede elegir entre los candidatos de finalización de instrucción. Este método exige que implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> y <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> marcas como parámetros. Aparece la lista de elementos de finalización en un cuadro de lista desplazable. Como el usuario continúa escribiendo, la selección en el cuadro de lista se actualiza para reflejar que la coincidencia más cercana a los caracteres más reciente escrito. El editor principal implementa la interfaz de usuario para la finalización de instrucciones, pero debe implementar el servicio de lenguaje el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz para definir un conjunto de elementos de finalización de candidatos para la instrucción.

## <a name="see-also"></a>Vea también
- [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)