---
title: SDK de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bf8c558d01538d477aee3670b3c119d72a83878d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o integrar características nuevas en Visual Studio. Puede distribuir sus extensiones a otros usuarios, así como para Visual Studio Marketplace. Estas son algunas de las formas en que se puede ampliar Visual Studio:  
  
-   Agregue comandos, botones, menús y otros elementos de interfaz de usuario para el IDE  
  
-   Agregar ventanas de herramientas para la nueva funcionalidad  
  
-   Extender IntelliSense para un idioma determinado, o proporcionar IntelliSense para los lenguajes de programación nueva  
  
-   Usar bombillas para proporcionar sugerencias y sugerencias que ayudan a los desarrolladores escriben código mejor  
  
-   Habilitar la compatibilidad con un nuevo lenguaje  
  
-   Agregar un tipo de proyecto personalizado  
  
-   Alcanzar millones de desarrolladores a través de Visual Studio Marketplace  
  
 Si nunca ha escrito una extensión de Visual Studio antes, debe buscar más información acerca de estas características y en [comenzar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio  
 El SDK de Visual Studio es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novedades en el SDK de Visual Studio de 2017  
 El SDK de Visual Studio tiene algunas características nuevas como el formato de v3 VSIX así como últimos cambios que necesitan actualizar la extensión. Para obtener más información, consulte [What's New en el SDK de Visual Studio de 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario de Visual Studio  
 Obtener sugerencias interesantes para diseñar la interfaz de usuario para la extensión en [instrucciones para la experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 También puede aprender a hacer que la extensión de un aspecto excelente en dispositivos alta de PPP con nuestro [problemas de PPP de direccionamiento](../extensibility/addressing-dpi-issues2.md) tema.  
  
 Aprovechar las ventajas de la [servicio de imágenes y catálogo](../extensibility/image-service-and-catalog.md) para la administración de imágenes excelente y compatibilidad con valores altos de PPP y temas.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Búsqueda e instalación de extensiones de Visual Studio existentes  
 Puede encontrar las extensiones de Visual Studio en el **extensiones y actualizaciones** cuadro de diálogo en el **herramientas** menú. Para más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). También puede buscar extensiones en la [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referencia SDK de Visual Studio  
 Puede encontrar la referencia de API de SDK de Visual Studio en [referencia de SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ejemplos de SDK de Visual Studio  
 Puede encontrar ejemplos de código abierto de extensiones del SDK de VS en GitHub en [ejemplos de Visual Studio](https://aka.ms/vs2015sdksamples). Este repositorio de GitHub contiene ejemplos que muestran diversas características extensibles en Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Otros recursos SDK de Visual Studio  
 Si tiene alguna pregunta sobre el VSSDK o desea compartir sus experiencias desarrollar extensiones, puede usar el [foro de extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o [salón de chat de ExtendVS Gitter](https://gitter.im/Microsoft/extendvs).  
  
 Puede encontrar más información en el [arcanos VSX blog](http://blogs.msdn.com/b/vsx/) y una serie de blogs escritos MVPs Microsoft:  
  
-   [Extensiones de Visual Studio favoritos](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extender Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vea también  
 [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Cómo: migrar proyectos de extensibilidad en Visual Studio de 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Preguntas más frecuentes: Conversión de complementos a las extensiones del VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Administración de varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Agregar comandos a las barras de herramientas](../extensibility/adding-commands-to-toolbars.md)   
 [Extender y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)   
 [Extender proyectos](../extensibility/extending-projects.md)   
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)   
 [Crear plantillas para proyectos y plantillas de elementos](../extensibility/creating-custom-project-and-item-templates.md)   
 [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)   
 [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso y proporciona servicios](../extensibility/using-and-providing-services.md)   
 [Administrar paquetes VSPackage](../extensibility/managing-vspackages.md)   
 [Aislamiento de Visual Studio Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Extensiones de Visual Studio de envío](../extensibility/shipping-visual-studio-extensions.md)   
 [En el SDK de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Compatibilidad con el SDK de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivo](../extensibility/archive.md)   
 [Referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
