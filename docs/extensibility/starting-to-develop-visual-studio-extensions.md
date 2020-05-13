---
title: Comenzando a desarrollar extensiones de Visual Studio ? Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699739"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Comienzo del desarrollo de extensiones de Visual Studio

Si nunca ha escrito una extensión de Visual Studio antes, probablemente tenga algunas preguntas. Hemos enumerado algunos de los más comunes aquí. Si no ves la información que estás buscando, usa los botones de comentarios **(¿Fue útil esta página?** en la parte inferior de la pantalla) para preguntar lo que quieres.

> [!NOTE]
> Este artículo se aplica a Visual Studio en Windows. Para Visual Studio para Mac, vea [Extender Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac). Para Visual Studio Code, vea Api de extensión de código de [Visual Studio](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>¿Qué software necesito para desarrollar extensiones de Visual Studio?

Debe instalar el SDK de Visual Studio además de Visual Studio para desarrollar extensiones de Visual Studio. Puede instalar el SDK de Visual Studio como parte de la instalación normal o puede instalarlo más adelante. Para obtener más información acerca de la instalación del SDK de Visual Studio, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>¿Qué tipos de cosas puedo hacer con las extensiones de Visual Studio?

El cielo es el límite cuando se trata de imaginar diferentes extensiones de Visual Studio. Por supuesto, la mayoría de las extensiones tienen algo que ver con escribir código, pero ese no tiene que ser el caso. Estos son algunos ejemplos de los tipos de extensiones que puede crear:

- Compatibilidad con lenguajes que no se incluyen en Visual Studio, con coloración de sintaxis, IntelliSense y compatibilidad con compiladores y depuración

- Herramientas de productividad que amplían la experiencia principal del IDE con plantillas adicionales, refactorización de código, nuevos cuadros de diálogo o ventanas de herramientas

- Diseñadores específicos de dominio para escenarios como el diseño de datos o la compatibilidad con la nube

Para ver ejemplos de extensiones, consulte [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Muchas extensiones son de código abierto y Marketplace incluye vínculos a su repositorio de GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>¿Qué características de Visual Studio puedo ampliar?

En teoría, puede ampliar casi cualquier parte de Visual Studio: menús, barras de herramientas, comandos, ventanas, soluciones, proyectos, editores, etc.

En la práctica, hemos encontrado que las características que la mayoría de la gente quiere ampliar son comandos, menús y barras de herramientas, ventanas, IntelliSense y proyectos. Aquí hay enlaces a las secciones relevantes:

- [Ampliación de menús y comandos:](../extensibility/extending-menus-and-commands.md)agregue sus propios elementos a los menús y barras de herramientas de Visual Studio. Puede usarlos para iniciar la nueva funcionalidad de Visual Studio o sus propias aplicaciones auxiliares externas. También puede proporcionar accesos directos personalizados para los elementos de menú.

- [Ampliación y personalización](../extensibility/extending-and-customizing-tool-windows.md)de ventanas de herramientas: amplíe las ventanas de herramientas existentes o cree sus propias ventanas de herramientas. Por ejemplo, podría agregar nuevas propiedades a **Propiedades**o crear una nueva ventana de herramientas para agregar características adicionales.

- [Editor y extensiones](../extensibility/editor-and-language-service-extensions.md)de servicio de lenguaje: agregue sus propias personalizaciones a IntelliSense proporcionado para los lenguajes de Visual Studio o cree compatibilidad con nuevos lenguajes de programación. Puede crear nuevas terminaciones de instrucciones, sugerencias y nuevas descripciones emergentes de QuickInfo. Con las bombillas, puede agregar sugerencias de refactorización y correcciones de código para admitir nuevos lenguajes de programación.

- [Ampliación de proyectos](../extensibility/extending-projects.md)

- [Ampliación de configuración y opciones de usuario](../extensibility/extending-user-settings-and-options.md)

- [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)

- [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Shell aislado de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>¿Qué plantillas de proyecto proporciona VSSDK?
 Los dos tipos principales de extensiones son VSPackages y extensiones MEF. En general, las extensiones de VSPackage se usan para las extensiones que usan o extienden comandos, ventanas de herramientas y proyectos. Las extensiones MEF se usan para ampliar o personalizar el editor de Visual Studio.

 Para las extensiones de Visual C y Visual Basic, el VSSDK proporciona una plantilla de proyecto VSIX vacía que puede usar junto con las nuevas plantillas de elemento que crean comandos de menú, ventanas de herramientas y extensiones de editor. También puede usar esta plantilla para empaquetar plantillas de proyecto, fragmentos de código y otros artefactos para su distribución a otros usuarios.

 Para C++, el asistente de VSPackage proporciona el código para agregar comandos de menú, ventanas de herramientas y editores personalizados.

 La plantilla Shell aislado se usa para empaquetar una extensión en una versión del shell de Visual Studio que puede marcar y distribuir como propia. Los siguientes temas le muestran cómo empezar a utilizar cada tipo de extensión:

- Comandos de menú: [Creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

- Ventanas de herramientas: [Creación de una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)

- Extensiones del editor: [Creación de una extensión con una plantilla](../extensibility/creating-an-extension-with-an-editor-item-template.md) de elemento de editor

- VSPackages básicos: [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Plantilla de proyecto VSIX: [Introducción a la plantilla](../extensibility/getting-started-with-the-vsix-project-template.md) de proyecto VSIX

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>¿Cómo obtengo mi extensión para que se parezca a Visual Studio?
 Obtenga excelentes consejos para diseñar la interfaz de usuario para la extensión en [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>¿Dónde puedo encontrar ejemplos de código VSSDK?
 Cada uno de los vínculos enumerados en la sección anterior tiene tutoriales paso a paso que muestran cómo implementar características específicas. También puede encontrar ejemplos de VSSDK de código abierto en GitHub en [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>¿Cómo puedo distribuir mi extensión?
 Puede instalar su extensión en otro equipo o enviarlo a sus amigos como un archivo .vsix, que se instala haciendo doble clic en él. Puede obtener más información sobre los paquetes VSIX en [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 También puede publicar la extensión en Visual Studio Marketplace, lo que la hace visible para un gran número de clientes de Visual Studio. Para obtener un ejemplo de empaquetado de una extensión en Marketplace, vea [Tutorial: publicación](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)de una extensión de Visual Studio . Para obtener más información acerca de lo que debe hacer para publicar en Marketplace, vea [Productos y extensiones para Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Vea también

- [Extender Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Ampliación del código de Visual Studio](https://code.visualstudio.com/api)
