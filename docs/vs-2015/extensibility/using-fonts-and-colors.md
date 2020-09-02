---
title: Usar fuentes y colores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177223"
---
# <a name="using-fonts-and-colors"></a>Uso de fuentes y colores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Proporciona compatibilidad para usar fuentes y colores para mostrar texto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general sobre fuentes y colores](../extensibility/font-and-color-overview.md)  
 Describe la configuración de fuente y color de texto en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) de. También presenta los conceptos de las categorías y los elementos para mostrar, y describe cómo los VSPackages y el editor principal usan atributos de texto.  
  
 [Obtención de información sobre fuentes y colores para la coloración de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Proporciona instrucciones para implementar la coloración de texto en VSPackages que administran **categorías** que no sean el **Editor de texto**.  
  
 [Acceso a la configuración de fuentes y colores almacenados](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explica cómo se pueden almacenar, recuperar y aplicar la configuración de fuente y color actual.  
  
 [Implementación de categorías y elementos para mostrar personalizados](../extensibility/implementing-custom-categories-and-display-items.md)  
 Describe los pasos básicos por los que una ventana puede crear y usar su propio de **Mostrar elementos** y **categorías** para admitir la presentación de texto.  
  
 Este enfoque requiere un VSPackage para implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz y las interfaces relacionadas.  
  
 [Cómo: Acceder al esquema integrado de fuentes y colores](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Describe cómo definir y registrar una categoría usando fuentes y colores integrados e iniciar el uso de fuentes y colores proporcionados por el sistema.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Proporciona una instancia de `IVsFontAndColorDefaults` o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaz que corresponde a un elemento determinado que se muestra en la lista **Mostrar valores para** en la página **fuentes y colores** del cuadro de diálogo **Opciones** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permite que un VSPackage admita la página **fuentes y colores** del IDE definiendo fuentes y colores predeterminados para una ventana o un componente de la interfaz de usuario.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Proporciona un mecanismo por el que un VSPackage que proporciona compatibilidad de fuente y color puede especificar un grupo de elementos para mostrar (una supercategoría que representa la Unión de dos o más categorías).  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Habilita un VSPackage para recuperar los datos de fuente y color, o guardarlos en el registro.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica a los VSPackages que usan información de fuente y color sobre los cambios en la configuración de fuente y color.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Proporciona herramientas para trabajar con los datos de entrada y salida que usan los métodos del mecanismo de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **color y fuente** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controla el almacenamiento en memoria caché de la configuración de fuente y color.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Describe cómo los VSPackages pueden utilizar los servicios de lenguaje para personalizar el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
 [Colores de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries cómo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utiliza el editor los servicios de lenguaje para implementar el color de la sintaxis.  
  
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
