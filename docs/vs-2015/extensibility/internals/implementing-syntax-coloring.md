---
title: Implementación de colores de sintaxis | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c86a782b3b100811d29b1f81bf2beb6c8cfae1a0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580274"
---
# <a name="implementing-syntax-coloring"></a>Implementación de colores de la sintaxis
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [implementar colores de sintaxis](https://docs.microsoft.com/visualstudio/extensibility/internals/implementing-syntax-coloring).  
  
Cuando el servicio de lenguaje proporciona la coloración de sintaxis, el analizador convierte una línea de texto en una matriz de elementos coloreables y devuelve los tipos de token correspondientes a estos elementos coloreables. El analizador debe devolver tipos de token que pertenecen a una lista de elementos coloreables. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] cada elemento coloreable se muestra en la ventana de código según los atributos asignados por el objeto de Coloreador para el tipo de token adecuado.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no especifica una interfaz del analizador, y la implementación del analizador es decisión suya. Sin embargo, se proporciona una implementación del analizador de forma predeterminada en el proyecto de paquete de idioma de Visual Studio. Para código administrado, managed package framework (MPF) proporciona compatibilidad completa para colorear el texto.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar los colores de sintaxis, vea [Tutorial: texto resaltado](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Pasos seguidos por un Editor para colorear el texto  
  
1.  El editor Obtiene el Coloreador mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.  
  
2.  Las llamadas de editor el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> método para determinar si el Coloreador requiere el estado de cada línea que se mantenga fuera el Coloreador.  
  
3.  Si el Coloreador requiere el mantenimiento fuera el Coloreador del estado, el editor se llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> método para obtener el estado de la primera línea.  
  
4.  Para cada línea en el búfer, se llama el editor de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método, que lleva a cabo los pasos siguientes:  
  
    1.  La línea de texto se pasa a un escáner para convertir el texto en tokens. Cada token especifica el texto del token y el tipo de token.  
  
    2.  El tipo de token se convierte en un índice en una lista de elementos coloreables.  
  
    3.  La información del token se usa para rellenar una matriz, que cada elemento de la matriz se corresponde con un carácter en la línea. Los valores almacenados en la matriz son los índices en la lista de elementos coloreables.  
  
    4.  Se devuelve el estado al final de la línea para cada línea.  
  
5.  Si el Coloreador requiere el mantenimiento del estado, el editor se almacena en caché el estado de esa línea.  
  
6.  El editor representa la línea de texto con la información devuelta por la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método. Para ello, siga estos pasos:  
  
    1.  Para cada carácter de la línea, obtiene el índice del elemento coloreable.  
  
    2.  Si usa los elementos coloreables de forma predeterminada, tener acceso a la lista de elementos coloreables del editor.  
  
    3.  También puede llamar el servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método para obtener un elemento coloreable.  
  
    4.  Use la información en el elemento coloreable para representar el texto en la pantalla.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Coloreador  
 Managed package framework (MPF) proporciona todas las clases que son necesarios para implementar un Coloreador. La clase de servicio de lenguaje debe heredar la <xref:Microsoft.VisualStudio.Package.LanguageService> clase e implementar los métodos necesarios. Debe proporcionar un escáner y analizador mediante la implementación de la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz y devolver una instancia de esa interfaz desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método (uno de los métodos que deben implementarse en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase). Para obtener más información, consulte [coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

