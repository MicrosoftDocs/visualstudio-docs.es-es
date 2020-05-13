---
title: Dentro del SDK de Visual Studio . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707582"
---
# <a name="inside-the-visual-studio-sdk"></a>Dentro de Visual Studio SDK

En esta sección se proporciona información detallada acerca de las extensiones de Visual Studio, incluida la arquitectura de Visual Studio, componentes, servicios, esquemas, utilidades y similares.

## <a name="extensibility-architecture"></a>Arquitectura de extensibilidad
 En la siguiente ilustración se muestra la arquitectura de extensibilidad de Visual Studio. VSPackages proporcionan funcionalidad de aplicación, que se comparte entre el IDE como servicios. El IDE estándar también ofrece una amplia <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>gama de servicios, como , que proporcionan acceso a la funcionalidad de ventanas IDE.

 ![Gráfico de Arquitectura ambiental](../../extensibility/internals/media/environment.gif "Environment") Vista generalizada de la arquitectura de Visual Studio

## <a name="vspackages"></a>VSPackages
 Los VSPackages son módulos de software que conforman y amplían Visual Studio con elementos de interfaz de usuario, servicios, proyectos, editores y diseñadores. VSPackages son la unidad arquitectónica central de Visual Studio. Para obtener más información, consulte [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 El shell de Visual Studio proporciona funcionalidad básica y admite la comunicación cruzada entre sus componentes VSPackages y extensiones MEF. Para obtener más información, vea Shell de [Visual Studio](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Directrices de la experiencia de usuario
 Si planea diseñar nuevas características para Visual Studio, debe echar un vistazo a estas directrices para sugerencias de diseño y facilidad de uso: [Directrices](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)de experiencia del usuario de Visual Studio .

## <a name="commands"></a>Comandos
 Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo.

 Al ampliar Visual Studio, puede crear comandos y registrarlos con el shell de Visual Studio. Puede especificar cómo aparecerán estos comandos en el IDE, por ejemplo, en un menú o barra de herramientas. Normalmente aparece un comando personalizado en el menú **Herramientas** y un comando para mostrar una ventana de herramientas aparecería en el submenú **Otras ventanas** del menú **Ver.**

 Al crear un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina cuándo el comando está visible o habilitado, le permite modificar su texto y garantiza que el comando responde correctamente cuando se activa. En la mayoría de los casos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> el IDE controla los comandos mediante la interfaz. Los comandos de Visual Studio se controlan a partir del contexto de comandos más interno, basado en la selección local, y procediendo al contexto más externo, en función de la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts.

 Para obtener más información, consulte [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menús y barras de herramientas
 Los menús y las barras de herramientas proporcionan una manera para que los usuarios invoquen comandos. Los menús son filas o columnas de comandos que normalmente se muestran como elementos de texto individuales en la parte superior de una ventana de herramientas. Los submenús son menús secundarios que aparecen cuando un usuario hace clic en comandos que incluyen una flecha pequeña. Los menús contextuales aparecen cuando un usuario hace clic con el botón derecho en determinados elementos de la interfaz de usuario. Algunos nombres de menú comunes son **Archivo**, **Editar**, **Ver**y **Ventana**. Para obtener más información, consulte Ampliación de [menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Las barras de herramientas son filas o columnas de botones y otros controles, como cuadros combinados, cuadros de lista y cuadros de texto. Los botones de la barra de herramientas suelen tener imágenes de icono, como un icono de carpeta para un comando **Abrir archivo** o una impresora para un comando **Imprimir.** Todos los elementos de la barra de herramientas están asociados con comandos. Al hacer clic en un botón de la barra de herramientas, se ejecuta su comando asociado. En el caso de un control desplegable, cada elemento de la lista desplegable está asociado a un comando diferente. Algunos controles de barra de herramientas, como un control divisor, son híbridos. Un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra varios comandos cuando se hace clic en él.

## <a name="tool-windows"></a>Ventanas de herramientas
 Las ventanas de herramientas se utilizan en el IDE para mostrar información. **Toolbox**, **Explorador de soluciones**, ventana **Propiedades** y **Explorador web** son ejemplos de ventanas de herramientas.

 Las ventanas de herramientas suelen ofrecer varios controles con los que el usuario puede interactuar. Por ejemplo, la ventana **Propiedades** permite al usuario establecer propiedades de objetos que sirven para un propósito determinado. La ventana **Propiedades** está especializada en este sentido, pero también general porque se puede utilizar en muchas situaciones diferentes. De forma similar, **la** salida ventana está especializada porque proporciona salida basada en texto, pero general porque muchos subsistemas en Visual Studio pueden usarlo para proporcionar salida al usuario de Visual Studio.

 Considere la siguiente imagen de Visual Studio, que contiene varias ventanas de herramientas:

 ![Captura de pantalla](../../extensibility/internals/media/t1gui.png "T1gui")

 Algunas de las ventanas de herramientas se acoplan juntas en un único panel que muestra la ventana de herramientas del Explorador de soluciones y oculta las otras ventanas de herramientas, pero las pone a disposición haciendo clic en las pestañas. La imagen muestra otras dos ventanas de herramientas, la **ventana Lista** de errores y **Salida,** acopladas en un solo panel.

 También se muestra el panel principal del documento, que muestra varias ventanas del editor. Aunque las ventanas de herramientas suelen tener una sola instancia (por ejemplo, solo puede abrir un **Explorador**de soluciones), las ventanas del editor pueden tener varias instancias, cada una de las cuales se utiliza para editar un documento independiente, pero todas ellas acopladas en el mismo panel. La imagen muestra un panel de documento que tiene dos ventanas del editor, una ventana del diseñador de formularios. Todas las ventanas del panel de documentos están disponibles haciendo clic en las pestañas, pero la ventana del editor que contiene EditorPane.cs archivo está visible y activa.

 Al ampliar Visual Studio, puede crear ventanas de herramientas que permiten a los usuarios de Visual Studio interactuar con la extensión. También puede crear sus propios editores que permiten a los usuarios de Visual Studio editar documentos. Dado que las ventanas de herramientas y los editores se integrarán en Visual Studio, no es necesario programarlos para acoplarlos o aparecer en una pestaña correctamente. Cuando se registran correctamente en Visual Studio, tendrán automáticamente las características típicas de las ventanas de herramientas y ventanas de documentos en Visual Studio. Para obtener más información, consulte [Ampliación y personalización](../../extensibility/extending-and-customizing-tool-windows.md)de las ventanas de herramientas .

## <a name="document-windows"></a>Ventanas de documento
 Una ventana de documento es una ventana secundaria enmarcada de una ventana de interfaz de varios documentos (MDI). Las ventanas de documento normalmente se usan para hospedar editores de texto, editores de formularios (también conocidos como diseñadores) o controles de edición, pero también pueden hospedar otros tipos funcionales. El cuadro de diálogo **Nuevo archivo** incluye ejemplos de ventanas de documento que proporciona Visual Studio.

 La mayoría de los editores son específicos de un lenguaje de programación o de un tipo de archivo, como páginas HTML, conjuntos de marcos, archivos C++ o archivos de encabezado. Al seleccionar una plantilla en el cuadro de diálogo **Nuevo archivo,** un usuario crea dinámicamente una ventana de documento para el editor para el tipo de archivo asociado a la plantilla. También se crea una ventana de documento cuando un usuario abre un archivo existente.

 Las ventanas de documento están restringidas al área de cliente MDI. Cada ventana del documento tiene una pestaña en la parte superior, y el orden de tabulación está vinculado a otras ventanas que pueden estar abiertas en el área MDI. Al hacer clic con el botón derecho en la pestaña de una ventana de documento, se muestra un menú contextual que incluye opciones para dividir el área MDI en varios grupos de fichas horizontales o verticales. La división del área MDI permite ver varios archivos al mismo tiempo. Para obtener más información, consulte [Document Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editores
 El editor de Visual Studio le permite personalizarlo y usarlo para su propio tipo de contenido mediante Managed Extensibility Framework (MEF). En muchos casos no necesitará crear un VSPackage para ampliar el editor, aunque si desea incluir características del shell (por ejemplo, un comando de menú o una tecla de método abreviado), puede combinar una extensión MEF con un VSPackage.

 También puede crear un editor personalizado, por ejemplo, si desea leer y escribir en una base de datos, o si desea utilizar un diseñador. También puede utilizar un editor externo como el Bloc de notas o Microsoft WordPad. Para obtener más información, consulte [Extensiones](../../extensibility/editor-and-language-service-extensions.md)de servicio de editor y lenguaje .

## <a name="language-services"></a>Servicios de idiomas
 Si desea que el editor de Visual Studio admita nuevas palabras clave de programación o incluso un nuevo lenguaje de programación, cree un servicio de lenguaje. Cada servicio de lenguaje puede implementar ciertas características del editor total, parcialmente o no en absoluto. Dependiendo de cómo se configure, el servicio de lenguaje puede proporcionar resaltado de sintaxis, coincidencia de llaves, compatibilidad con IntelliSense y otras características en el editor.

 En el corazón de un servicio de idiomas hay un analizador y un escáner. Un analizador (o lexer) divide un archivo de origen en elementos que se conocen como tokens y un analizador establece las relaciones entre esos tokens. Al crear un servicio de lenguaje, debe implementar el analizador y el analizador para que Visual Studio pueda comprender los tokens y la gramática del lenguaje. Puede crear servicios de lenguaje administrados o no administrados. Para obtener más información, consulte [Extensibilidad](../../extensibility/internals/legacy-language-service-extensibility.md)del servicio de lenguaje heredado .

## <a name="projects"></a>Proyectos

En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar y compilar el código fuente y otros recursos. Los proyectos le permiten organizar, compilar, depurar e implementar código fuente, referencias a servicios web y bases de datos y otros recursos. VSPackages puede extender el sistema de proyectos de Visual Studio proporcionando tipos de proyecto, subtipos de proyecto y herramientas personalizadas.

Los proyectos también se pueden reunir en una *solución,* que es una agrupación de uno o más proyectos que trabajan juntos para crear una aplicación. La información de proyecto y estado que pertenece a la solución se almacena en dos archivos de solución, el archivo de solución basada en texto [(.sln)](solution-dot-sln-file.md) y el archivo de opción de [usuario (.suo)](solution-user-options-dot-suo-file.md)de la solución binaria. Estos archivos son similares a los archivos de grupo (.vbg) que se usaban en versiones anteriores de Visual Basic y los archivos de área de trabajo (.dsw) y opciones de usuario (.opt) que se usaban en versiones anteriores de C++.

Para obtener más información, consulte [Proyectos](../../extensibility/internals/projects.md) y [soluciones](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Plantillas de proyecto y elemento
 Visual Studio incluye plantillas de proyecto predefinidas y plantillas de elementos de proyecto. También puede crear sus propias plantillas o adquirir plantillas de la comunidad y, a continuación, integrarlas en Visual Studio. [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) es el lugar a donde ir para plantillas y extensiones.

 Las plantillas contienen la estructura del proyecto y los archivos básicos necesarios para crear un tipo determinado de aplicación, control, biblioteca o clase. Cuando desee desarrollar software similar a una de las plantillas, cree un proyecto basado en la plantilla y, a continuación, modifique los archivos de ese proyecto.

> [!NOTE]
> Esta arquitectura de plantilla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no se admite para proyectos.

 Para obtener más información, vea Agregar plantillas de [proyecto y elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)de proyecto .

## <a name="properties-and-options"></a>Propiedades y opciones
 La ventana **Propiedades** muestra las propiedades de uno o varios elementos seleccionados: [extender](../../extensibility/internals/extending-properties.md) las páginas Opciones de propiedades contiene conjuntos de opciones que pertenecen a un componente determinado, como un lenguaje de programación o un VSPackage: [páginas de opciones y opciones](../../extensibility/internals/options-and-options-pages.md). La configuración suele ser características relacionadas con la interfaz de usuario que se pueden importar y exportar: [Compatibilidad con la configuración de usuario](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Servicios de Visual Studio
 Un servicio proporciona un conjunto específico de interfaces para que los componentes se consuman. Visual Studio proporciona un conjunto de servicios que pueden usar cualquier componente, incluidas las extensiones. Por ejemplo, los servicios de Visual Studio permiten que las ventanas de herramientas se muestren u oculten dinámicamente, habilitan el acceso a la Ayuda, la barra de estado o los eventos de la interfaz de usuario. El editor de Visual Studio también proporciona servicios que se pueden importar mediante extensiones de editor. Para obtener más información, consulte [Uso y suministro de servicios](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Depurador
 El depurador es la interfaz de usuario de los componentes de depuración específicos del idioma. Si ha creado un nuevo servicio de lenguaje, deberá crear un motor de depuración específico para enlazarlo al depurador. Para obtener más información, vea [Extensibilidad del depurador](../../extensibility/debugger/visual-studio-debugger-extensibility.md)de Visual Studio .

## <a name="source-control"></a>Control de código fuente
 Para obtener información acerca de cómo implementar un complemento de control de código fuente o VSPackage, vea [Control de código fuente](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Asistentes
 Puede crear un asistente junto con un nuevo tipo de proyecto, de modo que el asistente pueda ayudar a los usuarios a tomar las decisiones correctas cuando creen un nuevo proyecto de ese tipo. Para obtener más información, consulte [Asistentes](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Herramientas personalizadas
 Las herramientas personalizadas le permiten asociar una herramienta con un elemento de un proyecto y ejecutarla siempre que se guarde el archivo. Para obtener más información, consulte [Herramientas personalizadas](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilidades VSSDK
 El VSSDK incluye un conjunto de utilidades que puede necesitar para trabajar con diferentes aspectos de VSPackages. Para obtener más información, consulte [Utilidades VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Uso de Windows Installer
 En algunos casos, es posible que deba utilizar Windows Installer en lugar del instalador de VSIX: por ejemplo, es posible que deba escribir en el registro. Para obtener información sobre el uso de Windows Installer con las extensiones, vea [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visor de Ayuda
 Puede integrar sus propias páginas de ayuda y F1 en el Visor de ayuda. Para obtener más información, consulte SDK del Visor de Ayuda de [Microsoft](../../extensibility/internals/microsoft-help-viewer-sdk.md).
