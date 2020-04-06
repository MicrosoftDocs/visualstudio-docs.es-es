---
title: SDK de Visual Studio (Visual Studio SDK) Microsoft Docs
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
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698076"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
El SDK de Visual Studio le ayuda a ampliar las características de Visual Studio o integrar nuevas características en Visual Studio. Puede distribuir las extensiones a otros usuarios, así como a Visual Studio Marketplace. Estas son algunas de las formas en que se puede ampliar Visual Studio:

- Agregar comandos, botones, menús y otros elementos de la interfaz de usuario al IDE

- Añadir ventanas de herramientas para nuevas funciones

- Amplíe IntelliSense para un lenguaje determinado o proporcione IntelliSense para nuevos lenguajes de programación

- Utilice bombillas para proporcionar sugerencias y sugerencias que ayuden a los desarrolladores a escribir mejor código

- Habilitar soporte para un nuevo idioma

- Agregar un tipo de proyecto personalizado

- Llega a millones de desarrolladores a través de Visual Studio Marketplace

  Si nunca ha escrito una extensión de Visual Studio antes, debería encontrar más información acerca de estas características y en [Empezar a desarrollar extensiones](../extensibility/starting-to-develop-visual-studio-extensions.md)de Visual Studio .

## <a name="install-the-visual-studio-sdk"></a>Instalar Visual Studio SDK
 El SDK de Visual Studio es una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novedades del SDK de Visual Studio 2017
 El SDK de Visual Studio tiene algunas características nuevas, como el formato VSIX v3, así como cambios importantes, que pueden requerir que actualice la extensión. Para obtener más información, vea Novedades del SDK de [Visual Studio 2017.](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)

## <a name="visual-studio-user-experience-guidelines"></a>Directrices de experiencia de usuario de Visual Studio
 Obtenga excelentes consejos para diseñar la interfaz de usuario para la extensión en las directrices de la experiencia del usuario de [Visual Studio.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

 También puede aprender a hacer que la extensión se vea muy bien en dispositivos de ppp altos con el artículo Problemas de [PPP](../extensibility/addressing-dpi-issues2.md) de dirección.

 Aproveche el [servicio y catálogo](../extensibility/image-service-and-catalog.md) de imágenes para una excelente gestión de imágenes y soporte para alta DPI y temas.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Buscar e instalar extensiones de Visual Studio existentes
 Puede encontrar extensiones de Visual Studio en el cuadro de diálogo **Extensiones y actualizaciones** del menú **Herramientas.** Para obtener más información, vea [Buscar y usar extensiones](../ide/finding-and-using-visual-studio-extensions.md)de Visual Studio . También puede encontrar extensiones en [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Referencia del SDK de Visual Studio
 Puede encontrar la referencia de la API del SDK de Visual Studio en Referencia del SDK de [Visual Studio.](../extensibility/visual-studio-sdk-reference.md)

## <a name="visual-studio-sdk-samples"></a>Ejemplos del SDK de Visual Studio
 Puede encontrar ejemplos de código abierto de extensiones de SDK de VS en GitHub en [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Este repositorio de GitHub contiene ejemplos que ilustran varias características extensibles en Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Otros recursos del SDK de Visual Studio
 Si tiene preguntas sobre VSSDK o desea compartir sus experiencias desarrollando extensiones, puede usar el Foro de [extensibilidad](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) de Visual Studio o [extendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).

 Puede encontrar más información en el [blog vsx Arcana](https://blogs.msdn.microsoft.com/vsx/) y una serie de blogs escritos por Microsoft MVPs:

- [Extensiones favoritas de Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Extensibilidad de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Ampliación de Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Vea también

- [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Cómo: Migrar proyectos de extensibilidad a Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Preguntas frecuentes: Conversión de complementos a extensiones de VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Administrar varios subprocesos en código administrado](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Añadir comandos a las barras de herramientas](../extensibility/adding-commands-to-toolbars.md)
- [Ampliar y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md)
- [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md)
- [Ampliar proyectos](../extensibility/extending-projects.md)
- [Ampliar la configuración y las opciones del usuario](../extensibility/extending-user-settings-and-options.md)
- [Crear plantillas de proyectos y elementos personalizadas](../extensibility/creating-custom-project-and-item-templates.md)
- [Extender las propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)
- [Ampliar otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Uso y prestación de servicios](../extensibility/using-and-providing-services.md)
- [Administración de VSPackages](../extensibility/managing-vspackages.md)
- [Shell aislado de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Enviar extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Dentro de Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Soporte técnico para Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md)
