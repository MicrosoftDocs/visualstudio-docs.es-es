---
title: SDK de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c527604639d701c3cda5bddba9ee61c01e5c8dd
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586780"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o integrar las nuevas características en Visual Studio. Puede distribuir sus extensiones a otros usuarios, así como a Visual Studio Marketplace. Estas son algunas de las formas en que se puede ampliar Visual Studio:  
  
-   Agregar comandos, botones, menús y otros elementos de interfaz de usuario para el IDE  
  
-   Agregar ventanas de herramientas para la nueva funcionalidad  
  
-   Extender IntelliSense para un idioma determinado, o proporcionar IntelliSense para los nuevos lenguajes de programación  
  
-   Usar bombillas para proporcionar consejos y sugerencias que ayudan a los desarrolladores escriben código mejor  
  
-   Habilitar la compatibilidad con un nuevo idioma  
  
-   Agregar un tipo de proyecto personalizado  
  
-   Llegue a millones de desarrolladores a través de Visual Studio Marketplace  
  
 Si nunca ha escrito una extensión de Visual Studio antes, se debe encontrar más información sobre estas características y en [empezando a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK  
 El SDK de Visual Studio es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novedades de Visual Studio 2017 SDK  
 El SDK de Visual Studio tiene algunas características nuevas como el formato VSIX v3 así como cambios radicales que pueden requerir que actualice la extensión. Para obtener más información, consulte [Novedades de Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Instrucciones para la experiencia del usuario de visuales Studio  
 Obtenga sugerencias excelente para diseñar la interfaz de usuario para la extensión en [instrucciones para la experiencia de usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 También puede aprender a hacer que una extensión se ven perfectos en dispositivos altos PPP con el [dirección PPP emite](../extensibility/addressing-dpi-issues2.md) artículo.  
  
 Aproveche la [servicio y el catálogo de imágenes](../extensibility/image-service-and-catalog.md) para la administración de imágenes grandes y compatibilidad con valores altos de PPP y temas.  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>Buscar e instalar extensiones de Visual Studio existentes  
 Puede encontrar extensiones de Visual Studio en el **extensiones y actualizaciones** cuadro de diálogo en el **herramientas** menú. Para obtener más información, consulte [buscar y usar Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md). También puede encontrar extensiones en el [marketplace de Visual Studio](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referencia de Visual Studio SDK  
 Puede encontrar la referencia de API de SDK de Visual Studio en [referencia de SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ejemplos de Visual Studio SDK  
 Puede encontrar ejemplos de código abierto de extensiones del SDK de VS en GitHub en [ejemplos de Visual Studio](https://aka.ms/vs2015sdksamples). Este repositorio de GitHub contiene ejemplos que muestran diversas características extensibles en Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Otros recursos del SDK de Visual Studio  
 Si tiene alguna pregunta sobre el VSSDK o desea compartir sus experiencias de desarrollo de extensiones, puede usar el [foro de extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o [ExtendVS de chat de Gitter](https://gitter.im/Microsoft/extendvs).  
  
 Puede encontrar más información en el [arcanos VSX blog](http://blogs.msdn.com/b/vsx/) y una serie de blogs escritas por MVPs Microsoft:  
  
-   [Extensiones favoritas de Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extensión de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vea también  
 [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Cómo: migrar proyectos de extensibilidad de Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Preguntas más frecuentes: Convertir complementos en extensiones de VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Administrar varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Agregar comandos a barras de herramientas](../extensibility/adding-commands-to-toolbars.md)   
 [Ampliar y personalizar ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)   
 [Extensiones de servicio de editor y lenguaje](../extensibility/editor-and-language-service-extensions.md)   
 [Extender proyectos](../extensibility/extending-projects.md)   
 [Extender las opciones y configuración de usuario](../extensibility/extending-user-settings-and-options.md)   
 [Crear plantillas de proyecto y elemento personalizadas](../extensibility/creating-custom-project-and-item-templates.md)   
 [Extender las propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)   
 [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)   
 [Administrar los paquetes VSPackage](../extensibility/managing-vspackages.md)   
 [Shell de Visual Studio aislado](../extensibility/visual-studio-isolated-shell.md)   
 [Distribuir extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dentro de Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Compatibilidad con el SDK de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archive](../extensibility/archive.md)   
 [Referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
