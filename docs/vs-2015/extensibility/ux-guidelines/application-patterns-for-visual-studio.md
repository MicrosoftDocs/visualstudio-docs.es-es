---
title: Patrones de aplicación
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af70b191e4b9061d08acdc7f76ade843dee41709
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114133"
---
# <a name="application-patterns-for-visual-studio"></a>Patrones de aplicaciones para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interacciones de ventanas

### <a name="overview"></a>Información general
 Los dos tipos de ventana principales que se usan en Visual Studio son los editores de documentos y las ventanas de herramientas. Poco frecuente, pero posible, son cuadros de diálogo no modales de gran tamaño. Aunque son todos los modelos no modales en el Shell, sus patrones son fundamentalmente diferentes. En este tema se trata la diferencia entre las ventanas de documento, las ventanas de herramientas y los cuadros de diálogo no modales. Los patrones de diálogo modales se describen en los [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparar patrones de uso de ventanas
 Las **ventanas de documento** casi siempre se muestran en el cuadro de documento. Esto proporciona al editor de documentos una "etapa central" para organizar las ventanas de herramientas adicionales.

 Una **ventana de herramientas** se muestra normalmente como una ventana independiente y más pequeña, que puede ser visible, oculta o oculta automáticamente, contraída en el borde del IDE. Sin embargo, a veces se presentan en el área del documento, desactivando la propiedad **ventana/acoplar** de la ventana. Esto da como resultado una mayor independencia, pero también una decisión de diseño común: al intentar integrar en Visual Studio, debe decidir si la característica debe mostrar una ventana de herramientas o una ventana de documento.

 Los **cuadros de diálogo no modales** no se recomiendan en Visual Studio. En gran medida, son, por definición, las ventanas de herramientas flotantes y deben implementarse como tal. Los cuadros de diálogo no modales se permiten en los casos en los que el tamaño de una ventana de herramientas normal acoplada al lado del shell sería demasiado limitado. También se permiten en los casos en que el usuario podría pasar el cuadro de diálogo a un monitor secundario.

 Piense detenidamente en qué tipo de contenedor necesita. En la tabla siguiente se muestran las consideraciones comunes del patrón de uso para el diseño de la interfaz de usuario.

||Ventana de documento|Ventana de herramientas|Cuadro de diálogo no modal|
|-|---------------------|-----------------|---------------------|
|**Position**|Siempre se coloca dentro del área del documento y no se acopla alrededor de los bordes del IDE. Se puede "extraer" para que flote por separado del shell principal.|Normalmente acoplado con tabulación alrededor de los bordes del IDE, pero se puede personalizar para que sea flotante, oculto automáticamente (desanclado) o acoplado dentro del área del documento.|Ventana flotante grande independiente del IDE.|
|**Modelo de confirmación**|*Confirmación diferida*<br /><br /> Para guardar los datos en un documento, el usuario debe emitir el comando archivo/guardar, guardar como o guardar todo. Una ventana de documento tiene el concepto de los datos que contiene y se confirma en uno de los comandos de guardar. Al cerrar una ventana de documento, todo el contenido se guarda en el disco o se pierde.|*Confirmación inmediata*<br /><br /> No hay ningún modelo de guardado. En el caso de las ventanas de herramientas de inspector que ayudan a editar un archivo, el archivo debe estar abierto en el editor o diseñador activo y el editor o el diseñador posee el guardado.|*Confirmación retrasada o inmediata*<br /><br /> A menudo, un cuadro de diálogo no modal de gran tamaño requiere una acción para confirmar los cambios y permite una operación de "cancelación", que revierte los cambios realizados en la sesión de diálogo.  Esto diferencia un cuadro de diálogo no modal de una ventana de herramientas en que las ventanas de herramientas siempre tienen un modelo de confirmación inmediato.|
|**Visibilidad**|*Abrir/crear (archivo) y cerrar*<br /><br /> Para abrir una ventana de documento, se puede abrir un documento existente o usar una plantilla para crear un nuevo documento. No hay ningún comando "abrir \<specific editor> ".|*Ocultar y mostrar*<br /><br /> Las ventanas de herramientas de una sola instancia se pueden ocultar o mostrar. El contenido y los Estados de la ventana de herramientas se conservarán en la vista u ocultarse. Las ventanas de herramientas de varias instancias se pueden cerrar y ocultar. Cuando se cierra una ventana de herramientas de varias instancias, se descartan el contenido y el estado de la ventana de herramientas.|*Iniciado desde un comando*<br /><br /> Los cuadros de diálogo se inician desde un comando basado en tareas.|
|**Stance**|*Instancias múltiples*<br /><br /> Varios editores pueden abrirse al mismo tiempo y editar distintos archivos, mientras que algunos editores también permiten que el mismo archivo se abra en más de un editor (mediante la **ventana > comando nueva ventana** ).<br /><br /> Un solo editor puede estar editando uno o varios archivos al mismo tiempo (diseñador de proyectos).|*Una o varias instancias*<br /><br /> Cambio de contenido para reflejar el contexto (como en el explorador de propiedades) o el foco o el contexto de la extracción en otras ventanas (Lista de tareas, Explorador de soluciones).<br /><br /> Las ventanas de herramientas de instancia única y de varias instancias deben estar asociadas a la ventana de documento activa, a menos que haya una buena razón para no hacerlo.|*Instancia única*|
|**Ejemplos**|**Editores de texto**, como el editor de código<br /><br /> **Superficies de diseño**, como un diseñador de formularios o una superficie de modelado<br /><br /> **Diseños de controles similares a los cuadros de diálogo**, como el diseñador de manifiestos|El **Explorador de soluciones** proporciona una solución y proyectos incluidos en la solución.<br /><br /> El **Explorador de servidores** proporciona una vista jerárquica de los servidores y las conexiones de datos que el usuario elige abrir en la ventana de. Al abrir un objeto de la jerarquía de la base de datos, como una consulta, se abre una ventana de documento y se permite al usuario editar la consulta.<br /><br /> El **Explorador de propiedades** muestra las propiedades del objeto seleccionado en una ventana de documento o en otra ventana de herramientas. Las propiedades se presentan en una vista de cuadrícula jerárquica o en controles complejos de cuadro de diálogo y permiten que el usuario establezca los valores de esas propiedades.||

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Ventanas de herramientas

### <a name="overview"></a>Información general
 Las ventanas de herramientas admiten el trabajo del usuario que se produce en las ventanas de documento. Se pueden usar para mostrar una jerarquía que representa un objeto raíz fundamental que Visual Studio proporciona y puede manipular.

 Al considerar una nueva ventana de herramientas en el IDE, los autores deben:

- Use las ventanas de herramientas existentes apropiadas para tareas y no cree nuevas con una funcionalidad similar. Las nuevas ventanas de herramientas solo deben crearse si ofrecen una "herramienta" o funcionalidad significativamente diferente que no se puede integrar en una ventana similar, o si se convierte una ventana existente en un centro de dinamización.

- Use una barra de comandos estándar, si es necesario, en la parte superior de la ventana de herramientas.

- Sea coherente con los patrones ya presentes en otras ventanas de herramientas para la presentación de controles y la navegación mediante el teclado.

- Sea coherente con la presentación de controles en otras ventanas de herramientas.

- Las ventanas de herramientas específicas del documento deben ser visibles automáticamente cuando sea posible para que aparezcan solo cuando se activa el documento primario.

- Asegúrese de que el contenido de la ventana sea navegable por el teclado (compatibilidad con las teclas de dirección).

#### <a name="tool-window-states"></a>Estados de la ventana de herramientas
 Las ventanas de herramientas de Visual Studio tienen distintos Estados, algunos de los cuales están activados por el usuario (como la característica de ocultación automática). Otros Estados, como visible automáticamente, permiten que las ventanas de herramientas aparezcan en el contexto correcto y se ocultan cuando no se necesitan. Hay cinco Estados de ventanas de herramientas en total.

- Las ventanas de herramientas **acopladas o ancladas** se pueden adjuntar a cualquiera de los cuatro lados del área del documento. El icono de alfiler aparece en la barra de título de la ventana de herramientas. La ventana de herramientas se puede acoplar horizontal o verticalmente a lo largo del borde del shell y otras ventanas de herramientas, y también puede estar vinculada por tabulaciones.

- Las ventanas **de herramientas ocultas automáticamente** se desanclan. La ventana puede deslizarse fuera de la vista, saliendo de una tabulación (con el nombre de la ventana de herramientas y su icono) en el borde del área del documento. La ventana de herramientas se desliza fuera cuando un usuario mantiene el puntero sobre la pestaña.

- Las ventanas de herramientas **visibles** automáticamente aparecen automáticamente cuando se inicia otra parte de la interfaz de usuario, como un editor, o recibe el foco.

- Las ventanas de herramientas **flotantes** se desplazan fuera del IDE. Esto resulta útil para las configuraciones de varios monitores.

- Las ventanas de herramientas de **documentos con pestañas** se pueden acoplar en el área de documento. Esto resulta útil para las ventanas de herramientas de gran tamaño, como el Examinador de objetos, que necesitan más espacio real que el acoplamiento a los bordes del marco.

  ![Estados de la ventana de herramientas en Visual Studio](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702-01_ToolWindowStates")

  **Estados de la ventana de herramientas en Visual Studio**

#### <a name="single-instance-and-multi-instance"></a>Instancia única y de varias instancias
 Las ventanas de herramientas son de instancia única o de varias instancias. Es posible que algunas ventanas de herramientas de una sola instancia estén asociadas a la ventana de documento activa, mientras que las ventanas de herramientas de varias instancias podrían no hacerlo. Las ventanas de herramientas de varias instancias responden al comando Window/new window creando una nueva instancia de la ventana. En la imagen siguiente se muestra una ventana de herramientas que habilita el comando nueva ventana cuando una instancia de la ventana está activa:

 ![Habilitar comandos de ventana de herramientas de Visual Studio](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")

 **Ventana de herramientas que habilita el comando ' nueva ventana ' cuando una instancia de la ventana está activa**

 Las ventanas de herramientas de una sola instancia se pueden ocultar o mostrar, mientras que las ventanas de herramientas de varias instancias se pueden cerrar y ocultar. Todas las ventanas de herramientas se pueden acoplar, vincular por pestañas, flotar o establecer como una ventana secundaria de la interfaz de múltiples documentos (MDI) (similar a una ventana de documento). Todas las ventanas de herramientas deben responder a los comandos de administración de ventanas correspondientes en el menú ventana:

 ![Comandos de administración de la ventana de Visual Studio](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702-03_WindowManagementControls")

 **Comandos de administración de ventanas en el menú ventana de Visual Studio**

#### <a name="document-specific-tool-windows"></a>Ventanas de herramientas específicas del documento
 Algunas ventanas de herramientas están diseñadas para cambiar en función de un tipo determinado de documento. Estas actualizaciones de Windows se actualizan continuamente para reflejar la funcionalidad aplicable a la ventana de documento activa en el IDE.

 Ejemplos de ventanas de herramientas cuyo contenido cambia para reflejar el editor seleccionado son el cuadro de herramientas y el esquema del documento. Estas ventanas muestran una marca de agua cuando un editor tiene el foco que no ofrece contexto a la ventana.

#### <a name="navigable-list-tool-windows"></a>Ventanas de herramientas de lista navegable
 Algunas ventanas de herramientas muestran una lista de elementos navegables con los que el usuario puede interactuar. En este tipo de ventana, siempre debería haber comentarios para el elemento actual de la lista, incluso si la ventana está inactiva. La lista debe responder a los comandos **GoToNextLocation** y **GoToPrevLocation** cambiando también el elemento seleccionado actualmente en la ventana

 Ejemplos de ventanas de herramientas de lista navegables son los Explorador de soluciones y la ventana Resultados de la búsqueda.

### <a name="tool-window-types"></a>Tipos de ventanas de herramientas

#### <a name="common-tool-windows-and-their-functions"></a>Ventanas de herramientas comunes y sus funciones

|Tipo|Ventana de herramientas|Función|
|----------|-----------------|--------------|
|**Hierarchy**|Explorador de soluciones|Árbol jerárquico que muestra una lista de los documentos contenidos en proyectos, archivos varios y elementos de la solución. La presentación de los elementos dentro de los proyectos se define mediante el paquete que posee el tipo de proyecto (por ejemplo, tipos basados en referencia, basados en directorios o en modo mixto).|
|**Hierarchy**|Vista de clases|Árbol jerárquico de las clases y varios elementos del espacio de trabajo de documentos, independientemente de los propios archivos.|
|**Hierarchy**|Explorador de servidores|Árbol jerárquico que muestra todos los servidores y las conexiones de datos de la solución.|
|**Hierarchy**|Esquema del documento|Estructura jerárquica del documento activo.|
|**Grid**|Propiedades|Una cuadrícula que muestra una lista de propiedades para el objeto seleccionado, junto con los selectores de valor para editar esas propiedades.|
|**Grid**|Lista de tareas|Una cuadrícula que permite al usuario crear, editar o eliminar tareas y comentarios.|
|**Contenido**|Ayuda|Una ventana que permite a los usuarios tener acceso a varios métodos de obtención de ayuda, desde "¿cómo?" vídeos en foros de MSDN.|
|**Contenido**|Ayuda dinámica|Ventana de herramientas que muestra vínculos a temas de ayuda aplicables a la selección actual.|
|**Contenido**|Examinador de objetos|Un FRAMESET de dos columnas con una lista de componentes de objeto jerárquico en el panel izquierdo y las propiedades y los métodos del objeto en la columna derecha.|
|**Diálogo**|Buscar, búsqueda avanzada|Cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos de la solución.|
|**Otros**|Cuadro de herramientas|La ventana de herramientas que se usa para almacenar los elementos que se colocarán en las superficies de diseño, lo que proporciona un código de arrastre coherente para todos los diseñadores.|
|**Otros**|Página de inicio|El portal del usuario a Visual Studio, con acceso a las fuentes de noticias para desarrolladores, la ayuda de Visual Studio y los proyectos recientes. Los usuarios también pueden crear páginas de inicio personalizadas mediante la copia del archivo StartPage. Xaml desde el directorio de archivos de programa de Visual Studio "Common7\IDE\StartPages\" en la carpeta StartPages del directorio de documentos de Visual Studio y, a continuación, editar el código XAML manualmente o abrirlo en Visual Studio o en otro editor de código.|
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Autos||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Inmediato||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Resultados|La ventana de salida se puede usar siempre que se tenga el estado o los eventos de texto que se van a declarar.|
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Memory||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Puntos de interrupción||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|En ejecución||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Documentos||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Pila de llamadas||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Locals||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Relojería||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Desensamblado||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Registros||
|**Depurador:** grupo de ventanas específico para la depuración de tareas y actividades de supervisión|Subprocesos||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Convenciones del editor de documentos

### <a name="document-interactions"></a>Interacciones de documentos
 El "documento bien" es el espacio más grande dentro del IDE y es donde el usuario ha centrado su atención con el fin de completar sus tareas, asistida por ventanas de herramientas adicionales. Los editores de documentos representan las unidades fundamentales de trabajo que el usuario abre y guarda en Visual Studio. Conservan una gran sensación de selección ligada a Explorador de soluciones u otras ventanas de jerarquía activas. El usuario debe poder apuntar a una de esas ventanas de jerarquía y saber dónde se encuentra el documento y su relación con la solución, el proyecto u otro objeto raíz proporcionado por un paquete de Visual Studio.

 La edición de documentos requiere una experiencia de usuario coherente. Para que el usuario pueda centrarse en la tarea a mano en lugar de en la administración de ventanas y buscar comandos, seleccione una estrategia de vista de documento que se adapte mejor a las tareas de usuario para editar ese tipo de documento.

#### <a name="common-interactions-for-the-document-well"></a>Interacciones comunes para el cuadro de documento

- Mantenga un modelo de interacción coherente en las experiencias comunes de **archivo nuevo** y **abierto** .

- Actualice la funcionalidad relacionada en ventanas y menús relacionados cuando se abra la ventana de documento.

- Los comandos de menú se integran correctamente en los menús comunes, como los menús **Editar**, **formato**y **Ver** . Si hay disponible una cantidad considerable de comandos especializados, se puede crear un nuevo menú que solo está visible cuando el documento tiene el foco.

- Una barra de herramientas incrustada se puede colocar en la parte superior del editor. Es preferible tener una barra de herramientas independiente que aparezca fuera del editor.

- Mantenga siempre una selección en el Explorador de soluciones o en una ventana de jerarquía activa similar.

- Al hacer doble clic en un documento en el Explorador de soluciones debe realizar la misma acción que **Open**.

- Si se puede usar más de un editor en un tipo de documento, el usuario debe poder invalidar o restablecer la acción predeterminada en un tipo de documento determinado mediante el cuadro de diálogo **abrir con** haciendo clic con el botón secundario en el archivo y seleccionando **abrir con** en el menú contextual.

- No cree un asistente en un cuadro de documento.

### <a name="user-expectations-for-specific-document-types"></a>Expectativas del usuario para tipos de documentos específicos
 Hay varios tipos básicos diferentes de editores de documentos y cada uno tiene un conjunto de interacciones que son coherentes con otras del mismo tipo.

- **Editor basado en texto: editor de** código, archivos de registro

- **Superficie de diseño:** Diseñador de formularios de WPF, Windows Forms

- **Editor de estilo de cuadro de diálogo:** Diseñador de manifiestos, propiedades del proyecto

- **Diseñador de modelos:** diseñador de flujo de trabajo, codemap, diagrama de arquitectura, progresión

  También hay varios tipos que no son de editor que usan el cuadro de documento. Aunque no editan los propios documentos, deben seguir las interacciones estándar de las ventanas de documento.

- **Informes:** Informe de IntelliTrace, informe de Hyper-V, informe del generador de perfiles

- **Panel:** Concentrador de diagnósticos

#### <a name="text-based-editors"></a>Editores basados en texto

- El documento participa en el modelo de pestañas de vista previa, lo que permite obtener una vista previa del documento sin abrirlo.

- La estructura del documento se puede representar dentro de una ventana de herramientas complementaria, como un esquema del documento.

- IntelliSense (si es necesario) se comportará de forma coherente con otros editores de código.

- Los elementos emergentes o la interfaz de usuario de asistencia siguen estilos y patrones similares para la interfaz de usuario similar existente, como codelens.

- Los mensajes relacionados con el estado del documento se presentarán en un control de barra de información en la parte superior del documento o en la barra de estado.

- El usuario debe poder personalizar el aspecto de las fuentes y los colores mediante una página de **herramientas > opciones** , ya sea la página fuentes y colores compartidos o una específica del editor.

#### <a name="design-surfaces"></a>Superficies de diseño

- Un diseñador vacío debe tener una marca de agua en la superficie que indique cómo comenzar.

- Los mecanismos de cambio de vista seguirán los patrones existentes, como hacer doble clic para abrir un editor de código o pestañas dentro de la ventana de documento, lo que permite la interacción con ambos paneles.

- La adición de elementos a la superficie de diseño debe realizarse a través del cuadro de herramientas, a menos que se requiera una ventana de herramientas muy específica.

- Los elementos de la superficie seguirán un modelo de selección coherente.

- Las barras de herramientas incrustadas contienen comandos específicos del documento, no comandos comunes, como **Guardar**.

#### <a name="dialog-style-editors"></a>Editores de estilo de cuadro de diálogo

- El diseño del control debe seguir las convenciones normales de diseño de diálogo.

- Las pestañas del editor no deben coincidir con la apariencia de las pestañas del documento, deben coincidir con uno de los dos estilos de tabulación interiores permitidos.

- Los usuarios deben poder interactuar con los controles usando solo el teclado; ya sea mediante la activación del editor y la tabulación a través de los controles o mediante teclas de acceso estándar.

- El diseñador debe utilizar Common Save Model. No se deben colocar botones de guardar o de confirmación generales en la superficie, aunque otros botones pueden ser adecuados.

#### <a name="model-designers"></a>Diseñadores de modelos

- Un diseñador vacío debe tener una marca de agua en la superficie que indique cómo comenzar.

- La adición de elementos a la superficie de diseño debe realizarse a través del cuadro de herramientas.

- Los elementos de la superficie seguirán un modelo de selección coherente.

- Las barras de herramientas incrustadas contienen comandos específicos del documento, no comandos comunes, como **Guardar**.

- Puede aparecer una leyenda en la superficie, ya sea indicativa o una marca de agua.

- El usuario debe poder personalizar el aspecto de las fuentes y los colores mediante el uso de una página **herramientas > opciones** , ya sea la página fuentes y colores compartidos o una específica del editor.

#### <a name="reports"></a>Informes

- Los informes suelen ser meramente informativos y no participan en el modelo de almacenamiento. Sin embargo, pueden incluir interacción como vínculos a otras secciones o información relevante que se expandan y contraigan.

- La mayoría de los comandos de la superficie deben ser hipervínculos, no botones.

- El diseño debe incluir un encabezado y seguir las instrucciones estándar de diseño de informes.

#### <a name="dashboards"></a>Paneles

- Los paneles no tienen un modelo de interacción, pero sirven como medio para ofrecer una variedad de otras herramientas.

- No participan en el modelo de almacenamiento.

- Los usuarios deben poder interactuar con los controles usando solo el teclado, ya sea activando el editor y haciendo tabulador a través de los controles o usando teclas de acceso estándar.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Cuadros

### <a name="introduction"></a>Introducción
 Los cuadros de diálogo de Visual Studio normalmente deben admitir una unidad discreta del trabajo del usuario y, a continuación, descartarse.

 Si ha determinado que necesita un cuadro de diálogo, tiene tres opciones, en orden de preferencia:

1. Integre sus características en uno de los cuadros de diálogo compartidos de Visual Studio.

2. Cree su propio cuadro de diálogo usando un patrón que se encuentra en un cuadro de diálogo similar existente.

3. Cree un nuevo cuadro de diálogo, siguiendo las instrucciones de interacción y diseño.

   En este tema se describe cómo elegir el patrón de cuadro de diálogo correcto en los flujos de trabajo de Visual Studio y las convenciones comunes para el diseño de cuadros de diálogo.

### <a name="themes"></a>Temas
 Los cuadros de diálogo de Visual Studio siguen uno de dos estilos básicos:

#### <a name="standard-unthemed"></a>Estándar (desvinculado)
 La mayoría de los cuadros de diálogo son los cuadros de diálogo estándar de la utilidad y deben desinstalarse. No vuelva a crear plantillas para los controles comunes o intente crear controles o botones "modernos" estilizados. Los controles y el aspecto de Chrome siguen las [directrices de interacción del escritorio de Windows estándar para los cuadros de diálogo](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx).

#### <a name="themed"></a>Temáticas
 Los cuadros de diálogo "firma" de especialidad pueden estar en el tema. Los cuadros de diálogo con los que tienen un aspecto distinto, que también tiene algunos patrones de interacción especiales asociados con el estilo. Tema el cuadro de diálogo solo si cumple estos requisitos:

- El cuadro de diálogo es una experiencia común que se verá y usará con frecuencia o con muchos usuarios (por ejemplo, el cuadro de diálogo **nuevo proyecto** ).

- El cuadro de diálogo contiene elementos destacados de la marca de producto (por ejemplo, el cuadro de diálogo Configuración de la **cuenta** ).

- El cuadro de diálogo aparece como una parte integral de un flujo más grande que incluye otros cuadros de diálogo de los que se han agregado (por ejemplo, el cuadro de diálogo **Agregar servicio conectado** ).

- El cuadro de diálogo es una parte importante de una experiencia que juega un papel estratégico en la promoción o diferenciación de una versión del producto.

  Al crear un cuadro de diálogo de la organización, use los colores de entorno adecuados y siga los patrones de diseño e interacción correctos. (Consulte [diseño de Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>Diseño del cuadro de diálogo
 Los cuadros de diálogo bien diseñados tienen en cuenta los siguientes elementos:

- Tarea de usuario admitida

- Estilo de texto del cuadro de diálogo, lenguaje y terminología

- Elección del control y convenciones de la interfaz de usuario

- Especificación de diseño visual y alineación de controles

- Acceso mediante el teclado

#### <a name="content-organization"></a>Organización de contenido
 Tenga en cuenta las diferencias entre estos tipos básicos de cuadros de diálogo:

- Los [cuadros de diálogo simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentan controles en una sola ventana modal. La presentación puede incluir variaciones de patrones de control complejos, incluido un selector de campos o una barra de iconos.

- Los [cuadros de diálogo en capas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se usan para sacar el máximo partido de la pantalla cuando un solo elemento de la interfaz de usuario consta de varios grupos de controles. Las agrupaciones del cuadro de diálogo se "superponen" a través de los controles de ficha, los controles de lista de navegación o los botones para que el usuario pueda elegir qué agrupación ver en un momento dado.

- Los [asistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) son útiles para dirigir al usuario a través de una secuencia lógica de pasos hacia la finalización de una tarea. En los paneles secuenciales se ofrecen una serie de opciones que, a veces, introducen flujos de trabajo diferentes ("ramas") en función de la elección realizada en el panel anterior.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Cuadros de diálogo simples
 Un cuadro de diálogo simple es una presentación de controles en una sola ventana modal. Esta presentación podría incluir variaciones de patrones de control complejos, como un selector de campos. Para los cuadros de diálogo sencillos, siga el diseño general estándar, así como cualquier diseño específico necesario para las agrupaciones de controles complejos.

 ![Cuadro de diálogo sencillo en Visual Studio](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704-01_CreateStrongNameKey")

 **Crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio.**

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Cuadros de diálogo en capas
 Los cuadros de diálogo en capas incluyen pestañas, paneles y árboles incrustados. Se usan para maximizar el estado real cuando hay varios grupos de controles ofrecidos en una sola parte de la interfaz de usuario. Las agrupaciones se superponen para que el usuario pueda elegir la agrupación que se va a ver al mismo tiempo.

 En el caso más sencillo, el mecanismo para cambiar entre agrupaciones es un control de ficha. Hay varias alternativas disponibles. Consulte priorización y disposición en capas para elegir el estilo más apropiado.

 El cuadro de diálogo **herramientas > opciones** es un ejemplo de un cuadro de diálogo en capas que usa un árbol incrustado:

 ![Cuadro de diálogo con capas en Visual Studio](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704-02_ToolsOptions")

 **Herramientas > opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio.**

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Asistentes
 Los asistentes son útiles para dirigir al usuario a través de una secuencia lógica de pasos en la finalización de una tarea. En los paneles secuenciales se ofrecen una serie de opciones y el usuario debe continuar cada paso antes de continuar con el siguiente. Una vez que haya suficientes valores predeterminados disponibles, se habilitará el botón **Finalizar** .

 Los asistentes modales se utilizan para tareas que:

- Contienen bifurcaciones, donde se ofrecen diferentes rutas de acceso en función de las opciones del usuario.

- Contienen dependencias entre pasos, donde los pasos posteriores dependen de la entrada del usuario en los pasos anteriores

- Son lo suficientemente complejos como para que se use la interfaz de usuario para explicar las opciones ofrecidas y los posibles resultados de cada paso.

- Son transaccionales, que requieren un conjunto de pasos para completarse en su totalidad antes de que se confirmen los cambios.

### <a name="common-conventions"></a>Convenciones comunes
 Para lograr un diseño y una funcionalidad óptimos con los cuadros de diálogo, siga estas convenciones sobre el tamaño, la posición, los estándares, la configuración y la alineación del control, el texto de la interfaz de usuario, las barras de título, los botones de control y las teclas de acceso.

 Para obtener instrucciones específicas del diseño, consulte [diseño de Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Size
 Los cuadros de diálogo deben ajustarse a una resolución de pantalla de 1024 x 768 como mínimo y el tamaño inicial del cuadro de diálogo no debe superar los 900x700 píxeles. Se puede cambiar el tamaño de los cuadros de diálogo, pero no es un requisito.

 Hay dos recomendaciones para los cuadros de diálogo de tamaño ajustable:

1. Que un tamaño mínimo es un definido para el cuadro de diálogo que se optimizará para el conjunto de controles sin recorte y se ajustará para adaptarse al crecimiento de la localización razonable.

2. Que el tamaño escalado por el usuario se mantiene de una sesión a una sesión. Por ejemplo, si el usuario escala un cuadro de diálogo al 150%, se mostrará un inicio posterior del cuadro de diálogo en el 150%.

#### <a name="position"></a>Posición
 Los cuadros de diálogo deben aparecer centrados en el IDE en el primer inicio. En el caso de los cuadros de diálogo que no pueden cambiarse de tamaño, no es necesario que se conserve la última posición del cuadro de diálogo, por lo que aparecerá centrado en los lanzamientos posteriores. En el caso de los cuadros de diálogo de tamaño ajustable, el tamaño debe conservarse en los lanzamientos posteriores. En el caso de los cuadros de diálogo de tamaño variable que son modales, no es necesario conservar la posición. Mostrarlos centrados en el IDE evita la posibilidad de que el cuadro de diálogo aparezca en una posición imprevisible o inutilizable cuando la configuración de pantalla del usuario ha cambiado. En el caso de los cuadros de diálogo no modales que se pueden cambiar de posición, se debe mantener la posición del usuario en los lanzamientos posteriores, ya que el cuadro de diálogo se puede usar con frecuencia como parte integral de un flujo de trabajo mayor.

 Cuando los diálogos deben generar otros cuadros de diálogo, el cuadro de diálogo superior debe estar en cascada hacia la derecha y hacia abajo desde el elemento primario para que sea obvio para el usuario que ha navegado a un nuevo lugar.

#### <a name="modality"></a>Modalidad
 Ser modal significa que los usuarios deben completar o cancelar el cuadro de diálogo antes de continuar. Como los cuadros de diálogo modales impiden que el usuario interactúe con otras partes del entorno, el flujo de tareas de la característica debe usarlos de la manera más moderada posible. Cuando se necesita una operación modal, Visual Studio tiene una serie de cuadros de diálogo compartidos en los que puede integrar las características. Si tiene que crear un nuevo cuadro de diálogo, siga el patrón de interacción de un cuadro de diálogo existente con una funcionalidad similar.

 Cuando los usuarios necesitan realizar dos actividades a la vez, como **Buscar** y **reemplazar** mientras escriben código nuevo, el cuadro de diálogo debe ser un modelo no modal para que el usuario pueda cambiar fácilmente entre ellos. En general, Visual Studio usa ventanas de herramientas para este tipo de tarea vinculada que admite el editor.

#### <a name="control-configuration"></a>Configuración del control
 Sea coherente con las configuraciones de control existentes que realizan lo mismo en Visual Studio.

#### <a name="title-bars"></a>Barras de título

- El texto de la barra de título debe reflejar el nombre del comando que lo inició.

- No se debe usar ningún icono en las barras de título de diálogo. En los casos en los que el sistema requiere uno, use el logotipo de Visual Studio.

- Los cuadros de diálogo no deben tener botones minimizar o maximizar.

- Los botones de ayuda de la barra de título están desusados. No las agregue a nuevos cuadros de diálogo. Cuando existan, deben iniciar un tema de ayuda que sea conceptualmente relevante para la tarea.

  ![Especificaciones de la barra de título para Visual Studio](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704-03_TitleBarSpecs")

  **Especificaciones de instrucciones para las barras de título de los cuadros de diálogo de Visual Studio.**

#### <a name="control-buttons"></a>Botones de control
 En **General,** / **Cancel** / los botones cancelar**ayuda** se deben organizar horizontalmente en la esquina inferior derecha del cuadro de diálogo. La pila vertical alternativa está permitida si un cuadro de diálogo tiene varios botones en la parte inferior del cuadro de diálogo que presentarían confusión visual con los botones de control.

 ![Controlar las configuraciones de botón en Visual Studio](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704-04_ControlButtonConfig")

 **Configuraciones aceptables para botones de control en los cuadros de diálogo de Visual Studio**

 El cuadro de diálogo debe incluir un botón de control predeterminado. Para determinar el mejor comando que se usará como valor predeterminado, elija entre las siguientes opciones (que aparecen en orden de prioridad):

- Elija el comando más seguro y más seguro como predeterminado. Esto significa elegir el comando con más probabilidad de evitar la pérdida de datos y evitar el acceso al sistema imprevisto.

- Si la pérdida de datos y la seguridad no son factores, elija el comando predeterminado en función de su comodidad. Si se incluye el comando más probable como predeterminado, se mejorará el flujo de trabajo del usuario cuando el cuadro de diálogo admita tareas repetitivas o frecuentes.

  Evite elegir una acción destructiva permanentemente para el comando predeterminado. Si hay un comando de este tipo, elija un comando más seguro como el predeterminado en su lugar.

#### <a name="access-keys"></a>Claves de acceso
 No use teclas de acceso para **OK** / **Cancelar**los botones de / **ayuda** . De forma predeterminada, estos botones se asignan a las teclas de método abreviado:

|Nombre del botón|Método abreviado de teclado|
|-----------------|-----------------------|
|Aceptar|Escriba|
|Cancelar|Esc|
|Ayuda|F1|

#### <a name="imagery"></a>Imágenes
 Use imágenes con moderación en los cuadros de diálogo. No utilice iconos grandes en los cuadros de diálogo simplemente para usar el espacio. Use imágenes solo si son una parte importante de transmitir el mensaje al usuario, como iconos de advertencia o animaciones de estado.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Establecimiento de prioridades y disposición en capas

#### <a name="prioritizing-your-ui"></a>Priorizar la interfaz de usuario
 Es posible que sea necesario poner determinados elementos de la interfaz de usuario en Forefront y colocar opciones y comportamientos más avanzados (incluidos los comandos ocultos) en los cuadros de diálogo. Incorpore la funcionalidad de uso común a la de Forefront haciendo espacio en él y haciéndolo visible de forma predeterminada en la interfaz de usuario con una etiqueta de texto cuando se muestre el cuadro de diálogo.

#### <a name="layering-your-ui"></a>Disposición en capas de la interfaz de usuario
 Si ha determinado que un cuadro de diálogo es necesario, pero la funcionalidad relacionada que desea presentar al usuario va más allá de lo que se puede mostrar en un cuadro de diálogo simple, debe poner en capas la interfaz de usuario. Los métodos de capas más comunes que Visual Studio usa son pestañas y vestíbulos o paneles. En algunos casos, las regiones que pueden expandirse y contraerse pueden ser adecuadas. La interfaz de usuario adaptable generalmente no se recomienda en Visual Studio.

 Existen ventajas y desventajas de los distintos métodos para la disposición en capas de la interfaz de usuario a través de controles de tipo pestaña. Revise la lista siguiente para asegurarse de que está eligiendo una técnica de distribución en capas adecuada para su situación.

##### <a name="tabbing"></a>Tabulación

|Mecanismo de cambio|Ventajas y uso adecuado|Desventajas y uso inadecuado|
|-------------------------|------------------------------------|-----------------------------------------|
|Control Tab|Agrupar lógicamente las páginas de cuadro de diálogo en conjuntos relacionados<br /><br /> Útil para menos de cinco (o el número de pestañas que caben en una fila en las páginas del cuadro de diálogo) de controles relacionados en el cuadro de diálogo<br /><br /> Las etiquetas de tabulación deben ser cortas: una o dos palabras que puedan identificar fácilmente el contenido<br /><br /> Estilo de cuadro de diálogo común del sistema<br /><br /> Ejemplo: **Explorador de archivos > propiedades de elemento**|Crear etiquetas cortas descriptivas puede ser difícil<br /><br /> Por lo general, no se escalan las cinco pestañas en un cuadro de diálogo<br /><br /> No es apropiado si tiene demasiadas pestañas para una fila; usar una técnica de capas alternativa<br /><br /> No extensible|
|Navegación de Sidebar|Dispositivo de conmutación simple que puede alojar más categorías que las pestañas<br /><br /> Lista plana de categorías (sin jerarquía)<br /><br /> Extensible<br /><br /> Ejemplo: **personalizar... > agregar comando**|No es un buen uso del espacio horizontal si hay menos de tres grupos<br /><br /> La tarea puede ser más adecuada para una lista desplegable|
|Tree (control)|Permite categorías ilimitadas<br /><br /> Permite agrupar y/o jerarquía de categorías<br /><br /> Extensible<br /><br /> Ejemplo: **herramientas > opciones**|Las jerarquías muy anidadas pueden provocar un desplazamiento horizontal excesivo<br /><br /> Visual Studio tiene una gran cantidad de vistas de árbol|
|Asistente|Contribuye a la finalización de las tareas mediante el paso de los pasos secuenciales basados en tareas. El asistente representa una tarea de alto nivel y los paneles individuales representan las subtareas necesarias para realizar la tarea global.<br /><br /> Resulta útil cuando la tarea cruza los límites de la interfaz de usuario, como cuando el usuario tendría que usar varios editores y ventanas de herramientas para completar la tarea.<br /><br /> Útil cuando la tarea requiere bifurcación<br /><br /> Resulta útil cuando la tarea contiene dependencias entre pasos<br /><br /> Resulta útil cuando se pueden presentar en un cuadro de diálogo varias tareas similares con una bifurcación de decisión para reducir el número de cuadros de diálogo similares diferentes.|No es apropiado para cualquier tarea que no requiera un flujo de trabajo secuencial<br /><br /> Los usuarios pueden saturarse y confundirse con un asistente con demasiados pasos<br /><br /> Los asistentes tienen una inmobiliaria de pantalla limitada de forma inherente|

##### <a name="hallways-or-dashboards"></a>Vestíbulos o paneles
 Los pasillos y los paneles son cuadros de diálogo o paneles que sirven como punto de partida para otros cuadros de diálogo y ventanas. El "vestíbulo" bien diseñado solo muestra inmediatamente las opciones, los comandos y la configuración más comunes, lo que permite al usuario realizar fácilmente tareas comunes. Al igual que un vestíbulo en el mundo real, proporciona entradas para tener acceso a los salones que hay detrás de ellos. en este caso, la interfaz de usuario menos común se recopila en "salones" (a menudo otros cuadros de diálogo) de la funcionalidad relacionada a la que se puede tener acceso desde el vestíbulo principal.

 Como alternativa, una interfaz de usuario que ofrece toda la funcionalidad disponible en una sola colección en lugar de refactorizar la funcionalidad menos común en ubicaciones independientes es simplemente un panel.

 ![Concepto de vestíbulo en Outlook](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704-08_Hallway")

 **Concepto de vestíbulo para exponer una interfaz de usuario adicional en Outlook**

##### <a name="adaptive-ui"></a>Interfaz de usuario adaptativa
 La visualización u ocultación de la interfaz de usuario en función del uso o de la experiencia de notificación automática de un usuario es otra manera de presentar la interfaz de usuario necesaria mientras se ocultan otras partes. Esto no se recomienda en Visual Studio, ya que los algoritmos para decidir cuándo Mostrar u ocultar la interfaz de usuario pueden ser complicados, y las reglas siempre serán erróneas para algún conjunto de casos.

## <a name="projects"></a><a name="BKMK_Projects"></a>Proyecto

### <a name="projects-in-the-solution-explorer"></a>Proyectos en el Explorador de soluciones
 La mayoría de los proyectos se clasifican como basados en referencias, basados en directorios o mixtos. Los tres tipos de proyectos se admiten simultáneamente en el Explorador de soluciones. La raíz de la experiencia del usuario en trabajar con proyectos tiene lugar dentro de esta ventana. Aunque los distintos nodos del proyecto son proyectos de tipo de referencia, de directorio o de modo mixto, hay un patrón de interacción común que se debe aplicar como punto de partida antes de que sea divergente a patrones de usuario específicos del proyecto.

 Los proyectos siempre deben:

- Permite agregar carpetas de proyecto para organizar el contenido del proyecto.

- Mantener un modelo coherente para la persistencia del proyecto

  Los proyectos también deben mantener modelos de interacción coherentes para:

- Quitar elementos de proyecto

- Guardar documentos

- Edición de propiedades de proyecto

- Edición del proyecto en una vista alternativa

- Operaciones de arrastrar y colocar

### <a name="drag-and-drop-interaction-model"></a>Modelo de interacción de arrastrar y colocar
 Normalmente, los proyectos se clasifican por sí mismos como basados en referencias (solo se pueden conservar las referencias a los elementos de proyecto en el almacenamiento), basado en directorios (solo se pueden conservar los elementos de proyecto almacenados físicamente dentro de la jerarquía de un proyecto) o mixto (puede conservar referencias o elementos físicos). El IDE aloja los tres tipos de proyectos simultáneamente en el **Explorador de soluciones**.

 Desde una perspectiva de arrastrar y colocar, deben aplicarse las siguientes características a cada tipo de proyecto en el **Explorador de soluciones**:

- **Proyecto basado en referencia:** El punto clave es que el proyecto está arrastrando alrededor de una referencia a un elemento en el almacenamiento. Cuando un proyecto basado en referencia actúa como origen de una operación de movimiento, solo debe quitar la referencia al elemento del proyecto. El elemento no se debe eliminar realmente del disco duro. Cuando un proyecto basado en referencia actúa como destino de una operación de movimiento (o copia), debe agregar una referencia al elemento de origen original sin hacer una copia privada del elemento.

- **Proyecto basado en directorio:** Desde un punto de vista de arrastrar y colocar, el proyecto está arrastrando alrededor del elemento físico en lugar de una referencia. Cuando un proyecto basado en directorio actúa como origen de una operación de movimiento, debe terminar de eliminar el elemento físico del disco duro y quitarlo del proyecto. Cuando un proyecto basado en directorio actúa como destino de una operación de movimiento (o copia), debe hacer una copia del elemento de origen en su ubicación de destino.

- **Proyecto de destino mixto:** Desde un punto de vista de arrastrar y colocar, el comportamiento de este tipo de proyecto se basa en la naturaleza del elemento que se está arrastrando (ya sea una referencia a un elemento en el almacenamiento o el propio elemento). El comportamiento correcto para las referencias y los elementos físicos se ha descrito anteriormente.

  Si solo había un tipo de proyecto en el **Explorador de soluciones**, las operaciones de arrastrar y colocar serían sencillas. Dado que cada sistema del proyecto tiene la capacidad de definir su propio comportamiento de arrastrar y colocar, deben seguirse ciertas instrucciones (basadas en el comportamiento de arrastrar y colocar del explorador de Windows) para garantizar una experiencia de usuario predecible:

- Una operación de arrastrar sin modificar en el **Explorador de soluciones** (cuando no se mantienen presionadas las teclas Ctrl ni Mayús) debe producir una operación de movimiento.

- La operación de arrastrar y colocar también debe producir una operación de movimiento.

- Ctrl: la operación de arrastrar debe producir una operación de copia.

- Los sistemas de proyectos mixtos y basados en referencia admiten la noción de agregar un vínculo (o referencia) al elemento de origen. Cuando estos proyectos son el destino de una operación de arrastrar y colocar (cuando se mantiene presionada la tecla **Ctrl + Mayús** ), se debe producir una referencia al elemento que se va a agregar al proyecto.

  No todas las operaciones de arrastrar y colocar son sensatas en combinaciones de proyectos basados en referencia, basados en directorios y mixtos. En concreto, es problemático fingir permitir una operación de movimiento entre un proyecto de origen basado en directorio y un proyecto de destino basado en referencia porque el proyecto basado en directorio de origen tendrá que eliminar el elemento de origen una vez completada la operación de movimiento. El proyecto basado en referencia de destino terminaría con una referencia a un elemento eliminado.

  También es engañoso para permitir una operación de copia entre estos tipos de proyectos porque el proyecto basado en referencia de destino no debe hacer una copia independiente del elemento de origen. Del mismo modo, no se debe permitir que Ctrl + Mayús arrastre hasta un proyecto de destino basado en directorio porque un proyecto basado en directorio no puede conservar las referencias. En los casos en los que no se admite la operación de arrastrar y colocar, el IDE no debe permitir la eliminación y mostrar al usuario el cursor no colocado (que se muestra en la siguiente tabla de puntero).

  Para implementar correctamente el comportamiento de arrastrar y colocar, el proyecto de origen de la función de arrastrar debe comunicar su naturaleza (por ejemplo, ¿se trata de una referencia o basada en directorios?) al proyecto de destino. Esta información se indica mediante el formato del portapapeles que ofrece el origen. Como origen de una operación de arrastrar (o de copia del portapapeles), un proyecto debe ofrecer **CF_VSREFPROJECTITEM**S o **CF_VSSTGPROJECTITEMS** respectivamente, en función de si el proyecto está basado en referencias o en el directorio. Ambos formatos tienen el mismo contenido de datos, que es similar al formato de Windows **CF_HDROP** , salvo que las listas de cadenas, en lugar de los nombres de archivo, son una lista terminada en**null** de cadenas **Projref** (devuelta por **IVsSolution:: GetProjrefOfItem** o **:: GetProjrefOfProject** según corresponda).

  Como destino de una operación Drop (o pegar el portapapeles), un proyecto debe aceptar **CF_VSREFPROJECTITEMS** y **CF_VSSTGPROJECTITEMS**, aunque el control exacto de la operación de arrastrar y colocar varía en función de la naturaleza del proyecto de destino y del proyecto de origen. El proyecto de origen declara su naturaleza en función de si ofrece **CF_VSREFPROJECTITEMS** o **CF_VSSTGPROJECTITEMS**. El destino de la eliminación comprende su propia naturaleza y, por tanto, tiene suficiente información para tomar decisiones sobre si se debe realizar un movimiento, una copia o un vínculo. El usuario también modifica la operación de arrastrar y colocar que se debe realizar presionando las teclas Ctrl, Mayús o Ctrl y Mayús. Es importante que el destino de colocación indique correctamente qué operación se realizará de antemano en sus métodos **DragEnter** y **DragOver** . El **Explorador de soluciones** sabe automáticamente si el proyecto de origen y el proyecto de destino son el mismo proyecto.

  No se admite arrastrar elementos de proyecto entre instancias de Visual Studio (por ejemplo, de una instancia de devenv.exe a otra). El **Explorador de soluciones** también lo deshabilita directamente.

  El usuario siempre debe ser capaz de determinar el efecto de una operación de arrastrar y colocar seleccionando un elemento, arrastrándolo a la ubicación de destino y observando cuál de los siguientes punteros del mouse aparece antes de que se quite el elemento:

|Puntero|Get-Help|Descripción|
|-------------------|-------------|-----------------|
|![Icono de mouse "No colocar"](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706-01_MouseNoDrop")|No eliminar|No se puede quitar el elemento de la ubicación especificada.|
|![Icono de mouse "Copiar"](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706-02_MouseCopy")|Copiar|El elemento se copiará en la ubicación de destino.|
|![Icono de mouse "Mover"](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706-03_MouseMove")|Move|El elemento se mueve a la ubicación de destino.|
|![Icono de mouse "Agregar referencia"](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706-04_MouseAddRef")|Agregar referencia|Se agregará una referencia al elemento seleccionado en la ubicación de destino.|

#### <a name="reference-based-projects"></a>Proyectos basados en referencia
 En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como las operaciones de cortar, copiar y pegar) que deben realizarse en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino basados en referencia:

|Modificador|Operación|Elemento de origen: referencia/vínculo|Elemento de origen: elemento físico o sistema de archivos (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Sin modificador|Acción|Move|Vínculo|
|Sin modificador|Destino|Agrega una referencia al elemento original|Agrega una referencia al elemento original|
|Sin modificador|Source|Elimina la referencia al elemento original|Conserva el elemento original|
|Sin modificador|Resultado|**DROPEFFECT_MOVE** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_LINK** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Mayús + arrastrar|Acción|Move|No eliminar|
|Mayús + arrastrar|Destino|Agrega una referencia al elemento original|No eliminar|
|Mayús + arrastrar|Source|Elimina la referencia al elemento original|No eliminar|
|Mayús + arrastrar|Resultado|**DROPEFFECT_MOVE** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|No eliminar|
|Ctrl + arrastrar|Acción|Copiar|No eliminar|
|Ctrl + arrastrar|Destino|Agrega una referencia al elemento original|No eliminar|
|Ctrl + arrastrar|Source|Conserva la referencia al elemento original|No eliminar|
|Ctrl + arrastrar|Resultado|**DROPEFFECT_COPY** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|No eliminar|
|Ctrl + Mayús + arrastrar|Acción|Vínculo|Vínculo|
|Ctrl + Mayús + arrastrar|Destino|Agrega una referencia al elemento original|Agrega una referencia al elemento original|
|Ctrl + Mayús + arrastrar|Source|Conserva la referencia al elemento original|Conserva el elemento original|
|Ctrl + Mayús + arrastrar|Resultado|**DROPEFFECT_LINK** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_LINK** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Ctrl + Mayús + arrastrar|Nota|Igual que el comportamiento de arrastrar y colocar para los accesos directos en el explorador de Windows.||
|Cortar y pegar|Acción|Move|Vínculo|
|Cortar y pegar|Destino|Agrega una referencia al elemento original|Agrega una referencia al elemento original|
|Cortar y pegar|Source|Conserva la referencia al elemento original|Conserva el elemento original|
|Cortar y pegar|Resultado|El elemento permanece en la ubicación original en el almacenamiento|El elemento permanece en la ubicación original en el almacenamiento|
|Copiar y pegar|Acción|Copiar|Vínculo|
|Copiar y pegar|Source|Agrega una referencia al elemento original|Agrega una referencia al elemento original|
|Copiar y pegar|Resultado|Conserva la referencia al elemento original|Conserva el elemento original|
|Copiar y pegar|Acción|El elemento permanece en la ubicación original en el almacenamiento|El elemento permanece en la ubicación original en el almacenamiento|

#### <a name="directory-based-projects"></a>Proyectos basados en directorios
 En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como las operaciones de cortar, copiar y pegar) que deben realizarse en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino basados en directorios:

|Modificador|Operación|Elemento de origen: referencia/vínculo|Elemento de origen: elemento físico o sistema de archivos (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Sin modificador|Acción|Move|Move|
|Sin modificador|Destino|Copia el elemento en la ubicación de destino|Copia el elemento en la ubicación de destino|
|Sin modificador|Source|Elimina la referencia al elemento original|Elimina la referencia al elemento original|
|Sin modificador|Resultado|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Mayús + arrastrar|Acción|Move|Move|
|Mayús + arrastrar|Destino|Copia el elemento en la ubicación de destino|Copia el elemento en la ubicación de destino|
|Mayús + arrastrar|Source|Elimina la referencia al elemento original|Elimina un elemento de la ubicación original|
|Mayús + arrastrar|Resultado|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Ctrl + arrastrar|Acción|Copiar|Copiar|
|Ctrl + arrastrar|Destino|Copia el elemento en la ubicación de destino|Copia el elemento en la ubicación de destino|
|Ctrl + arrastrar|Source|Conserva la referencia al elemento original|Conserva la referencia al elemento original|
|Ctrl + arrastrar|Resultado|**DROPEFFECT_ copia** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ copia** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Ctrl + Mayús + arrastrar||No eliminar|No eliminar|
|Cortar y pegar|Acción|Move|Move|
|Cortar y pegar|Destino|Copia el elemento en la ubicación de destino|Copia el elemento en la ubicación de destino|
|Cortar y pegar|Source|Elimina la referencia al elemento original|Elimina un elemento de la ubicación original|
|Cortar y pegar|Resultado|El elemento permanece en la ubicación original en el almacenamiento|El elemento se elimina de la ubicación original en el almacenamiento|
|Copiar y pegar|Acción|Copiar|Copiar|
|Copiar y pegar|Destino|Agrega una referencia al elemento original|Copia el elemento en la ubicación de destino|
|Copiar y pegar|Source|Conserva el elemento original|Conserva el elemento original|
|Copiar y pegar|Resultado|El elemento permanece en la ubicación original en el almacenamiento|El elemento permanece en la ubicación original ins Storage|

#### <a name="mixed-target-projects"></a>Proyectos de destino mixto
 En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como las operaciones de cortar, copiar y pegar) que deben realizarse en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino mixto:

|Modificador|Operación|Elemento de origen: referencia/vínculo|Elemento de origen: elemento físico o sistema de archivos (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Sin modificador|Acción|Move|Move|
|Sin modificador|Destino|Agrega una referencia al elemento original|Copia el elemento en la ubicación de destino|
|Sin modificador|Source|Elimina la referencia al elemento original|Elimina la referencia al elemento original|
|Sin modificador|Resultado|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento se elimina de la ubicación original en el almacenamiento|
|Mayús + arrastrar|Acción|Move|Move|
|Mayús + arrastrar|Destino|Agrega una referencia al elemento original|Copia el elemento en la ubicación de destino|
|Mayús + arrastrar|Source|Elimina la referencia al elemento original|Elimina un elemento de la ubicación original|
|Mayús + arrastrar|Resultado|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ movimiento** se devuelve como acción de **::D ROP** y el elemento se elimina de la ubicación original en el almacenamiento|
|Ctrl + arrastrar|Acción|Copiar|Copiar|
|Ctrl + arrastrar|Destino|Agrega una referencia al elemento original|Copia el elemento en la ubicación de destino|
|Ctrl + arrastrar|Source|Conserva la referencia al elemento original|Conserva el elemento original|
|Ctrl + arrastrar|Resultado|**DROPEFFECT_ copia** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ copia** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Ctrl + Mayús + arrastrar|Acción|Vínculo|Vínculo|
|Ctrl + Mayús + arrastrar|Destino|Agrega una referencia al elemento original|Agrega una referencia al elemento de origen original.|
|Ctrl + Mayús + arrastrar|Source|Conserva la referencia al elemento original|Conserva el elemento original|
|Ctrl + Mayús + arrastrar|Resultado|**DROPEFFECT_ vínculo** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|**DROPEFFECT_ vínculo** se devuelve como acción de **::D ROP** y el elemento permanece en la ubicación original en el almacenamiento|
|Cortar y pegar|Acción|Move|Move|
|Cortar y pegar|Destino|Copia el elemento en la ubicación de destino|Copia el elemento en la ubicación de destino|
|Cortar y pegar|Source|Elimina la referencia al elemento original|Elimina un elemento de la ubicación original|
|Cortar y pegar|Resultado|El elemento permanece en la ubicación original en el almacenamiento|El elemento se elimina de la ubicación original en el almacenamiento|
|Copiar y pegar|Acción|Copiar|Copiar|
|Copiar y pegar|Destino|Agrega una referencia al elemento original|Copia el elemento en la ubicación de destino|
|Copiar y pegar|Source|Conserva el elemento original|Conserva el elemento original|
|Copiar y pegar|Resultado|El elemento permanece en la ubicación original en el almacenamiento|El elemento permanece en la ubicación original en el almacenamiento|

 Estos detalles se deben tener en cuenta al implementar el arrastre en el **Explorador de soluciones**:

- Diseño para escenarios de selección múltiple.

- Los nombres de archivo (ruta de acceso completa) deben ser únicos en el proyecto de destino o no se debe permitir la eliminación.

- Los nombres de carpeta deben ser únicos (sin distinción de mayúsculas y minúsculas) en el nivel en el que se van a quitar.

- Existen diferencias de comportamiento entre los archivos que están abiertos o cerrados en el momento de la arrastre (no se menciona en los escenarios anteriores).

- Los archivos de nivel superior se comportan de manera ligeramente diferente que los archivos de las carpetas.

  Otro problema que hay que tener en cuenta es cómo controlar las operaciones de movimiento en los elementos que tienen diseñadores o editores abiertos. El comportamiento esperado es el siguiente (esto se aplica a todos los tipos de proyecto):

1. Si el editor o el diseñador abiertos no tienen cambios sin guardar, la ventana Editor/Diseñador debe cerrarse de forma silenciosa.

2. Si el editor o el diseñador abiertos tienen cambios sin guardar, el origen del arrastre debe esperar a que se produzca la colocación y, a continuación, pedir al usuario que guarde los cambios no confirmados en los documentos abiertos antes de cerrar la ventana con un mensaje similar al siguiente:

   ```
   ==========================================================
        One or more open documents have unsaved changes.
   Do you want to save uncommitted changes before proceeding?
                     [Yes]  [No]  [Cancel]
   ==========================================================
   ```

   Esto ofrece al usuario la oportunidad de guardar el trabajo en curso antes de que el destino realice sus copias. Se ha agregado un nuevo método **IVsHierarchyDropDataSource2:: OnBeforeDropNotify** para habilitar este control.

   Después, el destino copiará el estado del elemento tal como está en el almacenamiento (sin incluir los cambios no guardados en el editor si el usuario eligió **no**). Una vez que el destino ha completado su copia (en **IVsHierarchyDropDataSource::D ROP**), el origen tiene la oportunidad de completar la parte de eliminación de la operación de movimiento (en **IVsHierarchyDropDataSource:: OnDropNotify**).

   Los editores con cambios sin guardar deben dejarse abiertos. En el caso de los documentos con cambios sin guardar, esto significa que se realizará la copia de la operación de movimiento, pero se anulará la parte de la eliminación. En un escenario de selección múltiple cuando el usuario elige **no**, los documentos con cambios no guardados no se deben cerrar ni quitar, pero los cambios que no se hayan guardado deberían cerrarse y quitarse.
