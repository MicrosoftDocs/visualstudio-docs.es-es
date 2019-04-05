---
title: SDK de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8184ae3085c6366256f37b3e5a034b70fcc3cd7a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002637"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o integrar las nuevas características en Visual Studio. Puede distribuir sus extensiones a otros usuarios, así como a la Galería de Visual Studio. Estas son algunas de las formas en que se puede ampliar Visual Studio:  
  
- Agregar comandos, botones, menús y otros elementos de interfaz de usuario para el IDE  
  
- Agregar ventanas de herramientas para la nueva funcionalidad  
  
- Extender IntelliSense para un idioma determinado, o proporcionar IntelliSense para los nuevos lenguajes de programación  
  
- Usar bombillas para proporcionar consejos y sugerencias que ayudan a los desarrolladores escriben código mejor  
  
- Habilitar la compatibilidad con un nuevo idioma  
  
- Agregar un tipo de proyecto personalizado  
  
- Llegue a millones de desarrolladores a través de Visual Studio Marketplace  
  
  Si nunca ha escrito una extensión de Visual Studio antes, se debe encontrar más información sobre estas características y en [comenzar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Novedades de Visual Studio 2015 SDK  
 El SDK de Visual Studio tiene algunas características nuevas, como bombillas y los nuevos elementos de proyecto que le permiten crear comandos de menú, ventanas de herramientas y extensiones de editor mediante un paquete VSIX. Para obtener más información, consulte [What ' s New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario de Visual Studio  
 Obtenga sugerencias excelente para diseñar la interfaz de usuario para la extensión en [directrices de experiencia de usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 También puede aprender a hacer que una extensión se ven perfectos en dispositivos altos PPP con nuestro [abordar problemas de PPP](../extensibility/addressing-dpi-issues2.md) tema.  
  
 Aproveche la [catálogo y servicio de imágenes](../extensibility/image-service-and-catalog.md) para la administración de imágenes grandes y compatibilidad con valores altos de PPP y temas.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Búsqueda e instalación de extensiones de Visual Studio existente  
 Puede encontrar extensiones de Visual Studio en el **extensiones y actualizaciones** cuadro de diálogo en el **herramientas** menú. Para más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). También puede encontrar extensiones en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referencia de Visual Studio SDK  
 Puede encontrar la referencia de API de SDK de Visual Studio en [referencia de SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ejemplos de SDK de Visual Studio  
 Puede encontrar ejemplos de código abierto de extensiones del SDK de VS en GitHub en [ejemplos de Visual Studio](https://aka.ms/vs2015sdksamples). Este repositorio de GitHub contiene ejemplos que muestran diversas características extensibles en Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Otros recursos SDK de Visual Studio  
 Si tiene alguna pregunta sobre el VSSDK o desea compartir sus experiencias de desarrollo de extensiones, puede usar el [foro de extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o [Chat en grupo ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Puede encontrar más información en el [arcanos VSX blog](http://blogs.msdn.com/b/vsx/) y un número de blogs escritas por MVPs Microsoft:  
  
-   [Extensiones de Visual Studio favorito](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extensión de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vea también  
 [Creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Cómo: Migrar proyectos de extensibilidad a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [PREGUNTAS MÁS FRECUENTES: Conversión de complementos en extensiones de VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Administración de varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Agregar comandos a barras de herramientas](../extensibility/adding-commands-to-toolbars.md)   
 [Ampliación y personalización de la herramienta Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)   
 [Extender proyectos](../extensibility/extending-projects.md)   
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)   
 [Creación de plantillas de elementos y proyectos personalizadas](../extensibility/creating-custom-project-and-item-templates.md)   
 [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)   
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Ampliación de los servicios conectados](../extensibility/extending-connected-services.md)   
 [Administración de VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio Shell (aislado)](../extensibility/visual-studio-isolated-shell.md)   
 [Extensiones de Visual Studio de trasvase de registros](../extensibility/shipping-visual-studio-extensions.md)   
 [Dentro de Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Compatibilidad con el SDK de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archive](../extensibility/archive.md)   
 [Referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
