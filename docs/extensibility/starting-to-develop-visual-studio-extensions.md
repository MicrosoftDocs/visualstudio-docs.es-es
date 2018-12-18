---
title: Comenzar a desarrollar extensiones de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5d6e84bc526cf597fbfd22bd36b93cd419ba0d6
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349668"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Comenzar a desarrollar extensiones de Visual Studio

Si nunca ha escrito una extensión de Visual Studio antes, probablemente tiene algunas preguntas. Presentamos algunas de las más comunes de aquí. Si no ve la información que busca, use los botones de comentarios (**resultó útil esta página?** en la parte inferior de la pantalla) para pedir lo que se desea.

> [!NOTE]
> En este artículo se aplica a Visual Studio en Windows. Para Visual Studio para Mac, consulte [extender Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>¿Qué software necesito para desarrollar extensiones de Visual Studio?

Deberá instalar el SDK de Visual Studio además de Visual Studio para desarrollar extensiones de Visual Studio. Puede instalar el SDK de Visual Studio como parte del programa de instalación normal, o puede instalarlo más adelante. Para obtener más información acerca de cómo instalar el SDK de Visual Studio, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>¿Qué tipos de cosas puedo hacer con extensiones de Visual Studio?

El cielo su caso el límite cuando se trata de imaginar diferentes extensiones de Visual Studio. Por supuesto, la mayoría de las extensiones tener algo que ver con la escritura de código, pero que no tiene que ser el caso. Estos son algunos ejemplos de los tipos de extensiones que puede crear:

- Compatibilidad con idiomas que no están incluidos en Visual Studio, con el color de la sintaxis, IntelliSense y compatibilidad de compilador y depuración

- Herramientas de productividad que amplían el núcleo IDE experiencia con plantillas adicionales, los cuadros de diálogo nuevo, refactorización de código o ventanas de herramientas

- Diseñadores de dominios para escenarios como la compatibilidad con datos de diseño o en la nube

Para obtener ejemplos de extensiones, consulte el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Muchas extensiones son de código abierto y el catálogo de soluciones incluye vínculos a su repositorio de GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>¿Qué características de Visual Studio se debe ampliar?

En teoría, puede ampliar cualquier parte de Visual Studio: menús, barras de herramientas, comandos, windows, soluciones, proyectos, editores y así sucesivamente.

En la práctica, hemos descubierto que las características en la mayoría de las personas que desea extender son comandos, menús y barras de herramientas, windows, IntelliSense y proyectos. Estos son vínculos a las secciones correspondientes:

-   [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md): agregar sus propios elementos de menús de Visual Studio y las barras de herramientas. Puede usarlos para iniciar la nueva funcionalidad de Visual Studio o sus propias aplicaciones auxiliares externo. También puede proporcionar accesos directos personalizados para los elementos de menú.

-   [Ampliación y personalización de Windows de herramienta](../extensibility/extending-and-customizing-tool-windows.md): Extender ventanas de herramientas existentes o crear sus propias ventanas de herramientas. Por ejemplo, podría agregar nuevas propiedades a la **propiedades**, o puede crear una nueva ventana de herramientas para agregar características adicionales.

-   [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md): agregar sus propias personalizaciones de IntelliSense que se proporciona para los lenguajes de Visual Studio, o crear compatibilidad para nuevos lenguajes de programación. Puede crear nuevas finalización de instrucciones, sugerencias y nueva información rápida. Con las bombillas, puede agregar sugerencias de refactorización y las correcciones de código para admitir nuevos lenguajes de programación.

-   [Ampliación de proyectos](../extensibility/extending-projects.md)

-   [Ampliación de configuración y opciones de usuario](../extensibility/extending-user-settings-and-options.md)

-   [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)

-   [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

-   [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)

##  <a name="BKMK_ProjectTemplate"></a> ¿Qué plantillas de proyecto se proporcionan por VSSDK?
 Los dos tipos principales de las extensiones son extensiones MEF y VSPackages. En general, las extensiones de VSPackage se usan para las extensiones que utilizan o amplían los comandos, ventanas de herramientas y proyectos. Se usan las extensiones MEF para ampliar o personalizar el editor de Visual Studio.

 Para las extensiones de Visual C# y Visual Basic, VSSDK proporciona una plantilla de proyecto VSIX vacía que puede usar junto con las nuevas plantillas de elemento que creación los comandos de menú, ventanas de herramientas y extensiones de editor. También puede usar esta plantilla para plantillas de proyecto de paquete, fragmentos de código y otros artefactos para su distribución a otros usuarios.

 En C++, el Asistente de VSPackage proporciona el código para agregar los comandos de menú, ventanas de herramientas y editores personalizados.

 La plantilla de Shell aislado se usa para empaquetar una extensión en una versión de Visual Studio shell que se puede personalizar y distribuir como su propio. Los temas siguientes muestran cómo empezar a trabajar con cada tipo de extensión:

-   Comandos de menú: [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

-   Ventanas de herramientas: [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)

-   Extensiones de editor: [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   VSPackages básicos: [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

-   Plantilla de proyecto VSIX: [Introducción a la plantilla de proyecto de VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>¿Cómo se puede obtener una extensión my al aspecto Visual Studio?
 Obtenga sugerencias excelente para diseñar la interfaz de usuario para la extensión en [directrices de experiencia de usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>¿Dónde puedo encontrar ejemplos de código VSSDK?
 Cada uno de los vínculos enumerados en la sección anterior tiene tutoriales paso a paso que muestran cómo implementar características específicas. También puede encontrar código abierto muestras de VSSDK en GitHub en [ejemplos de Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>¿Cómo puedo distribuir mi extensión?
 Puede instalar la extensión en otro equipo o envíe a sus amigos como un archivo .vsix, que instala haciendo doble clic en él. Puede encontrar más información acerca de los paquetes VSIX en [envío extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 También puede publicar su extensión en Visual Studio Marketplace, lo que es visible a un gran número de clientes de Visual Studio. Para obtener un ejemplo de empaquetado de una extensión en Marketplace, consulte [Tutorial: publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obtener más información sobre lo que necesita hacer para publicar en Marketplace, consulte [productos y extensiones para Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Vea también

- [Extender Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac)