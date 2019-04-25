---
title: Dentro de Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078bf457c798c0be9ac56aad1859c6750881922a
ms.sourcegitcommit: 05d104a14ff357d599ff274f97cd59d464ee4a46
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "57870278"
---
# <a name="inside-the-visual-studio-sdk"></a>Dentro de Visual Studio SDK

En esta sección se proporciona información detallada acerca de las extensiones de Visual Studio, incluida la arquitectura de Visual Studio, componentes, servicios, esquemas, utilidades y similares.

## <a name="extensibility-architecture"></a>Arquitectura de extensibilidad
 En la siguiente ilustración muestra la arquitectura de extensibilidad de Visual Studio. Los paquetes VSPackage proporcionan la funcionalidad de aplicación, que se comparte entre el IDE como servicios. El IDE estándar también ofrece una amplia gama de servicios, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que proporcionan acceso a las funciones de ventana del IDE.

 ![Gráfico de arquitectura de entorno](../../extensibility/internals/media/environment.gif "entorno") generalizado de la vista de la arquitectura de Visual Studio

## <a name="vspackages"></a>VSPackages
 Los VSPackages son módulos de software que conforman y amplían Visual Studio con elementos de interfaz de usuario, servicios, proyectos, editores y diseñadores. Los VSPackages son la unidad central de la arquitectura de Visual Studio. Para obtener más información, consulte [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 El shell de Visual Studio proporciona funcionalidad básica y admite la comunicación cruzada entre sus extensiones de componentes de MEF y VSPackages. Para obtener más información, consulte [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Directrices de la experiencia de usuario
 Si va a diseñar las nuevas características para Visual Studio, debe tomar un vistazo a estas directrices para obtener sugerencias sobre diseño y la facilidad de uso: [Directrices de experiencia de usuario de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Comandos
 Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo.

 Al extender Visual Studio, puede crear comandos y registrarlos en el shell de Visual Studio. Puede especificar cómo estos comandos aparecen en el IDE, por ejemplo, en un menú o barra de herramientas. Un comando personalizado aparece normalmente en el **herramientas** menú y un comando para mostrar una ventana de herramientas aparecería en el **Other Windows** submenú de la **vista** menú.

 Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina cuando el comando es visible o está activado, le permite modificar su texto y garantiza que el comando responde correctamente cuando se activa. En la mayoría de los casos, el IDE controla los comandos mediante el uso de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Comandos de Visual Studio se controlan empezando por el contexto de comandos más interno, según la selección local y continuando hasta el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts.

 Para obtener más información, consulte [comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Los menús y barras de herramientas
 Los menús y barras de herramientas proporcionan una manera para que los usuarios invocar comandos. Los menús están filas o columnas de los comandos que normalmente se muestran como elementos individuales de texto en la parte superior de una ventana de herramientas. Submenús son menús secundarios que aparecen cuando un usuario hace clic en los comandos que incluyen una pequeña flecha. Menús contextuales aparecen cuando un usuario hace clic con botón determinados elementos de interfaz de usuario. Algunos nombres comunes del menú son **archivo**, **editar**, **vista**, y **ventana**. Para obtener más información, consulte [ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Las barras de herramientas son filas o columnas de botones y otros controles, como cuadros combinados, cuadros de lista y cuadros de texto. Botones de barra de herramientas suelen tienen imágenes de icono, como un icono de carpeta para un **abrir archivo** comando o una impresora para un **impresión** comando. Todos los elementos de la barra de herramientas están asociados con los comandos. Al hacer clic en un botón de barra de herramientas, se ejecuta el comando asociado. En el caso de un control de lista desplegable, cada elemento de la lista desplegable está asociado con un comando diferente. Algunos controles de barra de herramientas, como un control divisor, son híbridos. Un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra varios comandos cuando se hace clic en.

## <a name="tool-windows"></a>Ventanas de herramientas
 Ventanas de herramientas se usan en el IDE para mostrar información. **Cuadro de herramientas**, **el Explorador de soluciones**, **propiedades** ventana, y **explorador Web** son ejemplos de ventanas de herramientas.

 Ventanas de herramientas normalmente ofrecen diversos controles con el que el usuario puede interactuar. Por ejemplo, el **propiedades** ventana permite al usuario establecer las propiedades de objetos que sirven para un propósito determinado. El **propiedades** ventana está especializado en este sentido, pero también general porque se puede usar en muchas situaciones diferentes. De forma similar, el **salida** está especializada en la ventana porque proporciona salida basado en texto, pero general porque muchos subsistemas en Visual Studio pueden usar para proporcionar la salida para el usuario de Visual Studio.

 Tenga en cuenta la siguiente imagen de Visual Studio, que contiene varias ventanas de herramientas:

 ![Captura de pantalla](../../extensibility/internals/media/t1gui.png "T1gui")

 Algunas de las ventanas de herramientas están acopladas juntas en un solo panel que muestra la ventana de herramientas del explorador de soluciones y oculta las otras ventanas de herramientas, pero hace que estén disponibles al hacer clic en las pestañas. La imagen muestran dos ventanas de herramientas, el **lista de errores** y **salida** ventana, acoplada juntas en un único panel.

 También se muestra es el panel de documento principal, que muestra varias ventanas del editor. Aunque las ventanas de herramientas normalmente tienen una sola instancia (por ejemplo, puede abrir sólo uno **el Explorador de soluciones**), ventanas del editor pueden tener varias instancias, cada uno de los cuales se usa para editar un documento independiente, pero todos ellos están acoplados en el mismo panel. La imagen muestra un panel de documento que tiene dos ventanas del editor, una ventana del Diseñador de formulario. Todas las ventanas en el panel de documento están disponibles al hacer clic en las fichas, pero la ventana del editor que contiene el archivo EditorPane.cs está visible y activo.

 Al extender Visual Studio, puede crear la herramienta interactúan de ventanas que permiten a los usuarios de Visual Studio con la extensión. También puede crear sus propios editores que permiten a los usuarios de Visual Studio editar documentos. Dado que los editores y ventanas de herramientas se integrarán en Visual Studio, no es necesario programarlos para acoplar o aparezcan correctamente en una pestaña. Están registrados correctamente en Visual Studio, automáticamente tienen las características típicas de las ventanas de herramientas y ventanas de documento en Visual Studio. Para obtener más información, consulte [ampliación y personalización de Windows de herramienta](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Ventanas de documento
 Una ventana de documento es una ventana secundaria con marcos de una ventana de interfaz de múltiples documentos (MDI). Ventanas de documento normalmente se utilizan para hospedar controles de edición, los editores de formulario (también conocido como diseñadores) o editores de texto, pero también pueden hospedar otros tipos funcionales. El **nuevo archivo** cuadro de diálogo incluye ejemplos de ventanas de documento que proporciona Visual Studio.

 Mayoría de los editores está relacionada con un lenguaje de programación o a un tipo de archivo, como páginas HTML, conjuntos de marcos, archivos de C++ o los archivos de encabezado. Al seleccionar una plantilla en el **nuevo archivo** cuadro de diálogo, un usuario crea dinámicamente una ventana de documento para el editor para el tipo de archivo que está asociado con la plantilla. También se crea una ventana de documento cuando un usuario abre un archivo existente.

 Ventanas de documento están restringidas al área de cliente MDI. Cada ventana de documento tiene una pestaña en la parte superior y orden de tabulación esté vinculado a otras ventanas que pueden estar abiertos en el área MDI. Haciendo clic en la pestaña de una ventana de documento, se muestra un menú contextual que incluye opciones para dividir el área MDI en varios de los grupos de pestañas horizontal o vertical. Dividir el área MDI permite que varios archivos de verse al mismo tiempo. Para obtener más información, consulte [documento Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editores
 El editor de Visual Studio permite personalizarlo y usarlo para su propio tipo de contenido por medio de Managed Extensibility Framework (MEF). En muchos casos no necesitará crear un VSPackage para ampliar el editor, aunque si van a incluir características desde el shell (por ejemplo, un comando de menú o una tecla de método abreviado), una extensión de MEF se puede combinar con un VSPackage.

 También puede crear un editor personalizado, por ejemplo si desea leer y escribir en una base de datos, o si desea usar un diseñador. También puede utilizar un editor externo, como el Bloc de notas o WordPad de Microsoft. Para obtener más información, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Servicios de lenguaje
 Si desea que el editor de Visual Studio para admitir las nuevas palabras clave de programación o incluso un nuevo lenguaje de programación, cree un servicio de lenguaje. Cada servicio de lenguaje puede implementar ciertas características del editor por completo, parcial o no admitirlo. Según cómo esté configurada, el servicio de lenguaje puede proporcionar resaltado de sintaxis, coincidencia de llaves, compatibilidad con IntelliSense y otras características en el editor.

 En el corazón de un servicio de lenguaje son un analizador y un escáner. Escáner (o lexer) divide un archivo de código fuente en los elementos que se conocen como tokens y un analizador establece las relaciones entre esos tokens. Cuando se crea un servicio de lenguaje, debe implementar el analizador y el analizador para que Visual Studio pueda comprender los tokens y la gramática del lenguaje. Puede crear servicios de lenguaje administrado o no administrado. Para obtener más información, consulte [extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Proyectos

En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar y compilar el código fuente y otros recursos. Proyectos permiten organizar, compilar, depurar y distribuir el código fuente, las referencias a servicios Web y bases de datos y otros recursos. Paquetes VSPackage pueden extender el sistema de proyectos de Visual Studio proporcionando herramientas personalizadas, subtipos de proyecto y tipos de proyecto.

Los proyectos también se pueden recopilar juntos un *solución*, que es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. Información de estado y de proyecto que pertenece a la solución se almacena en dos archivos de solución, basado en texto [archivo de solución (.sln)](solution-dot-sln-file.md) y el archivo binario [opción (.suo) archivo de solución usuario](solution-user-options-dot-suo-file.md). Estos archivos son similares a los archivos de grupo (. vbg) que se usaron en versiones anteriores de Visual Basic y el área de trabajo (.dsw) y los archivos de opciones (.opt) del usuario que se usaron en versiones anteriores de C++.

Para obtener más información, consulte [proyectos](../../extensibility/internals/projects.md) y [soluciones](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Plantillas de proyecto y elemento
 Visual Studio incluye plantillas de proyecto predefinidas y las plantillas de elemento de proyecto. Puede también hacer sus propias plantillas o adquirir las plantillas de la Comunidad y, a continuación, integrarlos en Visual Studio. El [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) es el lugar indicado para las plantillas y las extensiones.

 Las plantillas contienen la estructura del proyecto y los archivos básicos que son necesarios para compilar un determinado tipo de clase, biblioteca, control o aplicación. Cuando desea desarrollar software que se parece a una de las plantillas, cree un proyecto que se basa en la plantilla y, a continuación, modifique los archivos en el proyecto.

> [!NOTE]
> Esta arquitectura de la plantilla no es compatible con [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos.

 Para obtener más información, consulte [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Propiedades y opciones
 El **propiedades** ventana muestra las propiedades de uno o varios elementos seleccionados: [Extender propiedades](../../extensibility/internals/extending-properties.md) páginas de opciones contienen conjuntos de opciones que pertenecen a un componente determinado, como un lenguaje de programación o un paquete VSPackage: [Opciones y páginas de opciones](../../extensibility/internals/options-and-options-pages.md). Valores son características generalmente relacionadas con la interfaz de usuario que pueden importarse y exportarse: [Compatibilidad con la configuración de usuario](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio Services
 Un servicio proporciona un conjunto específico de interfaces de componentes consumir. Visual Studio proporciona un conjunto de servicios que puede usarse por los componentes, incluidas las extensiones. Por ejemplo, servicios de Visual Studio permiten ventanas de herramientas para mostrarse u oculto de forma dinámica, habilitar el acceso a la Ayuda, barra de estado o eventos de interfaz de usuario. El editor de Visual Studio también proporciona servicios que pueden importarse por extensiones de editor. Para obtener más información, consulte [Using y proporcionar servicios](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>instantáneas
 El depurador es la interfaz de usuario para los componentes de depuración específicos del idioma. Si ha creado un nuevo servicio de lenguaje, deberá crear un motor de depuración específicos para enlazar al depurador. Para obtener más información, consulte [extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Control de código fuente
 Para obtener información acerca de cómo implementar un complemento de control de código fuente o VSPackage, consulte [Control de código fuente](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Asistentes
 Puede crear un asistente junto con un nuevo tipo de proyecto, por lo que el asistente le ayuda a los usuarios tomen las decisiones correctas cuando crea un nuevo proyecto de ese tipo. Para obtener más información, consulte [asistentes](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Herramientas personalizadas
 Herramientas personalizadas le permiten asociar una herramienta con un elemento en un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Para obtener más información, consulte [Custom Tools](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilidades VSSDK
 VSSDK incluye un conjunto de utilidades que puede que necesite para trabajar con distintos aspectos de VSPackages. Para obtener más información, consulte [utilidades VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Uso de Windows Installer
 En algunos casos es posible que deba usar el instalador de Windows en lugar de con el instalador de VSIX: por ejemplo, es posible que deba escribir en el registro. Para obtener información sobre cómo usar Windows Installer con las extensiones, vea [Installing VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visor de Ayuda
 Puede integrar su ayuda y las páginas de F1 en el Visor de ayuda. Para obtener más información, consulte [SDK del Visor de Ayuda de Microsoft](../../extensibility/internals/microsoft-help-viewer-sdk.md).