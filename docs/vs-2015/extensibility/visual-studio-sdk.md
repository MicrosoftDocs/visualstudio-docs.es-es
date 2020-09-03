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
ms.openlocfilehash: 27dce16d9fe02063eae935af96c26184285e583d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850376"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o a integrar las nuevas características en Visual Studio. Puede distribuir sus extensiones a otros usuarios, así como a la galería de Visual Studio. Estas son algunas de las formas en que se puede ampliar Visual Studio:  
  
- Agregar comandos, botones, menús y otros elementos de la interfaz de usuario al IDE  
  
- Agregar ventanas de herramientas para nuevas funcionalidades  
  
- Extender IntelliSense para un lenguaje determinado o proporcionar IntelliSense para nuevos lenguajes de programación  
  
- Use bombillas para proporcionar sugerencias y sugerencias que ayuden a los desarrolladores a escribir código mejor  
  
- Habilitar la compatibilidad con un nuevo lenguaje  
  
- Agregar un tipo de proyecto personalizado  
  
- Llegue a millones de desarrolladores a través de la Visual Studio Marketplace  
  
  Si nunca ha escrito una extensión de Visual Studio, debe encontrar más información sobre estas características y en [empezar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalación de Visual Studio SDK  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Novedades de Visual Studio 2015 SDK  
 El SDK de Visual Studio tiene algunas características nuevas, incluidas las bombillas y los nuevos elementos de proyecto, que le permiten crear comandos de menú, ventanas de herramientas y extensiones de editor mediante un paquete VSIX. Para obtener más información, vea [What's New in the Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario de Visual Studio  
 Obtenga excelentes sugerencias para diseñar la interfaz de usuario de su extensión en directrices de la [experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 También puede obtener información sobre cómo hacer que la extensión tenga un aspecto excelente en dispositivos de alta PPP con nuestro tema de [problemas de PPP](../extensibility/addressing-dpi-issues2.md) .  
  
 Aproveche las ventajas del [servicio de imágenes y el catálogo](../extensibility/image-service-and-catalog.md) para una excelente administración de imágenes y soporte técnico para un gran número de PPP y de los mismos.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Búsqueda e instalación de extensiones de Visual Studio existentes  
 Puede encontrar extensiones de Visual Studio en el cuadro de diálogo **extensiones y actualizaciones** en el menú **herramientas** . Para obtener más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). También puede buscar extensiones en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referencia de Visual Studio SDK  
 Puede encontrar la referencia de la API del SDK de Visual Studio en [referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ejemplos del SDK de Visual Studio  
 Puede encontrar ejemplos de código abierto de extensiones del SDK de VS en GitHub en [ejemplos de Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Este repositorio de GitHub contiene ejemplos que muestran diversas características extensibles de Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Otros recursos del SDK de Visual Studio  
 Si tiene alguna pregunta sobre el VSSDK o desea compartir sus experiencias para desarrollar las extensiones, puede usar el [Foro de extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o el [chat de grupo ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Puede encontrar más información en el [blog de VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) y varios blogs escritos por MVP de Microsoft:  
  
- [Extensiones de Visual Studio favoritas](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Extender Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Consulte también  
 [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Cómo: migrar proyectos de extensibilidad a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Preguntas más frecuentes: convertir complementos en extensiones de VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Administrar varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Agregar comandos a las barras de herramientas](../extensibility/adding-commands-to-toolbars.md)   
 [Extender y personalizar ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)   
 [Extensiones del editor y del servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)   
 [Ampliar proyectos](../extensibility/extending-projects.md)   
 [Extender la configuración de usuario y las opciones](../extensibility/extending-user-settings-and-options.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../extensibility/creating-custom-project-and-item-templates.md)   
 [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)   
 [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Uso y suministro de servicios](../extensibility/using-and-providing-services.md)   
 [Extender Servicios conectados](../extensibility/extending-connected-services.md)   
 [Administrar VSPackages](../extensibility/managing-vspackages.md)   
 [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dentro del SDK de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Compatibilidad con el SDK de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivó](../extensibility/archive.md)   
 [Referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
