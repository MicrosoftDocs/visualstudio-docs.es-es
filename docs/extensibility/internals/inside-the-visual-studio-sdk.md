---
title: Dentro del SDK de Visual Studio | Microsoft Docs
description: Obtenga información sobre las extensiones del SDK de Visual Studio, incluida la arquitectura, los componentes, los servicios, los esquemas y las utilidades de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e11ee862f43ead3605d8e07dc159e18da13413b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074709"
---
# <a name="inside-the-visual-studio-sdk"></a>Dentro de Visual Studio SDK

En esta sección se proporciona información detallada sobre las extensiones de Visual Studio, incluida la arquitectura de Visual Studio, componentes, servicios, esquemas, utilidades y similares.

## <a name="extensibility-architecture"></a>Arquitectura de extensibilidad
 En la ilustración siguiente se muestra la arquitectura de extensibilidad de Visual Studio. Los VSPackages proporcionan funcionalidad de la aplicación, que se comparte en el IDE como servicios. El IDE estándar también ofrece una amplia gama de servicios, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , que proporcionan acceso a la funcionalidad de ventanas del IDE.

 ![Gráfico de arquitectura de entorno](../../extensibility/internals/media/environment.gif "Environment") Vista generalizada de la arquitectura de Visual Studio

## <a name="vspackages"></a>VSPackages
 Los VSPackages son módulos de software que conforman y amplían Visual Studio con elementos de interfaz de usuario, servicios, proyectos, editores y diseñadores. Los VSPackages son la unidad arquitectónica central de Visual Studio. Para obtener más información, consulte [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio Shell proporciona funcionalidad básica y admite la comunicación cruzada entre sus componentes VSPackages y extensiones de MEF. Para obtener más información, vea [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Directrices de la experiencia de usuario
 Si tiene previsto diseñar nuevas características para Visual Studio, eche un vistazo a estas instrucciones de diseño y sugerencias de facilidad de uso: instrucciones para la [experiencia del usuario de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Comandos
 Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo.

 Al extender Visual Studio, puede crear comandos y registrarlos con Visual Studio Shell. Puede especificar cómo aparecerán estos comandos en el IDE, por ejemplo, en un menú o una barra de herramientas. Normalmente aparece un comando personalizado en el menú **herramientas** y un comando para mostrar una ventana de herramientas aparecerá en el submenú **otras ventanas** del menú **Ver** .

 Al crear un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o está habilitado, le permite modificar su texto y garantiza que el comando responde correctamente cuando se activa. En la mayoría de los casos, el IDE controla los comandos mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Los comandos de Visual Studio se controlan empezando por el contexto de comandos más interno, según la selección local, y continuando hasta el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts.

 Para obtener más información, vea [comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menús y barras de herramientas
 Los menús y las barras de herramientas proporcionan a los usuarios una manera de invocar comandos. Los menús son filas o columnas de comandos que normalmente se muestran como elementos de texto individuales en la parte superior de una ventana de herramientas. Los submenús son menús secundarios que aparecen cuando un usuario hace clic en los comandos que incluyen una flecha pequeña. Los menús contextuales aparecen cuando un usuario hace clic con el botón secundario en determinados elementos de la interfaz de usuario. Algunos nombres de menú comunes son **archivo**, **edición**, **vista** y **ventana**. Para obtener más información, vea [extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Las barras de herramientas son filas o columnas de botones y otros controles, como cuadros combinados, cuadros de lista y cuadros de texto. Los botones de barra de herramientas suelen tener imágenes de iconos, como un icono de carpeta para un comando **Abrir archivo** o una impresora para un comando **Imprimir** . Todos los elementos de la barra de herramientas están asociados a comandos. Al hacer clic en un botón de la barra de herramientas, se ejecuta el comando asociado. En el caso de un control desplegable, cada elemento de la lista desplegable está asociado a un comando diferente. Algunos controles de barra de herramientas, como un control divisor, son híbridos. Un lado del control es un botón de la barra de herramientas y el otro lado es una flecha hacia abajo que muestra varios comandos cuando se hace clic en él.

## <a name="tool-windows"></a>Ventanas de herramientas
 Las ventanas de herramientas se usan en el IDE para mostrar información. **Cuadro de herramientas**, **Explorador de soluciones**, la ventana **propiedades** y el **explorador Web** son ejemplos de ventanas de herramientas.

 Las ventanas de herramientas suelen ofrecer varios controles con los que el usuario puede interactuar. Por ejemplo, la ventana **propiedades** permite al usuario establecer las propiedades de los objetos que tienen un propósito determinado. La ventana **propiedades** se especializa en este sentido, pero también en general porque se puede usar en muchas situaciones diferentes. Del mismo modo, la ventana de **salida** es especializada porque proporciona una salida basada en texto, pero general porque muchos subsistemas de Visual Studio pueden usarla para proporcionar resultados al usuario de Visual Studio.

 Tenga en cuenta la siguiente imagen de Visual Studio, que contiene varias ventanas de herramientas:

 ![Captura de pantalla](../../extensibility/internals/media/t1gui.png "T1gui")

 Algunas de las ventanas de herramientas están acopladas juntas en un solo panel que muestra la ventana de herramientas de Explorador de soluciones y oculta las demás ventanas de herramientas, pero hace que estén disponibles haciendo clic en pestañas. La imagen muestra otras dos ventanas de herramientas, la **lista de errores** y la ventana de **salida** , acopladas juntas en un solo panel.

 También se muestra el panel principal del documento, que muestra varias ventanas del editor. Aunque las ventanas de herramientas normalmente solo tienen una instancia (por ejemplo, solo puede abrir una **Explorador de soluciones**), las ventanas del editor pueden tener varias instancias, cada una de las cuales se usa para editar un documento independiente, pero todas están acopladas en el mismo panel. La imagen muestra un panel de documento con dos ventanas de editor, una ventana del diseñador de formularios. Todas las ventanas del panel documento están disponibles haciendo clic en pestañas, pero la ventana del editor que contiene el archivo EditorPane. CS es visible y activa.

 Al extender Visual Studio, puede crear ventanas de herramientas que permitan a los usuarios de Visual Studio interactuar con la extensión. También puede crear sus propios editores que permitan a los usuarios de Visual Studio editar documentos. Dado que las ventanas de herramientas y los editores se integrarán en Visual Studio, no es necesario programarlos para acoplarlos o aparecer en una pestaña correctamente. Cuando se registran correctamente en Visual Studio, tendrán automáticamente las características típicas de las ventanas de herramientas y de documentos en Visual Studio. Para obtener más información, vea [extender y personalizar ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Ventanas de documento
 Una ventana de documento es una ventana secundaria con marcos de una ventana de interfaz de múltiples documentos (MDI). Las ventanas de documento se suelen usar para hospedar editores de texto, editores de formularios (también conocidos como diseñadores) o controles de edición, pero también pueden hospedar otros tipos funcionales. El cuadro de diálogo **nuevo archivo** incluye ejemplos de ventanas de documento que Visual Studio proporciona.

 La mayoría de los editores son específicos de un lenguaje de programación o de un tipo de archivo, como páginas HTML, conjuntos de Marcos, archivos de C++ o archivos de encabezado. Al seleccionar una plantilla en el cuadro de diálogo **nuevo archivo** , un usuario crea dinámicamente una ventana de documento para el editor para el tipo de archivo que está asociado a la plantilla. También se crea una ventana de documento cuando un usuario abre un archivo existente.

 Las ventanas de documento están restringidas al área cliente MDI. Cada ventana de documento tiene una pestaña en la parte superior y el orden de tabulación se vincula a otras ventanas que pueden estar abiertas en el área MDI. Al hacer clic con el botón secundario en la pestaña de una ventana de documento, se muestra un menú contextual que incluye opciones para dividir el área MDI en varios grupos de pestañas horizontales o verticales. La división del área MDI permite ver varios archivos al mismo tiempo. Para obtener más información, vea [ventanas de documento](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editores
 El editor de Visual Studio le permite personalizarlo y usarlo para su propio tipo de contenido mediante el Managed Extensibility Framework (MEF). En muchos casos, no será necesario crear un VSPackage para extender el editor, aunque si desea incluir características del shell (por ejemplo, un comando de menú o una tecla de método abreviado), puede combinar una extensión de MEF con un VSPackage.

 También puede crear un editor personalizado, por ejemplo, si desea leer y escribir en una base de datos, o si desea utilizar un diseñador. También puede usar un editor externo, como el Bloc de notas o Microsoft WordPad. Para obtener más información, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Servicios de lenguaje
 Si desea que el editor de Visual Studio admita nuevas palabras clave de programación o incluso un nuevo lenguaje de programación, cree un servicio de lenguaje. Cada servicio de lenguaje puede implementar ciertas características del editor de forma total o parcial. Dependiendo de cómo se configure, el servicio de lenguaje puede proporcionar resaltado de sintaxis, coincidencia de llaves, compatibilidad con IntelliSense y otras características en el editor.

 En el corazón de un servicio de lenguaje se encuentran un analizador y un escáner. Un escáner (o Lexer) divide un archivo de código fuente en elementos que se conocen como tokens, y un analizador establece las relaciones entre esos tokens. Al crear un servicio de lenguaje, debe implementar el analizador y el analizador para que Visual Studio pueda comprender los tokens y la gramática del idioma. Puede crear servicios de lenguaje administrados o no administrados. Para obtener más información, consulte [extensibilidad del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Proyectos

En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar y compilar el código fuente y otros recursos. Los proyectos permiten organizar, compilar, depurar e implementar código fuente, referencias a servicios web y bases de datos, y a otros recursos. Los VSPackages pueden extender el sistema de proyectos de Visual Studio proporcionando tipos de proyecto, subtipos de proyecto y herramientas personalizadas.

Los proyectos también se pueden recopilar juntos en una *solución*, que es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. La información del proyecto y el estado que pertenece a la solución se almacena en dos archivos de solución, el archivo de solución basado en texto [(. sln)](solution-dot-sln-file.md) y el archivo de la opción de usuario de la solución binaria [(. suo)](solution-user-options-dot-suo-file.md). Estos archivos son similares a los archivos de grupo (. VBG) que se usaron en versiones anteriores de Visual Basic y los archivos de área de trabajo (. DSW) y de opciones de usuario (. OPT) que se usaron en versiones anteriores de C++.

Para obtener más información, vea [proyectos](../../extensibility/internals/projects.md) y [soluciones](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Plantillas de proyecto y elemento
 Visual Studio incluye plantillas de proyecto predefinidas y plantillas de elementos de proyecto. También puede crear sus propias plantillas o adquirir plantillas de la comunidad y, a continuación, integrarlas en Visual Studio. La [Galería de código de MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) es el lugar para buscar plantillas y extensiones.

 Las plantillas contienen la estructura del proyecto y los archivos básicos necesarios para compilar un tipo determinado de aplicación, control, biblioteca o clase. Si desea desarrollar software similar a una de las plantillas, cree un proyecto basado en la plantilla y, a continuación, modifique los archivos de ese proyecto.

> [!NOTE]
> Esta arquitectura de plantilla no se admite para los [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos de.

 Para obtener más información, vea [agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Propiedades y opciones
 La ventana **propiedades** muestra las propiedades de uno o varios elementos seleccionados: la [extensión](../../extensibility/internals/extending-properties.md) de las páginas opciones de propiedades contiene conjuntos de opciones que pertenecen a un componente determinado, como un lenguaje de programación o un VSPackage: [Opciones y páginas de opciones](../../extensibility/internals/options-and-options-pages.md). La configuración suele ser características relacionadas con la interfaz de usuario que se pueden importar y exportar: compatibilidad con la [configuración de usuario](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Servicios de Visual Studio
 Un servicio proporciona un conjunto específico de interfaces para que los componentes los consuman. Visual Studio proporciona un conjunto de servicios que pueden usar los componentes de, incluidas las extensiones. Por ejemplo, los servicios de Visual Studio permiten mostrar u ocultar dinámicamente las ventanas de herramientas, habilitar el acceso a la ayuda, la barra de estado o los eventos de la interfaz de usuario. El editor de Visual Studio también proporciona servicios que se pueden importar mediante extensiones de editor. Para obtener más información, vea [usar y proporcionar servicios](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>instantáneas
 El depurador es la interfaz de usuario para los componentes de depuración específicos del lenguaje. Si ha creado un nuevo servicio de lenguaje, tendrá que crear un motor de depuración específico para enlazarlo al depurador. Para obtener más información, consulte [extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Control de código fuente
 Para obtener información sobre cómo implementar un complemento de control de código fuente o VSPackage, vea [control de código fuente](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Asistentes
 Puede crear un asistente junto con un nuevo tipo de proyecto para que el asistente pueda ayudar a los usuarios a tomar las decisiones adecuadas al crear un nuevo proyecto de ese tipo. Para obtener más información, consulte [asistentes](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Herramientas personalizadas
 Las herramientas personalizadas permiten asociar una herramienta a un elemento de un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Para obtener más información, vea [herramientas personalizadas](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilidades VSSDK
 VSSDK incluye un conjunto de utilidades que puede necesitar para trabajar con distintos aspectos de los VSPackages. Para obtener más información, consulte [utilidades de VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Usar Windows Installer
 En algunos casos, puede que tenga que usar el Windows Installer en lugar del instalador de VSIX: por ejemplo, puede que tenga que escribir en el registro. Para obtener información sobre el uso de Windows Installer con las extensiones, vea [instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visor de Ayuda
 Puede integrar su propia ayuda y páginas F1 en el visor de ayuda. Para obtener más información, vea [visor de ayuda de Microsoft SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
