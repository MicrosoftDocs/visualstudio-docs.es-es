---
title: Información general sobre fuentes y colores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204347"
---
# <a name="font-and-color-overview"></a>Introducción a fuentes y colores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe la configuración de fuente y color de texto en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) de. También se presentan los conceptos de categorías y elementos para mostrar, y se describe cómo los VSPackages y el editor principal usan atributos de texto.  
  
## <a name="the-fonts-and-colors-property-page"></a>Página de propiedades fuentes y colores  
 Puede administrar los atributos del texto mostrado en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) a través de la página de propiedades **fuentes y colores** . Para buscar la página de propiedades **fuentes y colores** , en el menú **herramientas** , haga clic en **Opciones**. Expanda **Entorno**y haga clic en **Fuentes y colores**.  
  
## <a name="categories-and-display-items"></a>Categorías y mostrar elementos  
 Las fuentes y los colores se organizan en **categorías** y **muestran los elementos**.  
  
- Una **categoría** es un contenedor lógico o funcional para un número de **elementos mostrados**.  
  
   Una lista de **categorías** está en el cuadro desplegable **Mostrar valores para** de la página de propiedades **fuentes y colores** .  
  
- Un **elemento de visualización** es una entidad de texto bien definida, como un comentario, una cadena o una estructura de control que se coloreará cuando se muestre.  
  
  Cada **elemento de presentación** se define de forma única dentro de la **categoría** que lo contiene. Por consiguiente, más de una **categoría** puede tener un **elemento de presentación** con el mismo nombre.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Control VSPackage de fuentes y colores  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Permite que los VSPackages:  
  
- Definir **categorías**de fuente y color.  
  
- Especifique las fuentes y los colores usados para presentar **los elementos para mostrar**.  
  
- Interactúe con la página de propiedades **fuentes y colores** .  
  
- Agregue varias **categorías** a los grupos.  
  
- Conservar los cambios en la configuración predeterminada.  
  
  Hay dos maneras de interactuar con las selecciones de fuente y color dentro de [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Una manera se conoce como color de la *Sintaxis*. Lo usa un VSPackage que personaliza el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor existente para implementar un servicio de lenguaje y crear un editor de código fuente.  
  
   Solo una **categoría** admite este mecanismo, es decir, el **Editor de texto**.  
  
- Una alternativa más general es compatible con todas las demás **categorías** y componentes de la interfaz de usuario que no sean el editor de código fuente al mostrar texto. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Configuración de texto del editor principal  
 La configuración de fuente y color para el editor principal de un objeto de servicio de lenguaje se rige por el **texto EditorCategory** que se encuentra en el cuadro desplegable **Mostrar valores para** de la página de propiedades **fuentes y colores** .  
  
 Al trabajar con editores, debe utilizar el mecanismo de control de color y fuente especializado que el servicio de lenguaje proporciona para controlar y ampliar la configuración del **Editor de texto** . El mecanismo se conoce como *coloreado* de la sintaxis y proporciona:  
  
- Técnica simplificada para administrar las fuentes y los colores de los elementos para mostrar.  
  
   Para obtener más información, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Un mecanismo de coloración bien definido y optimizado.  
  
   Para obtener más información, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- La capacidad de usar los elementos de presentación integrados del **texto EditorCategory** y extenderlos.  
  
   Para obtener más información, vea [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md) y [elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md).  
  
- Persistencia automática del estado actual de los elementos de presentación integrados y personalizados con la categoría **Editor de texto** .  
  
  Para obtener más información sobre el color de la sintaxis, consulte [color de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces heredadas en el editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colores de la sintaxis en un servicio de lenguaje heredado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
