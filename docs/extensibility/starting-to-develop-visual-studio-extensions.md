---
title: Empezando a desarrollar extensiones de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: dc5416fe979ed3e52ef2df77e5b495cb98038dcd
ms.lasthandoff: 03/07/2017

---
# <a name="starting-to-develop-visual-studio-extensions"></a>Empezando a desarrollar extensiones de Visual Studio
Si nunca ha escrito una extensión de Visual Studio antes, probablemente tiene algunas preguntas. Presentamos algunos de los más comunes de aquí. Si no ve la información que busca, utilice los botones de comentarios (**resultó útil esta página?** en la parte inferior de la pantalla) para pedir lo que desea.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>¿Qué software es necesario desarrollar extensiones de Visual Studio?  
 Debe instalar el SDK de Visual Studio además de Visual Studio para desarrollar extensiones de Visual Studio. Puede instalar el SDK de Visual Studio como parte de la instalación normal, o puede instalar más adelante. Para obtener más información acerca de cómo instalar el SDK de Visual Studio, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>¿Qué tipo de cosas puedo hacer con las extensiones de Visual Studio?  
 El cielo su caso el límite cuando se trata de pensar en diferentes extensiones de Visual Studio. Por supuesto, la mayoría de las extensiones tienen algo que ver con la escritura de código, pero que no tiene que ser el caso. Estos son algunos ejemplos de los tipos de extensiones que se puede compilar:  
  
-   Compatibilidad con idiomas que no se incluyen en Visual Studio, con colores de sintaxis, IntelliSense y compatibilidad de compilador y depuración  
  
-   Herramientas de productividad que amplían el núcleo del IDE experimentar con plantillas adicionales, los cuadros de diálogo nuevo, refactorización del código o ventanas de herramientas  
  
-   Diseñadores de dominios para escenarios como la compatibilidad con datos de nube o de diseño  
  
 Para obtener ejemplos de extensiones, consulte el [Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). También puede echar un vistazo a [la extensiones de Visual Studio abra origen](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## <a name="which-visual-studio-features-can-i-extend"></a>¿Qué características de Visual Studio puedo extender?  
 En teoría, puede ampliar casi cualquier parte de Visual Studio: menús, barras de herramientas, comandos, windows, soluciones, proyectos, editores y así sucesivamente.  
  
 En la práctica, hemos descubierto que las características en la mayoría de las personas que desea extender son comandos, menús y barras de herramientas, windows, IntelliSense y proyectos. Vínculos a las secciones relevantes son:  
  
-   [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md): agregar sus propios elementos de menús de Visual Studio y barras de herramientas. Puede usarlas para iniciar la nueva funcionalidad de Visual Studio o en sus propias aplicaciones auxiliares externos. También puede proporcionar accesos directos personalizados para los elementos de menú.  
  
-   [Ampliación y personalización de ventanas de herramientas](../extensibility/extending-and-customizing-tool-windows.md): Extender ventanas de herramientas existentes o crear sus propias ventanas de herramientas. Por ejemplo, puede agregar nuevas propiedades a la **propiedades**, o bien puede crear una nueva ventana de herramienta para agregar características adicionales.  
  
-   [Editor y extensiones de servicio de lenguaje](../extensibility/editor-and-language-service-extensions.md): agregar sus propias personalizaciones de IntelliSense que se proporciona para los lenguajes de Visual Studio o crear compatibilidad para nuevos lenguajes de programación. Puede crear nuevos finalización de instrucciones, sugerencias y nuevos sobre herramientas de QuickInfo. Con las bombillas, puede agregar sugerencias de refactorización y las correcciones de código para admitir nuevos lenguajes de programación.  
  
-   [Ampliación de proyectos](../extensibility/extending-projects.md)  
  
-   [Ampliación de configuración y opciones de usuario](../extensibility/extending-user-settings-and-options.md)  
  
-   [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>¿Qué plantillas de proyecto se proporcionan con el VSSDK?  
 Los dos tipos principales de extensiones son extensiones de VSPackages y MEF. En general, las extensiones de VSPackage se usan para las extensiones que usar o amplían los proyectos, las ventanas de herramientas y comandos. Extensiones MEF se utilizan para ampliar o personalizar el editor de Visual Studio.  
  
 Para las extensiones de Visual C# y Visual Basic, el VSSDK proporciona una plantilla de proyecto VSIX vacía que puede usar junto con las nuevas plantillas de elemento que crean extensiones de editor, ventanas de herramientas y comandos de menú. También puede utilizar esta plantilla para plantillas de proyecto de paquete, fragmentos de código y otros artefactos para su distribución a otros usuarios.  
  
 En C++, el Asistente de VSPackage proporciona el código para agregar comandos de menú, ventanas de herramientas y editores personalizados.  
  
 La plantilla de Shell aislado se usa para empaquetar una extensión en una versión del shell de Visual Studio que puede personalizar y distribuir como su propio. Los temas siguientes muestran cómo empezar a trabajar con cada tipo de extensión:  
  
-   Comandos de menú: [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Ventanas de herramientas: [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Extensiones de editor: [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   VSPackages básica: [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Plantilla de proyecto VSIX: [Introducción a la plantilla de proyecto de VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio aislada shell: [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>¿Cómo se puede obtener una extensión my al aspecto Visual Studio?  
 Obtener excelentes consejos para diseñar la interfaz de usuario para la extensión en [instrucciones para la experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>¿Dónde puedo encontrar ejemplos de código VSSDK?  
 Cada uno de los vínculos enumerados en la sección anterior tienen tutoriales paso a paso que muestran cómo implementar características específicas. También puede encontrar código abierto VSSDK ejemplos en GitHub en [ejemplos de Visual Studio](https://aka.ms/vs2015sdksamples).  
  
## <a name="how-can-i-distribute-my-extension"></a>¿Cómo puedo distribuir mi extensión?  
 Puede instalar la extensión en otro equipo o enviarla a sus amigos como un archivo .vsix que instalar haciendo doble clic en él. Puede encontrar más información acerca de los paquetes VSIX en [envío extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 También puede publicar su extensión en la Galería de Visual Studio, lo que es visible a un gran número de clientes de Visual Studio. Para obtener un ejemplo de empaquetado de una extensión de la galería, consulte [Tutorial: publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obtener más información sobre lo que necesita hacer para publicar en la galería, consulte [productos y extensiones para Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
