---
title: Implementar el color de la sintaxis | Microsoft Docs
description: Obtenga información sobre cómo implementar el color de la sintaxis en Visual Studio mediante las características del servicio de lenguaje de Managed Package Framework (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 195cf7a26b1615b7c56f3f0d06cfd9e0d44a4384
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204675"
---
# <a name="implementing-syntax-coloring"></a>Implementación de colores de la sintaxis
Cuando el servicio de lenguaje proporciona coloración de la sintaxis, el analizador convierte una línea de texto en una matriz de elementos coloreables y devuelve tipos de token correspondientes a estos elementos coloreables. El analizador debe devolver tipos de token que pertenezcan a una lista de elementos coloreables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra cada elemento coloreable en la ventana de código según los atributos asignados por el objeto coloreador al tipo de token adecuado.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no especifica una interfaz de analizador y la implementación del analizador es totalmente suya. Sin embargo, se proporciona una implementación de analizador predeterminada en el proyecto de paquete de idioma de Visual Studio. Para el código administrado, el marco de trabajo de paquetes administrados (MPF) proporciona compatibilidad completa con la coloración de texto.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar el color de la sintaxis, vea [Tutorial: resaltar texto](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Pasos seguidos de un editor para colorear el texto

1. El editor obtiene el coloreador llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.

2. El editor llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> método para determinar si el coloreador necesita el estado de cada línea para mantenerse fuera del coloreador.

3. Si el coloreador requiere que el estado se mantenga fuera del coloreador, el editor llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> método para obtener el estado de la primera línea.

4. Para cada línea del búfer, el editor llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método, que realiza los pasos siguientes:

    1. La línea de texto se pasa a un escáner para convertir el texto en tokens. Cada token especifica el texto del token y el tipo de token.

    2. El tipo de token se convierte en un índice en una lista de elementos coloreables.

    3. La información del token se utiliza para rellenar una matriz de modo que cada elemento de la matriz se corresponda con un carácter de la línea. Los valores almacenados en la matriz son los índices de la lista de elementos coloreables.

    4. Se devuelve el estado al final de la línea para cada línea.

5. Si el coloreador requiere que se mantenga el estado, el editor almacena en caché el estado de esa línea.

6. El editor representa la línea de texto utilizando la información devuelta por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método. Para ello, siga estos pasos:

    1. Para cada carácter de la línea, obtenga el índice de elemento coloreable.

    2. Si usa los elementos coloreables predeterminados, acceda a la lista de elementos coloreables del editor.

    3. De lo contrario, llame al método del servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> para obtener un elemento coloreable.

    4. Utilice la información del elemento coloreable para representar el texto en la pantalla.

## <a name="managed-package-framework-colorizer"></a>Coloreador de Managed Package Framework
 El marco de trabajo de paquetes administrados (MPF) proporciona todas las clases necesarias para implementar un coloreador. La clase de servicio de lenguaje debe heredar la <xref:Microsoft.VisualStudio.Package.LanguageService> clase e implementar los métodos necesarios. Debe proporcionar un analizador y un analizador implementando la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz y devolver una instancia de esa interfaz desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método (uno de los métodos que se deben implementar en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase). Para obtener más información, vea [coloración de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Vea también
- [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
