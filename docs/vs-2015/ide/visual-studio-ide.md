---
title: Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6bd4e34e25add01de6e6e54c2439c2ca80ccf33
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062488"
---
# <a name="visual-studio-ide"></a>IDE de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 es un conjunto de herramientas para crear software, desde la fase de diseño pasando por la fases de diseño de la interfaz de usuario, codificación, pruebas, depuración, análisis de la calidad y el rendimiento del código, implementación en los clientes y recopilación de telemetría de uso. Estas herramientas están diseñadas para trabajar juntas de la forma más eficiente posible y todas se exponen a través del Entorno de desarrollo integrado (IDE) de Visual Studio.

Puede usar Visual Studio para crear muchos tipos de aplicaciones, desde sencillas aplicaciones y juegos de la Tienda para clientes móviles, hasta sistemas grandes y complejos para empresas y centros de datos. Puede crear:

- aplicaciones y juegos que se ejecutan no solo en Windows, sino también en Android y en iOS;

- sitios web y servicios web basados en ASP.NET, JQuery, AngularJS y otros entornos populares;

- aplicaciones para dispositivos y plataformas tan diversas como Azure, Office, SharePoint, Hololens, Kinect e Internet de las cosas, por nombrar solo algunos ejemplos;

- juegos y aplicaciones con gráficos avanzados para una variedad de dispositivos Windows, incluido Xbox, con DirectX.

De forma predeterminada, Visual Studio proporciona compatibilidad con C#, C y C++, JavaScript, F# y Visual Basic. Visual Studio funciona y se integra bien con aplicaciones de terceros como Unity a través de la extensión [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) , y Apache Cordova a través de [Visual Studio Tools para Apache Cordova](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Puede extender Visual Studio usted mismo creando herramientas personalizadas que realizan tareas especializadas.

Si nunca ha utilizado Visual Studio, descubra los aspectos básicos con nuestros tutoriales y visitas guiadas [Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md) .

Si desea obtener información sobre las nuevas características de Visual Studio 2015, consulte [What ' s New in Visual Studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Instalación de Visual Studio
 Puede averiguar qué edición de Visual Studio es adecuada para usted en [Ediciones de Visual Studio](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Puede instalar Visual Studio 2015 descargándolo en [Descargas de Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Si necesita más información sobre el proceso de instalación, vea [Instalación de Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Conceptos básicos del IDE
 La siguiente imagen muestra el IDE de Visual Studio con un proyecto abierto, la ventana Explorador de soluciones para desplazarse por los archivos de proyecto y la ventana de Team Explorer para navegar por el código fuente y controlar los elementos de trabajo. A continuación se explican con más detalle las características de la barra de título mencionadas.

 ![IDE de Visual Studio](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Iniciar sesión
 Cuando se inicia Visual Studio por primera vez, puede iniciar sesión con su cuenta de Microsoft o con su cuenta de trabajo o escuela. Iniciar sesión le permite sincronizar la configuración (como la disposición de ventanas) entre varios dispositivos y conectarse automáticamente a los servicios que pueda necesitar, como las suscripciones de Azure y Visual Studio Team Services. Si tiene una licencia de suscripción, deberá iniciar sesión Visual Studio de forma periódica para mantener actualizado su token de licencia. Si tiene una licencia de clave de producto, no tiene que iniciar sesión, pero hacerlo le permitirá conectarse más cómodamente a Visual Studio Team Services y a sus cuentas con Azure, Office 365, Salesforce.com. Para obtener más información, vea [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md).

 Si tiene varias cuentas de Visual Studio Team Services, cuentas de Azure o suscripciones a MSDN, puede vincularlas y acceder a los recursos y servicios de todas las cuentas con un inicio de sesión único. Para obtener más información, consulta [Work with multiple user accounts](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Mantenerse actualizado
 El icono de notificación en la esquina superior derecha de la barra de título le avisa cuando hay actualizaciones disponibles para Visual Studio o para otros componentes relacionados que haya instalado. Puede elegir si desea descartar estas notificaciones o actuar sobre ellas. Para obtener más información, consulte [Notificaciones de Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Realizar búsquedas y obtener ayuda
 La ventana [Inicio rápido](../ide/reference/quick-launch-environment-options-dialog-box.md) que se muestra más abajo es una forma rápida de buscar los comandos, las herramientas o las características de Visual Studio si no conoce la ubicación del menú o el método abreviado de teclado. Escriba lo que está buscando e Inicio rápido le proporcionará un vínculo.

 ![Resultados de inicio rápido para "nuevo proyecto"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN es el sitio web de documentación técnica; en este momento está leyendo esta página en MSDN. En Visual Studio, puede presionar **F1** para ir a la página de ayuda de MSDN de la ventana activa. También puede presionar **F1** en el editor de código para ir a la página de ayuda de MSDN para la API o la palabra clave que está en la posición actual del símbolo de intercalación. Por ejemplo, en un archivo de C#, podría colocar el símbolo de intercalación en algún lugar dentro o al final de una declaración `System.String` y, después, presionar **F1** para ir a la página de ayuda de MSDN de <xref:System.String>.

### <a name="giving-feedback"></a>Enviar comentarios
 Es fácil enviar comentarios sobre Visual Studio siempre que quiera. Haga clic en el icono de comentarios de la barra de título junto a **Inicio rápido** y, después, haga clic en **Notificar un problema** u **Ofrecer una sugerencia**. Las ediciones preliminares de Visual Studio también tienen una opción para **Calificar este producto** . Consultamos todos estos comentarios y los usamos para mejorar el producto. Para obtener más información, consulta [Talk to Us](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personalizar el IDE
 Puede personalizar el diseño de las ventanas para que se ajuste a su estilo de desarrollo. Puede acoplar, hacer flotar u ocultar cualquier ventana en cualquier momento, y también puede ejecutar el editor en modo de pantalla completa. Puede crear y guardar varios diseños de ventanas personalizados que muestren solo las ventanas que necesita para contextos específicos. Por ejemplo, puede crear un diseño de pantalla completa para que todo lo que vea sea el editor de código. Y puede crear diseños diferentes para la depuración y para las operaciones del equipo. Para obtener más información, vea [Personalizar los diseños de ventana](../ide/customizing-window-layouts-in-visual-studio.md).

 Puede personalizar Visual Studio de muchas otras formas y trasladar la configuración si trabaja en varios equipos. Para obtener más información, vea [Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md).

 Hay métodos abreviados de teclado para casi todo, y puede personalizarlos también. Para crear nuevos métodos abreviados, escriba "Teclado" en el Inicio rápido para abrir el cuadro de diálogo Teclado. Allí puede presionar F1 para ir a la página de ayuda de MSDN si necesita más información acerca de las opciones. Para obtener más información, consulte [Métodos abreviados de teclado predeterminados de Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Conectarse a Visual Studio Team Services y Team Foundation Server
 Visual Studio Team Services (VSTS) es un servicio en la nube para hospedar proyectos de software y que permite la colaboración en los equipos. VSTS admite los sistemas de control de código fuente Git y Team Foundation, así como las metodologías de desarrollo Scrum, CMMI y Agile. El control de versiones de Team Foundation (TFVC) usa un solo repositorio del servidor centralizado para los archivos de seguimiento y de versión. Los cambios locales siempre se protegen en el servidor central, donde otros desarrolladores pueden obtener los cambios más recientes. Team Foundation Server (TFS) 2015 es el centro de administración del ciclo de vida de aplicación de Visual Studio. Permite a todas las partes interesadas en el proceso de desarrollo participar con una única solución. TFS es útil para administrar equipos heterogéneos y también proyectos.

 Si tiene una cuenta de Visual Studio Team Services o Team Foundation Server en la red, conéctese a ella en la ventana de Team Explorer. Desde esta ventana puede proteger o desproteger código en el control de código fuente, administrar elementos de trabajo, iniciar compilaciones y acceder a los salones y las áreas de trabajo del equipo. Puede abrir Team Explorer desde **inicio rápido** o en el menú principal de **vista &#124; Team Explorer** o desde **equipo &#124; administrar conexiones**.  Para más información sobre Visual Studio Online, consulte [www.visualstudio.com](https://www.visualstudio.com/). Para más información sobre Team Foundation Server, vea [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 En la siguiente imagen se muestra el panel Team Explorer de una solución que se hospeda en VSTS:

 ![Visual Studio Team Explorer](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Crear soluciones y proyectos
 Aunque puede usar Visual Studio para examinar archivos de código individuales, normalmente trabajará en un *proyecto*. Un proyecto de Visual Studio es una colección de archivos y recursos que, en el caso de las aplicaciones, se compilan en un solo archivo ejecutable binario (por ejemplo, .exe, DLL, appx, etc.). En el caso de sitios web que no sean ASP.NET, no se genera ningún archivo ejecutable y el proyecto contiene solo los archivos HTML y JavaScript e imágenes. Como a veces quizás tenga que crear varios archivos binarios o sitios web que están estrechamente relacionados, Visual Studio tiene el concepto de solución, que puede contener varios proyectos o sitios web. Cuando se crea un proyecto, en realidad está creando un proyecto en una solución, y más adelante puede agregar más proyectos a esa solución si es necesario. Por ejemplo, si tiene un proyecto DLL, puede agregar a la solución un proyecto .exe que carga y usa el archivo DLL.

 Una *plantilla de proyecto* es una colección de archivos de código y opciones de configuración previamente rellenados que permite preparar rápidamente la creación de un tipo específico de aplicación. Visual Studio incluye numerosas plantillas de proyecto para elegir pero, si no le sirve ninguna de las plantillas predeterminadas, puede crear las suyas propias. Después de crear un proyecto con una plantilla, puede empezar a escribir su propio código en él, en los archivos proporcionados o en los nuevos archivos que agregue. Para obtener más información, vea [Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md). La ilustración siguiente muestra el cuadro de diálogo Nuevo proyecto con las plantillas de proyecto que hay disponibles para las aplicaciones ASP.NET.

 ![Cuadro de diálogo nuevo proyecto de Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Diseñar la interfaz de usuario
 Un diseñador es una herramienta intuitiva que permite crear una interfaz de usuario sin escribir código. Puede arrastrar los controles de interfaz de usuario, como cuadros de lista, calendarios y botones, desde la ventana [Toolbox](../ide/reference/toolbox.md) hasta una superficie de diseño que represente el cuadro de diálogo o la ventana. Puede cambiar el tamaño y reorganizar los elementos sin escribir ningún código. Se incluyen diseñadores para cualquier tipo de proyecto que tenga una interfaz de usuario.

 Si el proyecto tiene una interfaz de usuario basada en XAML, el diseñador predeterminado es Blend para Visual Studio, una sofisticada herramienta de gráficos que funciona sin problemas con Visual Studio.

 ![Mesa de trabajo](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Vista Diseño** Muestra el diseño visual del documento. En esta vista, puede dibujar o modificar objetos de la superficie de diseño.|
|![](../designers/media/b1-2.png "B1_2")|**Ruta de navegación** Permite desplazarse rápidamente entre el modo de edición de plantillas, el modo de edición de estilos y el ámbito de edición de objetos para un objeto seleccionado.|
|![](../designers/media/b1-3.png "B1_3")|**Zoom** Sirve para acercar o alejar la superficie de diseño o los objetos que se encuentran en ella.|
|![](../designers/media/b1-4.png "B1_4")|**Controles de la superficie de diseño** Use estos controles (**Mostrar cuadrícula de ajuste**, **Ajustar a las líneas de la cuadrícula** y **Activar o desactivar ajuste a las guías de alineación**) para definir opciones de ajuste. El ajuste sirve para alinear objetos entre sí o en líneas con un espaciado uniforme en la superficie de diseño.|
|![](../designers/media/b1-5.png "B1_5")|**Editor de código** Edite el código XAML, C#, C++ o Visual Basic de forma manual en el Editor de código.|

 Para obtener más información, consulte [diseñar XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Escribir código, desplazarse por él y comprenderlo
 Si es programador, la ventana del editor es el lugar donde probablemente pasará la mayor parte del tiempo. Visual Studio incluye editores para C#, C++, Visual Basic, JavaScript, XML, HTML, CSS y F#, así como complementos editores (y compiladores) de terceros para muchos otros lenguajes.

 Puede modificar archivos individuales en el editor de texto haciendo **archivo &#124; abierto &#124; archivo.** Para editar archivos en un proyecto abierto, haga clic en el nombre de archivo en el Explorador de soluciones. Se colorea el código y puede personalizar la combinación de colores escribiendo "Colores" en el inicio rápido. Puede tener muchas ventanas en pestañas del editor de texto abiertas a la vez. Puede dividir cada ventana de forma independiente. También puede ejecutar el editor de texto en modo de pantalla completa.

 ![GreetingsConsoleApp.cpp en el editor de código](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn C ++")

 El editor de texto es sumamente interactivo (si quiere que lo sea) con muchas características de productividad que le ayudarán a escribir código mejor y más rápidamente. Las características varían según el lenguaje y no tiene que usar cualquiera de ellos (escriba "Editor" en el inicio rápido) para activar o desactivar las características: Algunas de las características de productividad comunes son:

1. [Refactoring](../ide/refactoring-in-visual-studio.md) incluye operaciones tales como el cambio inteligente de nombre de las variables, mover líneas seleccionadas de código a una función diferente, mover código a otras ubicaciones, reordenar los parámetros de una función y mucho más.

2. *IntelliSense* es un término que aglutina un conjunto de características muy populares que muestran información escritura sobre el código directamente en el editor y, en algunos casos, escriben pequeños fragmentos de código automáticamente. Básicamente, IntelliSense es como tener documentación básica insertada en el editor, lo que evita tener que buscar información de escritura en una ventana de ayuda independiente. Las características de IntelliSense varían según el lenguaje. Para más información, consulte [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic-Specific IntelliSense](../ide/visual-basic-specific-intellisense.md). La ilustración siguiente muestra algunas características de IntelliSense en funcionamiento:

    ![Lista de miembros de Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. Los**subrayados ondulados** le avisan de errores o posibles problemas en el código en tiempo real a medida que escribe, lo que permite corregirlos inmediatamente sin esperar a que el error se detecte en tiempo de compilación o de ejecución. Si mantiene el mouse sobre la línea ondulada, verá información adicional sobre el error. También puede aparecer una bombilla en el margen izquierdo con sugerencias para corregir el error. Para obtener más información, consulta [Perform quick actions with light bulbs](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Bombilla con mantener el puntero del mouse](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. Los [marcadores](../ide/setting-bookmarks-in-code.md) le permiten ir rápidamente a líneas específicas en los archivos en los que está trabajando activamente.

5. En el menú contextual del editor de texto, puede invocar la ventana [Call Hierarchy](../ide/reference/call-hierarchy.md) para mostrar los métodos que llaman a y son llamados por el método situado por debajo del símbolo de intercalación.

6. **Code Lens** permite buscar referencias y cambios en el código, errores vinculados, elementos de trabajo, revisiones de código y pruebas unitarias, todo sin salir del editor. Para obtener más información, vea [Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md).

7. La ventana **Ojear la definición** muestra un método o definición de tipo en línea, sin salir del contexto actual. Esta ventana ahora funciona también para XAML.

8. La opción de menú contextual **Ir a definición** le lleva directamente al lugar donde se definen la función o el objeto. También hay otros comandos de navegación disponibles haciendo clic con el botón secundario en el editor.

9. La herramienta relacionada [Examinador de objetos](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) permite inspeccionar ensamblados .NET o Windows Runtime en el sistema para ver qué tipos contienen y qué métodos y propiedades contienen esos tipos.

     ![Examinador de objetos que muestra System.Timer](../ide/media/objectbrowser.png "ObjectBrowser")

   La mayoría de los elementos de los menús Editar y Ver se relacionan con el editor de código de alguna manera. Para obtener más información sobre el editor, vea [Writing Code (Escribir código)](../ide/writing-code-in-the-code-and-text-editor.md) y [Edición del código](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Compilar y generar el código

Compilar un proyecto significa compilar el código fuente y realizar los pasos necesarios para generar el archivo ejecutable. Los distintos lenguajes tienen operaciones de compilación diferentes y los sitios web normales no se compilan. Independientemente del tipo de proyecto, el menú Compilar es la ubicación estándar de estos comandos. Para compilar y ejecutar el código con una sola pulsación de tecla, presione F5. Cada compilador se puede configurar totalmente mediante el IDE. La barra de herramientas Compilar permite especificar si se va a compilar una versión de depuración del programa, con símbolos y comprobación de errores adicional habilitados para admitir puntos de interrupción y ejecución paso a paso en el depurador, o una compilación de versión, que es lo que finalmente proporcionará a los clientes. Puede configurar más opciones de compilación y muchas otras opciones en la página de propiedades de un proyecto. Haga clic con el botón secundario en el nodo de proyecto en el Explorador de soluciones y elija Propiedades. También puede ejecutar compilaciones desde la línea de comandos.

La salida de la compilación, incluidos los mensajes de error o éxito, aparecen en la ventana **Salida**. El **lista de errores** muestra información detallada sobre los errores de compilación.

## <a name="debugging-your-code"></a>Depurar el código
 El vanguardista depurador de Visual Studio le permite depurar el código que se ejecuta en su proyecto local, en un dispositivo remoto o en un emulador, como los de Android o Windows Phone. Puede ejecutar el código instrucción por instrucción e inspeccionar las variables en cada paso, puede ejecutar paso a paso aplicaciones multiproceso y puede establecer puntos de interrupción que solo se producen cuando se cumple una condición especificada. Todo esto se puede configurar en el propio editor de código para que no tenga que salir del contexto del código.

 ![Vista de ventana de configuración del punto de interrupción](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 El propio depurador tiene varias ventanas que le permiten ver y manipular las variables locales, la pila de llamadas y otros aspectos del entorno en tiempo de ejecución. Encontrará estas ventanas en el menú **Depurar** .

 [Immediate Window](../ide/reference/immediate-window.md) permite escribir en una expresión y ver su resultado inmediatamente.

 La ventana [IntelliTrace](http://msdn.microsoft.com/en-us/629e9660-c59a-446b-8c30-290059158f61) registra cada llamada a métodos y otros eventos en un programa de .NET en ejecución, que puede ayudar a encontrar rápidamente dónde se origina un problema.

 Para obtener más información, vea [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Probar el código
 Visual Studio incluye un entorno de pruebas unitarias para código administrado (.NET) y otro para C++ nativo. Para crear pruebas unitarias, basta con agregar un proyecto de prueba a la solución, escribir las pruebas y, después, ejecutarlas desde la ventana Explorador de pruebas. Para obtener más información, vea [Haga una prueba unitaria de su código](../test/unit-test-your-code.md).

 ![Explorador de pruebas unitarias](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analizar la calidad y el rendimiento del código
 Visual Studio incluye herramientas eficaces para el análisis estático y en tiempo de ejecución. Las herramientas de análisis estático ayudan a identificar posibles errores de diseño, globalización, interoperabilidad, rendimiento, seguridad y otras categorías. Las pruebas de rendimiento o de generación de perfiles implican medir cómo se ejecuta el programa. A estas herramientas se accede desde el menú **Analizar** . Para obtener más información, consulte [Mejorar la calidad con las herramientas de diagnóstico de Visual Studio](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Conectarse a bases de datos y servicios en la nube
 La ventana [Explorador de servidores](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) de Visual Studio muestra los recursos de todas las cuentas administradas en su cuenta de personalización (con la que inició sesión), incluidas las instancias de SQL Server, Azure, Salesforce.com, Office 365 y los sitios web.

 ![Explorador de servidores](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio incluye [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), que permiten compilar, depurar, mantener y refactorizar bases de datos. Puede trabajar con un proyecto de base de datos o directamente con una instancia de base de datos conectada de manera local o externa.

 El Explorador de objetos de SQL Server en Visual Studio ofrece una vista de los objetos de base de datos similar a la de SQL Server Management Studio. El Explorador de objetos de SQL Server permite realizar trabajos ligeros de administración y diseño de bases de datos, incluida la edición de datos de tabla, comparación de esquemas y ejecución de consultas mediante los menús contextuales directamente desde el Explorador de objetos de SQL Server. SSDT también incluye tipos de proyecto especiales y herramientas para desarrollar soluciones de SQL Server 2012 Analysis Services, Reporting Services e Integration Services Business Intelligence (BI), antes conocido como Business Intelligence Development Studio.

 ![Explorador de objetos de SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Implementar la aplicación finalizada
 Cuando la aplicación está lista para implementarse en los clientes, Visual Studio proporciona las herramientas para hacerlo, ya sea para implementar en la Tienda Windows, en un sitio de Sharepoint o usando las tecnologías Installshield o Windows Installer. Todo está disponible a través del IDE. Para obtener más información, consulte [Implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Herramientas de arquitectura y modelado (solo en Enterprise)
 Puede usar las herramientas de arquitectura y modelado de Visual Studio para diseñar y modelar la aplicación. Estas herramientas ayudan a visualizar la estructura del código, su comportamiento y sus relaciones. Puede crear modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo. Puede controlar los requisitos, las tareas, los casos de prueba, los errores y otros trabajos asociados con los modelos mediante la vinculación de elementos del modelo a elementos de trabajo de Team Foundation Server y su plan de desarrollo. Para obtener más información, consulte [Diseñar y modelar la aplicación](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Extender Visual Studio mediante el SDK de Visual Studio
 Visual Studio es una plataforma extensible. Una extensión de Visual Studio es una herramienta personalizada que se integra con el IDE. Puede agregar extensiones de terceros o crear las suyas propias. Para obtener más información, consulte [Desarrollar extensiones de Visual Studio](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 Las [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) son una referencia esencial para todo aquel que escriba extensiones para Visual Studio. Estas directrices específicas para cada plataforma incluyen información sobre el diseño de cuadros de diálogo, fuentes, colores, iconos, controles comunes y otros patrones de interacción que harán que la nueva característica se integren perfectamente con Visual Studio.

## <a name="in-this-guide"></a>En esta guía

|||
|-|-|
|[Cuentas de usuario y actualizaciones](../ide/user-accounts-and-updates.md)|[Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)|
|[Cómo: moverse por el IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Introducción al desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|
|[Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|[Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)|
|[Escribir código](../ide/writing-code-in-the-code-and-text-editor.md)|[Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Herramientas de generación de perfiles](../profiling/profiling-tools.md)|[Mejorar la calidad del código](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Diseño de interfaces de usuario](../designers/designing-user-interfaces.md)|[Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)|
|[Compilar y generar en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)|[Implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md)|
|[Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)|[Seguridad](../ide/security-in-visual-studio.md)|
|[Ejemplos de Visual Studio](../ide/visual-studio-samples.md)|[Visor de Ayuda de Microsoft](../ide/microsoft-help-viewer.md)|
|[Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)|[Referencia de la interfaz de usuario](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Vea también

- [Instalación de Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Edición del código](https://www.visualstudio.com/features/ide-vs)
- [Novedades de Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Hable con nosotros](../ide/talk-to-us.md)