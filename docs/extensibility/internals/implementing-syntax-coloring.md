---
title: Implementar el color de la sintaxis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cab338e253cca8c7f8457752980e7f3624317d9c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727038"
---
# <a name="implementing-syntax-coloring"></a>Implementación de colores de la sintaxis
Cuando el servicio de lenguaje proporciona coloración de la sintaxis, el analizador convierte una línea de texto en una matriz de elementos coloreables y devuelve tipos de token correspondientes a estos elementos coloreables. El analizador debe devolver tipos de token que pertenezcan a una lista de elementos coloreables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra cada elemento coloreable en la ventana de código según los atributos asignados por el objeto coloreador al tipo de token adecuado.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no especifica una interfaz de analizador y la implementación del analizador es totalmente suya. Sin embargo, se proporciona una implementación de analizador predeterminada en el proyecto de paquete de idioma de Visual Studio. Para el código administrado, el marco de trabajo de paquetes administrados (MPF) proporciona compatibilidad completa con la coloración de texto.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar el color de la sintaxis, vea [Tutorial: resaltar texto](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Pasos seguidos de un editor para colorear el texto

1. El editor obtiene el coloreador llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> en el objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>.

2. El editor llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> para determinar si el coloreador necesita el estado de cada línea para mantenerse fuera del coloreador.

3. Si el coloreador requiere que el estado se mantenga fuera del coloreador, el editor llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> para obtener el estado de la primera línea.

4. Para cada línea del búfer, el editor llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, que realiza los pasos siguientes:

    1. La línea de texto se pasa a un escáner para convertir el texto en tokens. Cada token especifica el texto del token y el tipo de token.

    2. El tipo de token se convierte en un índice en una lista de elementos coloreables.

    3. La información del token se utiliza para rellenar una matriz de modo que cada elemento de la matriz se corresponda con un carácter de la línea. Los valores almacenados en la matriz son los índices de la lista de elementos coloreables.

    4. Se devuelve el estado al final de la línea para cada línea.

5. Si el coloreador requiere que se mantenga el estado, el editor almacena en caché el estado de esa línea.

6. El editor representa la línea de texto utilizando la información devuelta por el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>. Para ello, siga estos pasos:

    1. Para cada carácter de la línea, obtenga el índice de elemento coloreable.

    2. Si usa los elementos coloreables predeterminados, acceda a la lista de elementos coloreables del editor.

    3. De lo contrario, llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> del servicio de lenguaje para obtener un elemento coloreable.

    4. Utilice la información del elemento coloreable para representar el texto en la pantalla.

## <a name="managed-package-framework-colorizer"></a>Coloreador de Managed Package Framework
 El marco de trabajo de paquetes administrados (MPF) proporciona todas las clases necesarias para implementar un coloreador. La clase de servicio de lenguaje debe heredar la clase <xref:Microsoft.VisualStudio.Package.LanguageService> e implementar los métodos necesarios. Debe proporcionar un escáner y un analizador implementando la interfaz <xref:Microsoft.VisualStudio.Package.IScanner> y devolver una instancia de esa interfaz desde el método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (uno de los métodos que se deben implementar en la clase <xref:Microsoft.VisualStudio.Package.LanguageService>). Para obtener más información, vea [coloración de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Vea también
- [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)