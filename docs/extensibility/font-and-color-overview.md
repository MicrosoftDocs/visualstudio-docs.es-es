---
title: "Información general de Color y fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13a2a8b584af507f8937fd6abb46c85f329de0b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="font-and-color-overview"></a>Información general de Color y fuente
Este tema describe la configuración de fuente y color del texto en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). También se presentan los conceptos de categorías y mostrar los elementos y describe cómo el editor básico y VSPackages usan atributos de texto.  
  
## <a name="the-fonts-and-colors-property-page"></a>La página de propiedad de colores y fuentes  
 Puede administrar los atributos de texto mostrado en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) a través de la **fuentes y colores** página de propiedades. Para buscar el **fuentes y colores** página de propiedades, en la **herramientas** menú, haga clic en **opciones**. Expanda **entorno**y, a continuación, haga clic en **fuentes y colores**.  
  
## <a name="categories-and-display-items"></a>Categorías y mostrar los elementos  
 Fuentes y colores se organizan en **categorías** y **elementos para mostrar**.  
  
-   A **categoría** es un contenedor lógico o funcional para un número de **elementos para mostrar**.  
  
     Una lista de **categorías** está en el **mostrar valores para** cuadro de lista desplegable de la **fuentes y colores** página de propiedades.  
  
-   A **elemento para mostrar** es una entidad de texto bien definido como un comentario, una cadena o una estructura de control que se colorea cuando aparezca.  
  
 Cada **elemento para mostrar** se define de forma única dentro de la **categoría** que lo contiene. Por lo tanto, más de un **categoría** puede tener un **elemento para mostrar** con el mismo nombre.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Control de VSPackage de fuentes y colores  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permite VSPackages para:  
  
-   Definir la fuente y color **categorías**.  
  
-   Especificar las fuentes y los colores utilizados para presentar **elementos para mostrar**.  
  
-   Interactuar con el **fuentes y colores** página de propiedades.  
  
-   Agregado varios **categorías** en grupos.  
  
-   Conservar los cambios en la configuración predeterminada.  
  
 Hay dos formas de interactuar con las selecciones de fuente y color dentro de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Una manera se conoce como *colores de sintaxis*. Se utiliza por un paquete VSPackage que personaliza existente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor para implementar un servicio de lenguaje y crear un origen de editor.  
  
     Solo un **categoría** es compatible con este mecanismo, es decir, el **Editor de texto**.  
  
-   Una alternativa más general es compatible con todos los demás **categorías** y componentes de la interfaz de usuario que no sea el editor de código fuente para mostrar texto. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Configuración de texto del Editor de núcleo  
 Configuración de fuente y color para el editor principal de un objeto de servicio de lenguaje se rige por la **EditorCategory de texto** se encuentra en la **mostrar valores para** cuadro de lista desplegable de la **fuentes y colores** página de propiedades.  
  
 Cuando se trabaja con editores, debe usar la fuente especializada y el mecanismo de control de color que proporciona el servicio de lenguaje para controlar y ampliar la **Editor de texto** configuración. El mecanismo se conoce como *colorear la sintaxis* y proporciona:  
  
-   Una técnica simplificada para administrar las fuentes y colores de elementos para mostrar.  
  
     Para obtener más información, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un mecanismo de coloración bien definidos y optimizados.  
  
     Para obtener más información, consulta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La capacidad de ambos usan elementos de pantalla integrada desde la **EditorCategory de texto** y ampliarlas.  
  
     Para obtener más información, consulte [Cómo: Use los elementos integrados coloreable](../extensibility/internals/how-to-use-built-in-colorable-items.md) y [elementos coloreable personalizado](../extensibility/internals/custom-colorable-items.md).  
  
-   La persistencia automática del actual estado de ambos integrados y personalizado mostrar los elementos con el **Editor de texto** categoría.  
  
 Para obtener más información acerca de la sintaxis color vea [sintaxis de color en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vea también  
 [Interfaces heredadas en el Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colores de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)