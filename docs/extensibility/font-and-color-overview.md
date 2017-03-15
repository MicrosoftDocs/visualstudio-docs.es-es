---
title: "Introducci&#243;n de Color y fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], fuente y color"
  - "control de fuente y color [Visual Studio SDK] editores"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Introducci&#243;n de Color y fuente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tema explica la fuente de texto y definiciones de colores en el entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  También presenta conceptos de categorías y los elementos de la pantalla, y describe cómo VSPackages y el editor básico utilizan atributos de texto.  
  
## Las fuentes y la página de propiedades de colores  
 Puede administrar atributos de texto mostrado en el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(IDE\) a través de la página de propiedades de **Fuentes y colores** .  Para encontrar la página de propiedades de **Fuentes y colores** , en el menú de **Herramientas** , haga clic en **Opciones**.  Expanda **Entorno** y, a continuación, haga clic en **Fuentes y colores**.  
  
## Categorías y elementos de presentación  
 Organizan las fuentes y los colores de **Categorías** y **Mostrar los elementos**.  
  
-   **Categoría** es un contenedor funcional OR lógica para varios **Mostrar los elementos**.  
  
     una lista de **Categorías** está en la lista desplegable de **Mostrar valores para** de la página de propiedades de **Fuentes y colores** .  
  
-   **elemento de la pantalla** es una entidad bien definido de texto como un comentario, una cadena, o una estructura de control que debe ser coloreada cuando se muestra.  
  
 cada **Muestre el elemento** es únicamente definido dentro de **Categoría** que lo contiene.  Por consiguiente, más de un **Categoría** puede tener **elemento de la pantalla** con el mismo nombre.  
  
## Control de VSPackage de fuentes y colores  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permite VSPackages:  
  
-   Defina la fuente y el color **Categorías**.  
  
-   Especifique las fuentes y los colores utilizados para mostrar **Mostrar los elementos**.  
  
-   Interactuar con la página de propiedades de **Fuentes y colores** .  
  
-   **Categorías** varios global en grupos.  
  
-   Se conservan los cambios en la configuración predeterminada.  
  
 Hay dos maneras de interactuar con la fuente y selecciones de color dentro de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Una manera se denomina *colorear la sintaxis*.  Se utiliza en un Paquete que personalizar el editor existente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para implementar un servicio de lenguaje y crear un editor de código fuente.  
  
     Sólo un **Categoría** admite este mecanismo, a saber, **Editor de texto**.  
  
-   Una alternativa más general admite el resto de **Categorías** y los componentes de la interfaz de usuario distinto del editor de código fuente al mostrar texto.  Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## Valores básicos del texto del editor  
 **Editor de texto Categoría** rigen a la fuente y definiciones de colores para el editor básico de un objeto de servicio de lenguaje encontrado en la lista desplegable de **Mostrar valores para** de la página de propiedades de **Fuentes y colores** .  
  
 Al ejecutar los editores, debe usar el mecanismo especializado de fuente y control de color que el servicio de lenguaje ofrece para controlar y extender los valores de **Editor de texto** .  El mecanismo se denomina *colorear la sintaxis* y proporciona:  
  
-   una técnica simplificada para administrar las fuentes y los colores de los elementos de la pantalla.  
  
     Para obtener más información, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un mecanismo bien definido y optimización del color.  
  
     Para obtener más información, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La capacidad de ambos elementos de presentación integrada de uso de **Editor de textoCategoría** y amplían.  
  
     Para obtener más información, vea [Cómo: usar elementos coloreables integrados](../extensibility/internals/how-to-use-built-in-colorable-items.md) y [Elementos coloreables personalizados](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistencia automática de estado actual integrada y los elementos personalizados de presentación a la categoría de **Editor de texto** .  
  
 Para obtener más información sobre el colorear la sintaxis vea [Colores en un servicio de lenguaje heredado de sintaxis](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## Vea también  
 [Interfaces heredadas en el Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Colores en un servicio de lenguaje heredado de sintaxis](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)