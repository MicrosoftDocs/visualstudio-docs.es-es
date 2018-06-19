---
title: Implementación de colores de sintaxis | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131860"
---
# <a name="implementing-syntax-coloring"></a>Color de la sintaxis de implementación
Cuando el servicio de lenguaje proporciona colores de sintaxis, el analizador convierte una línea de texto en una matriz de elementos coloreables y devuelve los tipos de token correspondientes a estos elementos coloreables. El analizador debe devolver tipos de token que pertenecen a una lista de elementos coloreables. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra cada elemento coloreable en la ventana de código según los atributos asignados por el objeto de aplicador de color para el tipo de token adecuado.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no se especifica una interfaz de analizador, y la implementación de analizador es decisión suya. Sin embargo, se proporciona una implementación de analizador de forma predeterminada en el proyecto de paquete de idioma de Visual Studio. Para código administrado, managed package framework (MPF) proporciona total compatibilidad para colorear texto.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información sobre la nueva manera de implementar el color de sintaxis, vea [Tutorial: texto resaltado](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Pasos seguidos por un Editor para colorear el texto  
  
1.  El editor Obtiene el aplicador de color mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.  
  
2.  Las llamadas de editor el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> método para determinar si es necesario el estado de cada línea se mantenga fuera del aplicador de color del aplicador de color.  
  
3.  Si el aplicador de color requiere que el estado se mantenga fuera del aplicador de color, el editor llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> método para obtener el estado de la primera línea.  
  
4.  Para cada línea en el búfer, se llama el editor de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método, que realiza los pasos siguientes:  
  
    1.  La línea de texto se pasa a un escáner para convertir el texto en tokens. Cada token especifica el texto del token y el tipo de token.  
  
    2.  El tipo de token se convierte en un índice en una lista de elementos coloreable.  
  
    3.  La información del token se usa para rellenar una matriz de forma que cada elemento de la matriz corresponde a un carácter en la línea. Los valores almacenados en la matriz son los índices en la lista de elementos coloreable.  
  
    4.  Se devuelve el estado al final de la línea para cada línea.  
  
5.  Si el aplicador de color requiere el mantenimiento del estado, el editor se almacena en caché el estado de esa línea.  
  
6.  El editor representa la línea de texto que usa la información devuelta por la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método. Para ello, siga estos pasos:  
  
    1.  Para cada carácter de la línea, obtener el índice del elemento coloreable.  
  
    2.  Si utiliza los elementos coloreable predeterminados, tener acceso a lista de elementos coloreable del editor.  
  
    3.  De lo contrario, llame al servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método para obtener un elemento coloreable.  
  
    4.  Use la información en el elemento coloreable para representar el texto en la pantalla.  
  
## <a name="managed-package-framework-colorizer"></a>Aplicador de color de Managed Package Framework  
 Managed package framework (MPF) proporciona todas las clases necesitan para implementar un aplicador de color. La clase de servicio de lenguaje debe heredar el <xref:Microsoft.VisualStudio.Package.LanguageService> clase e implementar los métodos necesarios. Debe proporcionar un analizador y el analizador implementando la <xref:Microsoft.VisualStudio.Package.IScanner> de interfaz y devolver una instancia de la interfaz de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (método) (uno de los métodos que deben implementarse en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase). Para obtener más información, consulte [coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)