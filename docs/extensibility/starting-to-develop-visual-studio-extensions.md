---
title: Empezando a desarrollar extensiones de Visual Studio | Documentos de Microsoft
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
ms.openlocfilehash: 44403b5d60fc13666ffc6ec00558b80ef3a50ea9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144468"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Empezando a desarrollar extensiones de Visual Studio
Si nunca ha escrito una extensión de Visual Studio antes, probablemente tenga algunas preguntas. Presentamos algunos de los más comunes que aquí. Si no ve la información que está buscando, utilice los botones de comentarios (**¿le resultó útil esta página?** en la parte inferior de la pantalla) para pedir lo que desea.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>¿Qué software es necesario desarrollar extensiones de Visual Studio?  
 Debe instalar el SDK de Visual Studio además de Visual Studio para desarrollar extensiones de Visual Studio. Puede instalar el SDK de Visual Studio como parte del programa de instalación normal, o puede instalar más adelante. Para obtener más información acerca de cómo instalar el SDK de Visual Studio, vea [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>¿Qué tipo de cosas puedo hacer con las extensiones de Visual Studio?  
 El cielo a su caso el límite cuando se trata de uno se imagina diferentes extensiones de Visual Studio. Por supuesto, la mayoría de las extensiones tienen algo relacionado con la escritura de código, pero que no tiene que ser el caso. Estos son algunos ejemplos de los tipos de extensiones que se puede compilar:  
  
-   Compatibilidad con idiomas que no se incluyen en Visual Studio, con colores de sintaxis, IntelliSense y compatibilidad de compilador y de depuración  
  
-   Herramientas de productividad que amplían el núcleo del IDE experiencia con plantillas adicionales, los cuadros de diálogo de refactorización, nueva del código o las ventanas de herramientas  
  
-   Diseñadores de específico de dominio para escenarios como la compatibilidad con datos de diseño o en la nube  
  
 Para obtener ejemplos de extensiones, eche un vistazo el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Muchas de las extensiones están abiertas con origen y el Marketplace incluye vínculos a su repositorio de GitHub. 
  
## <a name="which-visual-studio-features-can-i-extend"></a>¿Qué características de Visual Studio se debe extender?  
 En teoría, puede ampliar casi cualquier elemento de Visual Studio: menús, barras de herramientas, comandos, windows, soluciones, proyectos, editores y así sucesivamente.  
  
 En la práctica, encontramos que las características en la a que mayoría de los usuarios desea extender son comandos, menús y barras de herramientas, ventanas, IntelliSense y proyectos. Estos son vínculos a las secciones correspondientes:  
  
-   [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md): agregar sus propios elementos de menús de Visual Studio y las barras de herramientas. Puede utilizarlos para iniciar la nueva funcionalidad de Visual Studio o sus propias aplicaciones auxiliares externos. También puede proporcionar accesos directos personalizados para sus elementos de menú.  
  
-   [Ampliar y personalizar las ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md): extender las ventanas de herramientas existente o crear sus propias ventanas de herramientas. Por ejemplo, puede agregar nuevas propiedades a la **propiedades**, o puede crear una nueva ventana de herramientas para agregar características adicionales.  
  
-   [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md): agregar sus propias personalizaciones proporcionada para los lenguajes de Visual Studio IntelliSense o crear compatibilidad con lenguajes de programación de nuevo. Puede crear nueva finalización de instrucciones y sugerencias, información sobre herramientas de QuickInfo nueva. Con las bombillas, puede agregar sugerencias de refactorización y las correcciones de código para admitir nuevos lenguajes de programación.  
  
-   [Ampliación de proyectos](../extensibility/extending-projects.md)  
  
-   [Ampliación de configuración y opciones de usuario](../extensibility/extending-user-settings-and-options.md)  
  
-   [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> ¿Qué plantillas de proyecto se proporcionan con el VSSDK?  
 Los dos tipos principales de extensiones son extensiones MEF y VSPackages. En general, las extensiones del VSPackage se usan para las extensiones que usar o amplían los comandos, ventanas de herramientas y proyectos. Se utilizan las extensiones MEF para ampliar o personalizar el editor de Visual Studio.  
  
 Las extensiones de Visual C# y Visual Basic, el VSSDK proporciona una plantilla de proyecto VSIX vacía que puede usar junto con las nuevas plantillas de elemento que crean comandos de menú, ventanas de herramientas y extensiones de editor. También puede usar esta plantilla para plantillas de proyecto de paquete, fragmentos de código y otros artefactos para distribuirlo a otros usuarios.  
  
 En C++, el Asistente de VSPackage proporciona el código para agregar comandos de menú, ventanas de herramientas y editores personalizados.  
  
 La plantilla de Shell aislado se usa para empaquetar una extensión en una versión del shell de Visual Studio que se puede personalizar y distribuir como su propio. Los temas siguientes muestra cómo empezar a trabajar con cada tipo de extensión:  
  
-   Comandos de menú: [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Ventanas de herramientas: [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Extensiones de editor: [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   VSPackages básicas: [crear una extensión con un paquete VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Plantilla de proyecto VSIX: [Introducción a la plantilla de proyecto de VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Aislamiento de Visual Studio shell: [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>¿Cómo se puede obtener una extensión que se parezca a Visual Studio?  
 Obtener sugerencias interesantes para diseñar la interfaz de usuario para la extensión en [instrucciones para la experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>¿Dónde puedo encontrar ejemplos de código VSSDK?  
 Cada uno de los vínculos enumerados en la sección anterior tener tutoriales paso a paso que muestran cómo implementar características específicas. También puede encontrar código abierto muestras de VSSDK en GitHub en [ejemplos de Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  
  
## <a name="how-can-i-distribute-my-extension"></a>¿Cómo puedo distribuir una extensión?  
 Puede instalar la extensión en otro equipo o enviarla a sus amigos como un archivo .vsix, que se instala haciendo doble clic en él. Puede encontrar más información acerca de los paquetes VSIX en [trasvase extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 También puede publicar la extensión en Visual Studio Marketplace, que lo hace visible a un gran número de clientes de Visual Studio. Para obtener un ejemplo de cómo empaquetar una extensión Marketplace, vea [Tutorial: publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obtener más información sobre lo que necesita hacer para publicar en Marketplace, vea [productos y extensiones para Visual Studio](/vsts/integrate/ide/extensions/overview).
