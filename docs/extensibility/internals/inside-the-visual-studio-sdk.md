---
title: "En el SDK de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plan de integración de Visual Studio SDK"
  - "Plan SDK de integración de Visual Studio"
  - "plan de integración, el SDK de Visual Studio"
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# En el SDK de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta sección proporciona información detallada acerca de las extensiones de Visual Studio, incluida la arquitectura de Visual Studio, componentes, servicios, esquemas, utilidades y similares.  
  
## Arquitectura de extensibilidad  
 La siguiente ilustración muestra la arquitectura de extensibilidad de Visual Studio. VSPackages proporciona la funcionalidad de la aplicación, que se comparte entre el IDE como servicios. El IDE estándar también ofrece una amplia gama de servicios, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que proporcionan acceso a la funcionalidad de ventana IDE.  
  
 ![Gráfico de arquitectura de entorno](../../extensibility/internals/media/environment.png "environment")  
Vista general de la arquitectura de Visual Studio  
  
## VSPackages  
 Los VSPackages son módulos de software que conforman y amplían Visual Studio con los elementos de interfaz de usuario, servicios, proyectos, editores y diseñadores. Los VSPackages son la unidad de la arquitectura central de Visual Studio. Para obtener más información, consulta [VSPackages](../../extensibility/internals/vspackages.md).  
  
## Visual Studio Shell  
 El shell de Visual Studio proporciona funcionalidad básica y admitir la comunicación cruzada entre sus extensiones de componente VSPackages y MEF. Para obtener más información, consulta [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## Instrucciones para la experiencia de usuario  
 Si va a diseñar nuevas características de Visual Studio, debería echarle un vistazo a estas directrices para obtener sugerencias de diseño y facilidad de uso: [Instrucciones para la experiencia de usuario de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Comandos  
 Comandos son funciones que realizar tareas, como la impresión de un documento, al actualizar una vista o crear un nuevo archivo.  
  
 Al extender Visual Studio, puede crear comandos y regístrelos con el shell de Visual Studio. Puede especificar cómo estos comandos aparecerán en el IDE, por ejemplo, en un menú o barra de herramientas. Un comando personalizado aparece normalmente en el **herramientas** aparecerán menús y un comando para mostrar una ventana de herramientas en el **otras ventanas** submenú de la **vista** menú.  
  
 Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o está habilitado, permite modificar su texto y garantiza que el comando responde correctamente cuando se activa. En la mayoría de los casos, el IDE controla los comandos utilizando la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Comandos de Visual Studio se controlan empezando por el contexto de comandos más interno, según la selección local y continuar con el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para secuencias de comandos.  
  
 Para obtener más información, consulta [Barras de herramientas, menús y comandos](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Menús y barras de herramientas  
 Menús y barras de herramientas proporcionan una manera para que los usuarios invocar comandos. Los menús están filas o columnas de los comandos que normalmente se muestran como elementos individuales de texto en la parte superior de una ventana de herramientas. Submenús son menús secundarios que aparecen cuando un usuario hace clic en los comandos que incluyen una pequeña flecha. Los menús contextuales aparecen cuando un usuario hace clic con botón ciertos elementos de interfaz de usuario. Algunos nombres de menú comunes son **archivo**, **Editar**, **vista**, y **ventana**. Para obtener más información, consulta [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
 Barras de herramientas son filas o columnas de botones y otros controles, como cuadros combinados, cuadros de lista y cuadros de texto. Botones de barra de herramientas suelen tienen imágenes de icono, como un icono de carpeta para una **Abrir archivo** comando o una impresora para un **Imprimir** comando. Todos los elementos de la barra de herramientas están asociados con los comandos. Al hacer clic en un botón de barra de herramientas, se ejecuta el comando asociado. En el caso de un control de lista desplegable, cada elemento de la lista desplegable está asociado con un comando distinto. Algunos controles de barra de herramientas, como un control divisor, son híbridos. Un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra varios comandos cuando se hace clic.  
  
## Ventanas de herramientas  
 Ventanas de herramientas se utilizan en el IDE para mostrar información.**Herramientas**, **el Explorador de soluciones**, **propiedades** ventana, y **explorador Web** son ejemplos de ventanas de herramientas.  
  
 Ventanas de herramientas normalmente ofrecen diversos controles con la que pueda interactuar el usuario. Por ejemplo, el **propiedades** ventana permite al usuario establecer las propiedades de objetos que sirven para un propósito determinado. El **propiedades** ventana está especializada en este sentido, pero también general porque se puede utilizar en muchas situaciones diferentes. De forma similar, el **salida** ventana especializada porque proporciona resultados basados en texto, pero general porque muchos subsistemas en Visual Studio pueden utilizar para proporcionar resultados al usuario de Visual Studio.  
  
 Considere la siguiente imagen de Visual Studio, que contiene varias ventanas de herramientas.  
  
 ![Captura de pantalla](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Algunas de las ventanas de herramientas están acopladas juntas en un panel que muestra la ventana de herramientas del explorador de soluciones y oculta las otras ventanas de herramientas, pero hace disponibles haciendo clic en fichas. La imagen muestran dos ventanas de herramientas, el **lista de errores** y **salida** ventana, acoplada juntas en un solo panel.  
  
 También se muestra es el panel de documento principal, que muestra varias ventanas del editor. Aunque las ventanas de herramientas normalmente tienen una sola instancia \(por ejemplo, puede abrir sólo uno **el Explorador de soluciones**\), ventanas del editor pueden tener varias instancias, cada uno de los cuales se usa para editar un documento independiente, pero todos ellos se acoplan en el mismo panel. La imagen muestra un panel de documento que tiene dos ventanas del editor, una ventana de diseñador de formularios y una ventana del explorador que muestra la página de inicio. Todas las ventanas en el panel de documento están disponibles haciendo clic en fichas, pero la ventana del editor que contiene el archivo EditorPane.cs está visible y activo.  
  
 Al extender Visual Studio, puede crear herramienta interactúan de windows que permiten a los usuarios de Visual Studio con la extensión. También puede crear sus propios editores que permiten a los usuarios de Visual Studio editar documentos. Los editores y ventanas de herramientas se integrarán en Visual Studio, que no tiene programarlos para acoplar o aparezcan correctamente en una pestaña. Están registrados correctamente en Visual Studio, automáticamente tienen las características típicas de ventanas de herramientas y ventanas de documento en Visual Studio. Para obtener más información, consulta [Ampliación y personalización de ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## Ventanas de documento  
 Una ventana de documento es una ventana secundaria con marcos de una ventana de interfaz de múltiples documentos \(MDI\). Ventanas de documento se utilizan normalmente para hospedar controles de edición, editores de formulario \(también conocido como diseñadores\) o editores de texto, pero también pueden alojar otros tipos funcionales. El **nuevo archivo** cuadro de diálogo incluye ejemplos de ventanas de documento que proporciona Visual Studio.  
  
 La mayoría de los editores son específicos de un lenguaje de programación o a un tipo de archivo, como páginas HTML, conjuntos de marcos, archivos de C\+\+ o archivos de encabezado. Al seleccionar una plantilla en el **nuevo archivo** cuadro de diálogo, un usuario crea dinámicamente una ventana de documento para el editor para el tipo de archivo que está asociado a la plantilla. También se crea una ventana de documento cuando un usuario abre un archivo existente.  
  
 Ventanas de documento se restringirá al área de cliente MDI. Cada ventana de documento tiene una ficha en la parte superior y orden de tabulación está vinculado a otras ventanas que pueden estar abiertos en el área MDI. Hacer clic en la ficha de una ventana de documento aparece un menú contextual que incluye opciones para dividir el área MDI en varios de los grupos de pestañas horizontal o vertical. Dividir el área MDI permite varios archivos para ver al mismo tiempo. Para obtener más información, consulta [Ventanas de documento](../../extensibility/internals/document-windows.md).  
  
## Editores  
 El editor de Visual Studio permite personalizar y usar su propio tipo de contenido por medio de Managed Extensibility Framework \(MEF\). En muchos casos no necesitará crear un VSPackage para ampliar el editor, aunque si van a incluir características desde el shell \(por ejemplo, un comando de menú o una tecla de método abreviado\), puede combinar una extensión MEF con un VSPackage.  
  
 También puede crear un editor personalizado, por ejemplo si desea leer y escribir en una base de datos o si desea usar un diseñador. También puede utilizar un editor externo, como el Bloc de notas o Microsoft WordPad. Para obtener más información, consulta [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
## Servicios de lenguaje  
 Si desea que el editor de Visual Studio para admitir nuevas palabras clave de programación o incluso un nuevo lenguaje de programación, cree un servicio de lenguaje. Cada servicio de lenguaje puede implementar determinadas características del editor totalmente, parcialmente o nada. Según cómo esté configurada, el servicio de lenguaje puede proporcionar resaltado de sintaxis, coincidencia de llaves, compatibilidad con IntelliSense y otras características en el editor.  
  
 En el corazón de un servicio de lenguaje son un analizador y un escáner. Escáner \(o lexer\) divide un archivo de código fuente en elementos que se conocen como tokens y un analizador establece las relaciones existentes entre esos tokens. Al crear un servicio de lenguaje, debe implementar el analizador y el analizador para que Visual Studio pueda entender los tokens y la gramática del lenguaje. Puede crear servicios de lenguaje administrado o no administrado. Para obtener más información, consulta [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## Proyectos  
 En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar y compilar el código fuente y otros recursos. Proyectos permiten organizar, compilar, depurar y distribuir el código fuente, las referencias a servicios Web y bases de datos y otros recursos. VSPackages puede extender el sistema de proyectos de Visual Studio al proporcionar herramientas personalizadas, subtipos de proyecto y tipos de proyecto.  
  
 También pueden recopilar los proyectos en una solución, que es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. Información de estado y de proyecto que pertenece a la solución se almacena en dos archivos de solución, el archivo basado en texto de solución \(.sln\) y el archivo de solución binario usuario opción \(.suo\). Estos archivos son similares a los archivos de grupo \(.vbg\) que se utilizaban en versiones anteriores de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], y el área de trabajo \(.dsw\) y el usuario opciones \(.opt\) los archivos que se utilizaban en versiones anteriores de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Para obtener más información, consulte [Proyectos](../../extensibility/internals/projects.md) y [Soluciones](../../extensibility/internals/solutions.md).  
  
## Plantillas de proyectos y elementos  
 Visual Studio incluye plantillas de proyecto predefinidas y plantillas de elemento de proyecto. Puede también hacer sus propias plantillas o adquirir de plantillas de la Comunidad y, a continuación, integrarlas en Visual Studio. El [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) es el lugar indicado para plantillas y extensiones.  
  
 Las plantillas contienen la estructura de proyecto y los archivos básicos necesarios para crear un tipo determinado de la aplicación, control, biblioteca o clase. Cuando desea desarrollar software que se parece a una de las plantillas, cree un proyecto basado en la plantilla y, a continuación, modifique los archivos en el proyecto.  
  
> [!NOTE]
>  Esta arquitectura de plantilla no es compatible con [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos. Para obtener información sobre cómo crear [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] plantillas de proyecto, vea [Diseñar un asistente](/visual-cpp/ide/designing-a-wizard).  
  
 Para obtener más información, consulta [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Propiedades y opciones  
 El **propiedades** ventana muestra las propiedades de uno o varios elementos seleccionados: [Extender propiedades](../../extensibility/internals/extending-properties.md) páginas de opciones contienen conjuntos de opciones que pertenecen a un componente determinado, como un lenguaje de programación o un paquete VSPackage: [Opciones y páginas de opciones](../../extensibility/internals/options-and-options-pages.md). Configuración es características suelen estar relacionados con la interfaz de usuario que se pueden importar y exportar: [Compatibilidad con la configuración de usuario](../../extensibility/internals/support-for-user-settings.md).  
  
## Servicios de Visual Studio  
 Un servicio proporciona un conjunto específico de interfaces de componentes consumir. Visual Studio proporciona un conjunto de servicios que se puede utilizar los componentes, incluidas las extensiones. Por ejemplo, servicios de Visual Studio permiten ventanas de herramientas se muestra o oculta de forma dinámica, habilitar el acceso a la Ayuda, barra de estado o eventos de interfaz de usuario. El editor de Visual Studio también proporciona servicios que pueden importarse mediante extensiones de editor. Para obtener más información, consulta [Utilizar y proporcionar servicios](../../extensibility/using-and-providing-services.md).  
  
## Depurador  
 El depurador es la interfaz de usuario para los componentes de depuración específica del lenguaje. Si ha creado un nuevo servicio de lenguaje, debe crear un motor de depuración específica para enlazar en el depurador. Para obtener más información, consulta [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Control de código fuente  
 Para obtener información acerca de cómo implementar un complemento de control de código fuente o VSPackage, consulte [Control de código fuente](../../extensibility/internals/source-control.md).  
  
## Asistentes  
 Puede crear un asistente junto con un nuevo tipo de proyecto, para que el asistente le ayuda a los usuarios tomar las decisiones correctas cuando se cree un nuevo proyecto de ese tipo. Para obtener más información, consulta [Asistentes](../../extensibility/internals/wizards.md).  
  
## Herramientas personalizadas  
 Herramientas personalizadas le permiten asociar una herramienta con un elemento en un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Para obtener más información, consulta [Herramientas personalizadas](../../extensibility/internals/custom-tools.md).  
  
## Utilidades VSSDK  
 El VSSDK incluye un conjunto de utilidades que puede que necesite para trabajar con distintos aspectos de VSPackages. Para obtener más información, consulta [Utilidades VSSDK](../../extensibility/internals/vssdk-utilities.md).  
  
## Con Windows Installer  
 En algunos casos debe utilizar el instalador de Windows en lugar de con el instalador VSIX: por ejemplo, debe escribir en el registro. Para obtener información acerca de cómo utilizar Windows Installer con las extensiones, consulte [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## Visor de ayuda  
 Puede integrar su propia ayuda y F1 páginas en el Visor de ayuda. Para obtener más información, consulta [SDK del Visor de Ayuda de Microsoft](../../extensibility/internals/microsoft-help-viewer-sdk.md).