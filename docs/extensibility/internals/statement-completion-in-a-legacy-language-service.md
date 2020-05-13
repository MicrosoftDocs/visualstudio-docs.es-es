---
title: Finalización de la declaración en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704944"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Finalización de instrucciones en un servicio de lenguaje heredado
La finalización de instrucciones es el proceso mediante el cual el servicio de lenguaje ayuda a los usuarios a finalizar una palabra clave de idioma o elemento que han comenzado a escribir en el editor principal. En este tema se describe cómo funciona la finalización de instrucciones y cómo implementarla en el servicio de lenguaje.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar la finalización de instrucciones, vea [Tutorial: Mostrar finalización](../../extensibility/walkthrough-displaying-statement-completion.md)de instrucciones .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementing-statement-completion"></a>Implementación de la finalización de la declaración
 En el editor principal, la finalización de instrucciones activa una interfaz de usuario especial que le ayuda de forma interactiva a escribir código de forma más fácil y rápida. La finalización de instrucciones ayuda al mostrar objetos o clases pertinentes cuando son necesarios, lo que evita tener que recordar elementos específicos o tener que buscarlos en un tema de referencia de ayuda.

 Para implementar la finalización de instrucciones, el idioma debe tener un desencadenador de finalización de instrucciones, que se puede analizar. Por ejemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utiliza un operador de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] punto (.), mientras que utiliza un operador de flecha (->). Un servicio de lenguaje puede usar más de un desencadenador para iniciar la finalización de instrucciones. Estos desencadenadores se programan en el filtro de comandos.

## <a name="command-filters-and-triggers"></a>Filtros y disparadores de comandos
 Los filtros de comandos interceptan las apariciones del desencadenador o los desencadenadores. Para agregar el filtro de comandos a la vista, implemente la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y adjúntela a la vista llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método. Puede usar el mismo<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>filtro de comandos ( ) para todos los aspectos del servicio de lenguaje, como la finalización de instrucciones, marcadores de error y sugerencias de método. Para obtener más información, consulte [Interceptación de comandos](../../extensibility/internals/intercepting-legacy-language-service-commands.md)de servicio de lenguaje heredado .

 Cuando se introduce el desencadenador en el editor, específicamente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> búfer de texto, el servicio de lenguaje llama al método. Esto hace que el editor para que aparece la interfaz de usuario para que el usuario puede elegir entre los candidatos de finalización de la instrucción. Este método requiere que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> implemente <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> y las marcas como parámetros. La lista de elementos de finalización aparece en un cuadro de lista de desplazamiento. A medida que el usuario continúa escribiendo, la selección dentro del cuadro de lista se actualiza para reflejar la coincidencia más cercana a los caracteres más recientes escritos. El editor principal implementa la interfaz de usuario para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> la finalización de instrucciones, pero el servicio de lenguaje debe implementar la interfaz para definir un conjunto de elementos de finalización de candidatos para la instrucción.

## <a name="see-also"></a>Vea también
- [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
