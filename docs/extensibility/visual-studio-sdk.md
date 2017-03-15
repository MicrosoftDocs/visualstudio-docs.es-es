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
caps.latest.revision: 56
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: efc5a2722757229057a91f5e3a6c2ad3681f5a89
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o integrar nuevas características en Visual Studio. Puede distribuir sus extensiones a otros usuarios, así como a la Galería de Visual Studio. Estas son algunas de las formas en que se puede ampliar Visual Studio:  
  
-   Agregar comandos, botones, menús y otros elementos de interfaz de usuario del IDE  
  
-   Agregar ventanas de herramientas para la nueva funcionalidad  
  
-   Extender IntelliSense para un idioma determinado, o proporcionar IntelliSense para los nuevos lenguajes de programación  
  
-   Usar bombillas para proporcionar consejos y sugerencias que ayudan a los desarrolladores escriben código mejor  
  
-   Habilitar la compatibilidad con un idioma nuevo  
  
-   Agregar un tipo de proyecto personalizadas  
  
-   Llegar a millones de desarrolladores a través de la Galería de Visual Studio  
  
 Si nunca ha escrito una extensión de Visual Studio antes, encontrará más información acerca de estas características y en [empezando a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Novedades en el SDK Visual Studio 2015  
 El SDK de Visual Studio tiene algunas características nuevas, incluidas las bombillas y nuevos elementos de proyecto que le permiten crear extensiones de editor mediante un paquete VSIX, ventanas de herramientas y comandos de menú. Para obtener más información, consulte [Novedades en el SDK de Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario de Visual Studio  
 Obtener excelentes consejos para diseñar la interfaz de usuario para la extensión en [instrucciones para la experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 También aprenderá cómo hacer que la extensión de Maravilla en dispositivos de PPP alta con nuestro [abordar problemas de PPP](../extensibility/addressing-dpi-issues2.md) tema.  
  
 Aprovechar la [catálogo y el servicio de imágenes](../extensibility/image-service-and-catalog.md) para administración de imágenes excelentes y compatibilidad con alta concentración de PPP y temas.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Buscar e instalar las extensiones de Visual Studio existentes  
 Puede encontrar las extensiones de Visual Studio en el **extensiones y actualizaciones** cuadro de diálogo en el **herramientas** menú. Para obtener más información, consulte [búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). También puede buscar extensiones en la [Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referencia del SDK de Visual Studio  
 Puede encontrar la referencia de API del SDK de Visual Studio en [referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ejemplos SDK de Visual Studio  
 Puede encontrar ejemplos de código abierto de extensiones del SDK de VS en GitHub en [ejemplos de Visual Studio](https://aka.ms/vs2015sdksamples). Este repositorio de GitHub contiene ejemplos que muestran diversas características extensibles en Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Otros recursos SDK de Visual Studio  
 Si tiene alguna pregunta sobre el VSSDK o desea compartir su experiencia de desarrollo de extensiones, puede usar el [foro de extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o [Chat en grupo ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Puede encontrar más información en el [blog de VSX arcanos](http://blogs.msdn.com/b/vsx/) y un número de blogs escritos por MVPs Microsoft:  
  
-   [Extensiones de Visual Studio favorito](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extensión de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vea también  
 [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Cómo: migrar proyectos de extensibilidad en Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Preguntas más frecuentes: Convertir complementos en extensiones de VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Administración de varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)   
 [Agregar comandos a las barras de herramientas](../extensibility/adding-commands-to-toolbars.md)   
 [Ampliación y personalización de ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)   
 [Extender proyectos](../extensibility/extending-projects.md)   
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)   
 [Creación de proyecto personalizadas y plantillas de elementos](../extensibility/creating-custom-project-and-item-templates.md)   
 [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)   
 [Extensión de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Administración de VSPackages](../extensibility/managing-vspackages.md)   
 [Shell de aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [En el SDK de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Compatibilidad con el SDK de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivo](../extensibility/archive.md)   
 [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md)
