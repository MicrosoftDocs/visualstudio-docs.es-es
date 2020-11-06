---
title: SDK de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2dbe2832d52d17047795d1898f0e0bfd8a275bb9
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414391"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o a integrar las nuevas características en Visual Studio. Puede distribuir sus extensiones a otros usuarios, así como al Visual Studio Marketplace. Estas son algunas de las formas en que se puede ampliar Visual Studio:

- Agregar comandos, botones, menús y otros elementos de la interfaz de usuario al IDE

- Agregar ventanas de herramientas para nuevas funcionalidades

- Extender IntelliSense para un lenguaje determinado o proporcionar IntelliSense para nuevos lenguajes de programación

- Use bombillas para proporcionar sugerencias y sugerencias que ayuden a los desarrolladores a escribir código mejor

- Habilitar la compatibilidad con un nuevo lenguaje

- Agregar un tipo de proyecto personalizado

- Llegue a millones de desarrolladores a través de la Visual Studio Marketplace

  Si nunca ha escrito una extensión de Visual Studio, debe encontrar más información sobre estas características y en [empezar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK
 El SDK de Visual Studio es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Novedades del SDK de Visual Studio
 El SDK de Visual Studio tiene algunas características nuevas, como la advertencia de extensiones autocargadas de forma sincrónica y el formato VSIX V3, así como cambios importantes, que pueden requerir la actualización de la extensión. Para obtener más información, vea [what's New in the visual studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md) y [what's New in the Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Instrucciones para la experiencia del usuario de Visual Studio
 Obtenga excelentes sugerencias para diseñar la interfaz de usuario de su extensión en directrices de la [experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 También puede obtener información sobre cómo hacer que la extensión tenga un aspecto excelente en dispositivos de alta PPP con el artículo sobre [problemas de PPP de direcciones](../extensibility/addressing-dpi-issues2.md) .

 Aproveche las ventajas del [servicio de imágenes y el catálogo](../extensibility/image-service-and-catalog.md) para una excelente administración de imágenes y soporte técnico para un gran número de PPP y de los mismos.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Buscar e instalar extensiones existentes de Visual Studio
 Puede encontrar extensiones de Visual Studio en el cuadro de diálogo **extensiones y actualizaciones** en el menú **herramientas** . Para obtener más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). También puede buscar extensiones en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Referencia del SDK de Visual Studio
 Puede encontrar la referencia de la API del SDK de Visual Studio en [referencia de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Ejemplos del SDK de Visual Studio
 Puede encontrar ejemplos de código abierto de extensiones del SDK de VS en GitHub en [ejemplos de Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Este repositorio de GitHub contiene ejemplos que muestran diversas características extensibles de Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Otros recursos del SDK de Visual Studio
 Si tiene alguna pregunta sobre el VSSDK o desea compartir sus experiencias para desarrollar las extensiones, puede usar el [Foro de extensibilidad de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o el [chatroom ExtendVS Gitter](https://gitter.im/Microsoft/extendvs).

 Puede encontrar más información en el [blog de VSX Arcana](/archive/blogs/vsx/) y varios blogs escritos por MVP de Microsoft:

- [Extensiones de Visual Studio favoritas](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Extender Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Consulte también

- [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Cómo: migrar proyectos de extensibilidad a Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Preguntas más frecuentes: convertir complementos en extensiones de VSPackage](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Administrar varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Agregar comandos a las barras de herramientas](../extensibility/adding-commands-to-toolbars.md)
- [Extender y personalizar ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)
- [Extensiones del editor y del servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)
- [Ampliar proyectos](../extensibility/extending-projects.md)
- [Extender la configuración de usuario y las opciones](../extensibility/extending-user-settings-and-options.md)
- [Creación de plantillas de proyecto y de elemento personalizadas](../extensibility/creating-custom-project-and-item-templates.md)
- [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)
- [Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)
- [Administración de VSPackages](../extensibility/managing-vspackages.md)
- [Shell aislado de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Dentro de Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Soporte técnico para Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md)