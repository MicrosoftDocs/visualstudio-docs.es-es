---
title: Empezando a desarrollar extensiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d62a4c6cc45681fe6a66ae57df2e1da1d1cc12e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850590"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Comienzo del desarrollo de extensiones de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si nunca ha escrito una extensión de Visual Studio, es probable que tenga algunas preguntas. Aquí se enumeran algunos de los más comunes. Si no ve la información que busca, use los botones de comentarios (¿le resultó**útil esta página?** en la parte inferior de la pantalla) para solicitar lo que desea.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>¿Qué software necesito para desarrollar extensiones de Visual Studio?
 Debe instalar el SDK de Visual Studio 2015 además de Visual Studio 2015 para poder desarrollar extensiones de Visual Studio.   Puede instalar el SDK de Visual Studio 2015 como parte de la configuración normal, o puede instalarlo más adelante. Para obtener más información sobre cómo instalar el SDK de Visual Studio, vea [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>¿Qué tipos de cosas puedo hacer con las extensiones de Visual Studio?
 El cielo es el límite cuando se trata de imaginar diferentes extensiones de Visual Studio. Por supuesto, la mayoría de las extensiones tienen algo que hacer con la escritura de código, pero no es necesario que sea así. Estos son algunos ejemplos de los tipos de extensiones que puede compilar:

- Compatibilidad con idiomas que no están incluidos en Visual Studio, con colores de sintaxis, IntelliSense y compatibilidad con compilador y depuración

- Herramientas de productividad que amplían la experiencia del IDE principal con plantillas adicionales, refactorización de código, nuevos cuadros de diálogo o ventanas de herramientas

- Diseñadores específicos de dominio para escenarios como diseño de datos o soporte técnico en la nube

  Para obtener ejemplos de extensiones, consulte el [Visual Studio Marketplace](https://marketplace.visualstudio.com/). También puede echar un vistazo a [extensiones de código abierto de Visual Studio](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).

## <a name="which-visual-studio-features-can-i-extend"></a>¿Qué características de Visual Studio puedo ampliar?
 En teoría, puede extender prácticamente cualquier parte de Visual Studio: menús, barras de herramientas, comandos, ventanas, soluciones, proyectos, editores, etc.

 En la práctica, hemos descubierto que las características que la mayoría de las personas quieren extender son comandos, menús y barras de herramientas, ventanas, IntelliSense y proyectos. Estos son los vínculos a las secciones correspondientes:

- [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md): agregue sus propios elementos a los menús y las barras de herramientas de Visual Studio. Puede usarlos para iniciar nuevas funcionalidades de Visual Studio o sus propias aplicaciones auxiliares externas. También puede proporcionar accesos directos personalizados para los elementos de menú.

- [Extender y personalizar ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md): Extienda las ventanas de herramientas existentes o cree sus propias ventanas de herramientas. Por ejemplo, puede agregar nuevas propiedades a las **propiedades**o puede crear una nueva ventana de herramientas para agregar características adicionales.

- [Extensiones del editor y del servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md): agregue sus propias personalizaciones que IntelliSense proporcione para los lenguajes de Visual Studio o cree compatibilidad para los nuevos lenguajes de programación. Puede crear nuevas finalizaciones de instrucciones, sugerencias y nuevas informaciones sobre herramientas de QuickInfo. Con las bombillas, puede Agregar sugerencias de refactorización y correcciones de código para admitir nuevos lenguajes de programación.

- [Ampliación de proyectos](../extensibility/extending-projects.md)

- [Ampliación de configuración y opciones de usuario](../extensibility/extending-user-settings-and-options.md)

- [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)

- [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> ¿Qué plantillas de proyecto proporciona el VSSDK?
 Los dos tipos principales de extensiones son VSPackages y extensiones de MEF. En general, las extensiones VSPackage se utilizan para las extensiones que usan o extienden comandos, ventanas de herramientas y proyectos. Las extensiones de MEF se usan para extender o personalizar el editor de Visual Studio.

 En el caso de las extensiones de Visual C# y Visual Basic, VSSDK proporciona una plantilla de proyecto de VSIX vacía que se puede usar junto con las nuevas plantillas de elemento que crean comandos de menú, ventanas de herramientas y extensiones de editor. Para obtener más información, vea [What's New in the Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). También puede usar esta plantilla para empaquetar plantillas de proyecto, fragmentos de código y otros artefactos para su distribución a otros usuarios.

 En el caso de C++, el Asistente para VSPackage proporciona el código para agregar comandos de menú, ventanas de herramientas y editores personalizados.

 La plantilla de Shell aislado se usa para empaquetar una extensión en una versión de Visual Studio Shell que se puede personalizar y distribuir como su propia. En los temas siguientes se muestra cómo empezar a trabajar con cada tipo de extensión:

- Comandos de menú: [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

- Ventanas de herramientas: [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)

- Extensiones de editor: [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- VSPackages básico: [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Plantilla de Proyecto VSIX: [Introducción con la plantilla de Proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

- Shell aislado de Visual Studio: [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Cómo obtener mi extensión para que tenga un aspecto similar a Visual Studio
 Obtenga excelentes sugerencias para diseñar la interfaz de usuario de su extensión en directrices de la [experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>¿Dónde puedo encontrar ejemplos de código de VSSDK?
 Cada uno de los vínculos enumerados en la sección anterior contiene tutoriales paso a paso que muestran cómo implementar características específicas. También puede encontrar ejemplos de VSSDK de código abierto en GitHub en [ejemplos de Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>¿Cómo se puede distribuir la extensión?
 Puede instalar la extensión en otro equipo o enviarla a sus amigos como archivo. vsix, que puede instalar haciendo doble clic en ella. Puede encontrar más información sobre los paquetes VSIX en el [envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 También puede publicar su extensión en la galería de Visual Studio, lo que hace que sea visible para un gran número de clientes de Visual Studio. Para obtener un ejemplo de cómo empaquetar una extensión para la galería, vea [Tutorial: publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obtener más información sobre lo que debe hacer para publicar en la galería, consulte [Products and Extensions for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
