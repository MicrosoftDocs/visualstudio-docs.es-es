---
title: Información general de Color y fuente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 75db379b6a94d0c40fdbc1aa3946315f5fbc4edc
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498475"
---
# <a name="font-and-color-overview"></a>Información general de fuente y color
Este tema describe la configuración de fuente y color del texto en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). También se presentan los conceptos de categorías y mostrar los elementos, y describe cómo VSPackages y el editor principal de utilizan los atributos de texto.  
  
## <a name="the-fonts-and-colors-property-page"></a>Las fuentes y colores propiedad página  
 Puede administrar los atributos de texto mostrado en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) a través de la **fuentes y colores** página de propiedades. Para buscar el **fuentes y colores** página de propiedades, en el **herramientas** menú, haga clic en **opciones**. Expanda **entorno**y, a continuación, haga clic en **fuentes y colores**.  
  
## <a name="categories-and-display-items"></a>Categorías y mostrar los elementos  
 Fuentes y colores se organizan en **categorías** y **mostrar los elementos**.  
  
-   Un **categoría** es un contenedor lógico o funcional para un número de **mostrar los elementos**.  
  
     Una lista de **categorías** está en el **mostrar valores para** cuadro de lista desplegable de la **fuentes y colores** página de propiedades.  
  
-   Un **Mostrar artículo** es una entidad de texto bien definido como un comentario, una cadena o una estructura de control es que se coloreará cuando aparezca.  
  
 Cada **Mostrar artículo** se define de forma única dentro de la **categoría** que lo contiene. Por lo tanto, más de un **categoría** puede tener un **Mostrar artículo** con el mismo nombre.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage control de fuentes y colores  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permite que los VSPackages para:  
  
-   Definir color y fuente **categorías**.  
  
-   Especifique las fuentes y colores usados para presentar **mostrar los elementos**.  
  
-   Interactuar con el **fuentes y colores** página de propiedades.  
  
-   Agregado varios **categorías** en grupos.  
  
-   Conservar los cambios en la configuración predeterminada.  
  
 Hay dos formas de interactuar con las selecciones de fuente y color dentro de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Una manera se conoce como *colores de sintaxis*. Se usa un VSPackage que personaliza existente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor para implementar un servicio de lenguaje y a crear un origen de editor.  
  
     Solo un **categoría** es compatible con este mecanismo, es decir, el **Editor de texto**.  
  
-   Una alternativa más general es compatible con todos los demás **categorías** y componentes de interfaz de usuario que no sea el editor de código fuente para mostrar texto. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Configuración de texto del editor de núcleo  
 Configuración de fuente y color para el editor básico de un objeto de servicio de lenguaje se rige por la **texto EditorCategory** se encuentra en la **mostrar valores para** cuadro de lista desplegable de la **fuentes y colores** página de propiedades.  
  
 Cuando se trabaja con los editores, debe usar la fuente especializado y el mecanismo de control de color que proporciona el servicio de lenguaje para controlar y ampliar el **Editor de texto** configuración. El mecanismo se denomina *colores de sintaxis* y proporciona:  
  
-   Una técnica simplificada para administrar las fuentes y colores de elementos para mostrar.  
  
     Para obtener más información, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un mecanismo de coloración bien definidos y optimizados.  
  
     Para obtener más información, consulta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   Tanto la capacidad de usar los elementos de visualización integradas de la **EditorCategory texto** y a ampliarlos.  
  
     Para obtener más información, consulte [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md) y [elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistencia automática del estado de ambos integrados y personalizado actual mostrar los elementos con el **Editor de texto** categoría.  
  
 Para obtener más información sobre la sintaxis de color vea [colores de sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vea también  
 [Interfaces heredadas en el editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colores de sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)