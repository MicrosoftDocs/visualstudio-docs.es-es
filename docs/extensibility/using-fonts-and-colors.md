---
title: Utilizar fuentes y colores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4415d00e5a1233bfdf14dbc86a3a7ed2f7b8e770
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="using-fonts-and-colors"></a>Utilizar fuentes y colores
El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona compatibilidad para que utilizar fuentes y colores para mostrar el texto.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general de Color y fuente](../extensibility/font-and-color-overview.md)  
 Describe la configuración de fuente y color del texto en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). También presenta los conceptos de categorías y mostrar los elementos y describe cómo utilizan los atributos de texto VSPackages y el editor principal.  
  
 [Obtención de fuente y la información de Color para el color de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Proporciona directrices para implementar los colores de texto en los paquetes VSPackage que administran **categorías** distinto de **Editor de texto**.  
  
 [Obtener acceso a la configuración de Color y fuente almacenado](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explica cómo actual fuente y color de configuración se puede almacenar, recuperar y aplicar.  
  
 [Implementación de categorías personalizadas y mostrar los elementos](../extensibility/implementing-custom-categories-and-display-items.md)  
 Describe los pasos básicos mediante el cual puede crear y usar su propio de una ventana **mostrar elementos** y **categorías** para admitir la presentación del texto.  
  
 Este enfoque requiere un VSPackage implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz y las interfaces relacionadas.  
  
 [Cómo: obtener acceso a las fuentes integradas y la combinación de colores](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Describe cómo definir y registrar una categoría mediante el uso de colores y fuentes integradas para iniciar el uso de colores y fuentes proporcionados por el sistema.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Proporciona una instancia de la `IVsFontAndColorDefaults` o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaz que corresponde a un elemento determinado que se muestran en la **Mostrar configuración para** lista en la **fuentes y colores** página de la **Opciones** cuadro de diálogo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permite que un paquete VSPackage admitir el IDE **fuentes y colores** página mediante la definición de las fuentes predeterminadas y los colores de una ventana o un componente de interfaz de usuario.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Proporciona un mecanismo mediante el cual un VSPackage que proporciona soporte técnico de fuente y color puede especificar un grupo de elemento para mostrar - una categoría superobligatorios que representa la unión de dos o más categorías.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permite que un paquete VSPackage recuperar datos de fuente y color, o guardar en el registro.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica a VSPackages que está usando la información de fuente y color sobre los cambios en la configuración de fuente y color.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Proporciona herramientas para trabajar con los datos de entrada y salidos que se usan los métodos de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **fuente y Color** mecanismo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controla el almacenamiento en caché de configuración de fuente y color.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Describe cómo VSPackages puede utilizar servicios de lenguaje para personalizar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
 [Colores de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Se explica cómo el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor usa servicios de lenguaje para implementar los colores de sintaxis.  
  
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services para crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].