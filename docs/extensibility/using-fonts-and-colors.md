---
title: "Utilizar fuentes y colores | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fuentes, controlar en IDE"
  - "IDE, controlar el color del texto y fuentes"
  - "Página de propiedades de fuentes y colores"
  - "control de fuente y color [Visual Studio SDK]"
  - "texto, IDE"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilizar fuentes y colores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona compatibilidad para utilizar fuentes y colores para mostrar texto.  
  
## En esta sección  
 [Introducción de Color y fuente](../extensibility/font-and-color-overview.md)  
 Describe la fuente de texto y definiciones de colores en el entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  También presenta conceptos de categorías y los elementos de la pantalla, y describe cómo VSPackages y el editor básico utilizan atributos de texto.  
  
 [Obtención de información de Color para los colores de texto y de fuente](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Proporciona instrucciones para implementar el color del texto en VSPackages que administran **Categorías** distinto de **Editor de texto**.  
  
 [Obtener acceso a la configuración de Color y fuente almacenado](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explica cómo la fuente actual y las definiciones de colores se pueden almacenar, recuperar, y aplicarse.  
  
 [Implementación de categorías personalizadas y mostrar los elementos](../extensibility/implementing-custom-categories-and-display-items.md)  
 Describe los pasos básicos para los que una ventana puede crear y utilizar sus propios de **Mostrar los elementos** y de **Categorías** a la vista de texto admiten.  
  
 Este enfoque requiere un VSPackage implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> e interfaces relacionadas.  
  
 [Cómo: obtener acceso a las fuentes integradas y la combinación de colores](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Describe cómo definir y registrar una categoría con fuentes integradas y colores, e inicia el uso de sistema fuentes y colores.  
  
## Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Proporciona una instancia de `IVsFontAndColorDefaults` o interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> que corresponde a un caso anunciado determinado en **Mostrar valores para** enumerado en la página de **Fuentes y colores** del cuadro de diálogo de **Opciones** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permite a un Paquete para admitir la página del IDE **Fuentes y colores** definiendo las fuentes predeterminadas y los colores para una ventana o un componente de la interfaz de usuario.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Proporciona un mecanismo por el que un Paquete que proporciona fuente y compatibilidad de color puede especificar un grupo de elementos de presentación \(una estupendo\-categoría que representa la unión de dos o más categorías.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permite a un Paquete para recuperar la fuente y los datos de color, o guardarlo en el registro.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica VSPackages que usa la fuente y la información de color sobre cambios en fuente y definiciones de colores.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Proporciona herramientas para trabajar con la entrada y los datos de salida que usan métodos del mecanismo de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**fuente y Color** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controla el almacenamiento en caché de la fuente y definiciones de colores.  
  
## Secciones relacionadas  
 [Desarrollar un servicio de lenguaje](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explica cómo VSPackages puede utilizar servicios para personalizar el editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 [Colores en los editores personalizados de sintaxis](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries cómo el editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza servicios para implementar el colorear la sintaxis.  
  
 [Extensión de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo utilizar los servicios de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear elementos de la interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].