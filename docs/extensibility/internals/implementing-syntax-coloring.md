---
title: Implementación de la coloración de sintaxis ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707645"
---
# <a name="implementing-syntax-coloring"></a>Implementación de colores de la sintaxis
Cuando el servicio de lenguaje proporciona coloración de sintaxis, el analizador convierte una línea de texto en una matriz de elementos coloreables y devuelve tipos de token correspondientes a estos elementos coloreables. El analizador debe devolver tipos de token que pertenecen a una lista de elementos coloreables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]muestra cada elemento coloreable en la ventana de código según los atributos asignados por el objeto colorizer al tipo de token adecuado.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]no especifica una interfaz de analizador y la implementación del analizador depende completamente de usted. Sin embargo, se proporciona una implementación de analizador predeterminada en el proyecto paquete de lenguaje de Visual Studio. Para el código administrado, el marco de paquete administrado (MPF) proporciona compatibilidad completa para colorear texto.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar el color de sintaxis, consulte [Tutorial: Resaltar texto](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Pasos seguidos por un editor para colorear texto

1. El editor obtiene el colorante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> llamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> al método en el objeto.

2. El editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> llama al método para determinar si el colorante necesita que el estado de cada línea se mantenga fuera del colorante.

3. Si el colorizador requiere que el estado se mantenga fuera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> del colorizador, el editor llama al método para obtener el estado de la primera línea.

4. Para cada línea del búfer, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> el editor llama al método, que realiza los pasos siguientes:

    1. La línea de texto se pasa a un analizador para convertir el texto en tokens. Cada token especifica el texto del token y el tipo de token.

    2. El tipo de token se convierte en un índice en una lista de elementos coloreables.

    3. La información del token se utiliza para rellenar una matriz de modo que cada elemento de la matriz corresponda a un carácter de la línea. Los valores almacenados en la matriz son los índices de la lista de elementos coloreables.

    4. El estado al final de la línea se devuelve para cada línea.

5. Si el colorizador requiere que se mantenga el estado, el editor almacena en caché el estado de esa línea.

6. El editor representa la línea de texto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> utilizando la información devuelta por el método. Para ello, siga estos pasos:

    1. Para cada carácter de la línea, obtenga el índice de elementos coloreables.

    2. Si utiliza los elementos coloreables predeterminados, acceda a la lista de elementos coloreables del editor.

    3. De lo contrario, llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> al método del servicio de lenguaje para obtener un elemento coloreable.

    4. Utilice la información del elemento coloreable para representar el texto en la pantalla.

## <a name="managed-package-framework-colorizer"></a>Colorizador de marco de paquetes administrados
 El marco de paquete administrado (MPF) proporciona todas las clases necesarias para implementar un colorante. La clase de servicio <xref:Microsoft.VisualStudio.Package.LanguageService> de lenguaje debe heredar la clase e implementar los métodos necesarios. Debe proporcionar un analizador y un <xref:Microsoft.VisualStudio.Package.IScanner> analizador implementando la interfaz <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> y devolver una instancia de esa <xref:Microsoft.VisualStudio.Package.LanguageService> interfaz desde el método (uno de los métodos que se deben implementar en la clase). Para obtener más información, vea [Colorear sintaxis en un servicio](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)de lenguaje heredado .

## <a name="see-also"></a>Vea también
- [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
