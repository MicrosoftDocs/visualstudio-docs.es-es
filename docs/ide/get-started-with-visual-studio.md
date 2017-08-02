---
title: "Introducción a Visual Studio | Microsoft Docs"
description: "Obtener información de los aspectos básicos sobre cómo empezar a usar Visual Studio"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 078619c93e18fd25dfbc728d75835f5af58988fe
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="get-started-with-visual-studio"></a>Introducción a Visual Studio

Visual Studio es una herramienta eficaz para desarrollar aplicaciones. Si todavía no lo ha hecho, descargue e instale [Visual Studio](https://www.visualstudio.com/vs/). Vea el vídeo [Introducción a Visual Studio: Configurar el IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) para obtener más información sobre cómo descargar Visual Studio y configurarlo de la manera que quiera.

## <a name="visual-studio-tour"></a>Paseo por Visual Studio
Visual Studio tiene un grupo de barras de herramientas, menús y ventanas de herramientas que, conjuntamente, se denominan el entorno de desarrollo integrado o IDE. El IDE de Visual Studio le ayuda a completar las tareas de desarrollo. Aquí se muestra información general rápida de los elementos de IDE que probablemente use más a menudo.

### <a name="code-editor"></a>Editor de código
Una de las ventanas de herramientas más usadas en Visual Studio. Este es el lugar donde escribe, ve y navega por su código.

![Editor de código](~/docs/ide/media/VSIDE_CodeWindow.png)

A medida que escribe el código, el editor de código le ayuda a escribir y buscar código de manera más rápida y fácil gracias a características como la finalización de instrucciones, la coloración de sintaxis o el modo de mapa. Para obtener más información, vea el vídeo [Introducción a Visual Studio: Editar y navegar por el código](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5).

Algunos tipos de soluciones pueden incluir ventanas denominadas *formularios*, como formularios de Windows Presentation Foundation (WPF), formularios de Windows y formularios de lenguaje XAML, entre otros. En estos casos, también verá un diseñador visual en este espacio que le permite arrastrar y soltar controles, como botones y cuadros de lista, en el formulario, con los que los usuarios interactúan al ejecutar la aplicación.

### <a name="solution-explorer"></a>Explorador de soluciones

Una ventana de herramientas denominada **Explorador de soluciones** enumera todos los archivos de código. El Explorador de soluciones puede ayudar a organizar el código agrupando sus archivos en soluciones y proyectos. El proyecto en negrita se denomina *proyecto de inicio*. Es el primer código que se ejecuta cuando inicia la solución. y, si lo desea, puede cambiarlo. Para obtener más información, vea el vídeo [Introducción a Visual Studio: Crear bloques del IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK).

![Nodos contraídos del Explorador de soluciones](~/docs/ide/media/VSIDE_SolutionExplorer2_callouts.png)

 Además de soluciones y proyectos, el Explorador de soluciones muestra todos los archivos de cada proyecto cuando expande el nodo del proyecto. Cada proyecto contiene uno o más archivos, como archivos de código fuente y archivos de recursos como imágenes o bibliotecas.

![Explorador de soluciones](~/docs/ide/media/VSIDE_SolutionExplorer3.png)

Para ver las propiedades de las soluciones, proyectos y archivos, pulse el comando **Propiedades** en el menú contextual (botón derecho) o pulse **Ver, ventana Propiedades** en el menú.

![Propiedades (ventana)](~/docs/ide/media/VSIDE_SolutionExplorer4.png)

No es necesario crear una solución o un proyecto para empezar a trabajar con código. Simplemente puede abrir directamente archivos de código en Visual Studio, como archivos clonados de un repositorio de Git, y empezar a editarlos de inmediato. Los archivos aparecerán en el Explorador de soluciones y obtendrán la coloración de sintaxis y la finalización de instrucciones básica, entre otros, como en las soluciones tradicionales. Consulte [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) para obtener más información.

### <a name="toolbar-and-menus"></a>Barra de herramientas y menús
Para ejecutar el proyecto, crear nuevas soluciones, guardar archivos y mucho más, use los comandos del menú y la barra de herramientas de Visual Studio. Por ejemplo, una vez que el código esté listo para ejecutarse para la depuración, puede seleccionar el botón **Iniciar** de la barra de herramientas o puede pulsar **Depurar, Iniciar depuración** en el menú. Para crear una solución nueva, pulse el botón **Nuevo proyecto** o pulse **Archivo, Nuevo, Proyecto** en el menú, y así sucesivamente.

![Barra de herramientas de Visual Studio](~/docs/ide/media/VSIDE_SolutionExplorer5_callouts.png)

Tenga en cuenta que los iconos de la barra de herramientas y los comandos de menú pueden cambiar dependiendo del contexto, lo que afecta al elemento seleccionado actualmente. Se puede acceder a casi todos los comandos mediante comandos de teclado, así como a través de un mouse.

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** le permite conectarse a herramientas de control de código fuente como [Git](https://git-scm.com/) y [Control de versiones de Team Foundation (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview) para almacenar su código localmente o compartirlo con otros usuarios en un servicio hospedado. También puede usarlo para realizar el seguimiento de tareas y mucho más.

Vea los vídeos [Introducción a Visual Studio: Crear bloques del IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) e [Introducción a Visual Studio: Abrir un proyecto del control de código fuente](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3) para obtener más información.

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>Resultados (ventana)
La ventana de **Salida** es el lugar en el que Visual Studio envía sus notificaciones, como mensajes de error y de depuración, advertencias del compilador, mensajes de estado de publicación, etc. Cada tipo de mensaje tiene su propia pestaña.

![Resultados (ventana)](~/docs/ide/media/VSIDE_OutputWindow.png)

Para obtener más información sobre cómo usar la ventana de salida para la depuración, vea [The Output window while debugging with Visual Studio (La ventana de salida al depurar con Visual Studio)](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/).

## <a name="first-steps"></a>Primeros pasos
- **Obtenga una visión general**: para obtener una visión general de muchas de las características principales de Visual Studio, ¡dé un paseo! Consulte [Paseo por las características del IDE de Visual Studio](../ide/visual-studio-ide.md).
- **Instalación**: para obtener información sobre cómo descargar e instalar Visual Studio, vea [Instalación de Visual Studio 2017](../install/install-visual-studio.md).
- **Los aspectos básicos**: Para obtener más información sobre el funcionamiento de Visual Studio, vea [Introducción al desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md).
- **Configuración**: para obtener información sobre cómo personalizar Visual Studio para que se adapte a la forma en que desea trabajar. Vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).
- **Tutoriales**: Para obtener más información sobre cómo desarrollar código en Visual Studio, vaya a un tutorial, como [Introducción a Visual C# y Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) o [Introducción a C++ en Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md).
- **Vídeos**: para obtener más información sobre otras características y aspectos de Visual Studio, consulte los vídeos en el [canal de Microsoft Visual Studio](https://www.youtube.com/user/VisualStudio/videos) en YouTube, vídeos de Visual Studio en [Channel 9](https://channel9.msdn.com/Tags/visual+studio) o en [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer).

## <a name="access-cloud-based-resources"></a>Acceso a los recursos basados en la nube

Si quiere usar recursos basados en la nube en su aplicación o juego, incluya [servicios de Azure](https://azure.microsoft.com/en-us/services/). Para obtener Azure SDK para .NET, instale la carga de trabajo de **desarrollo de Azure** con el nuevo instalador de Visual Studio. Los paquetes que se instalan presentan el mismo nivel de características que la versión 2.9.5 del SDK. Para esta versión de Visual Studio y todas las versiones futuras, el SDK de Azure para .NET solo estará disponible desde el instalador de Visual Studio.

Después de instalar la carga de trabajo de desarrollo de Azure, aparece una nueva ventana de herramientas denominada **Cloud Explorer** en Visual Studio. Cloud Explorer le permite examinar y administrar los recursos y activos de Azure desde Visual Studio. Si una operación determinada requiere Azure Portal, Cloud Explorer proporciona vínculos que le dirigen al lugar de Azure Portal que necesita ir.

![Cloud Explorer](~/docs/ide/media/VSIDE_CloudExplorer.png)

Para obtener más información sobre cómo usar Cloud Explorer, vea [Administración de recursos de Azure con Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
La instalación de la carga de trabajo de desarrollo de Azure también le proporciona [Visual Studio Tools para Azure](https://www.visualstudio.com/vs/azure-tools/), así como otras herramientas.

## <a name="tips-and-tricks"></a>Sugerencias y trucos
Para obtener combinaciones de teclas y sugerencias y trucos útiles sobre cómo aprovechar al máximo Visual Studio, vea lo siguiente.
- [Getting Started with Visual Studio - Tips & Tricks (Introducción a Visual Studio: sugerencias y trucos)](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)
- [Sugerencias de productividad para Visual Studio](../ide/productivity-tips-for-visual-studio.md)
- [Visual Studio Tips and Tricks (Sugerencias y trucos para Visual Studio)](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [C++ Debugging Tips and Tricks (Sugerencias y trucos para la depuración de C++)](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)
- [Visual Studio's most useful (and underused) tips [Scott Hanselman blog]](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx) (Sugerencias más útiles [y menos utilizadas] de Visual Studio [Blog de Scott Hanselman])
- [Getting Started with Visual Studio - Installing Visual Studio extensions (Introducción a Visual Studio: instalación de las extensiones de Visual Studio)](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)

