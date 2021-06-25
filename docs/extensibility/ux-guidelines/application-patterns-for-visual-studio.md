---
title: Patrones de aplicación para Visual Studio | Microsoft Docs
description: Obtenga información sobre la diferencia entre las ventanas de documentos, las ventanas de herramientas y los cuadros de diálogo de modelado, incluidos los patrones de uso de ventanas para las nuevas características de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2726c7096bbf4606fbab2c32b01ffd197549e13c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899191"
---
# <a name="application-patterns-for-visual-studio"></a>Patrones de aplicaciones para Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interacciones de ventana

### <a name="overview"></a>Información general
Los dos tipos de ventana principales utilizados en Visual Studio son los editores de documentos y las ventanas de herramientas. Poco frecuentes, pero posibles, son diálogos de gran modelo. Aunque todos son modelados en el shell, sus patrones son fundamentalmente diferentes. En esta sección se trata la diferencia entre las ventanas de documentos, las ventanas de herramientas y los diálogos de modelado. Los patrones de diálogo modales se tratan en [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparación de patrones de uso de ventanas
**Las ventanas de** documento casi siempre se muestran dentro del documento. Esto proporciona al editor de documentos una "fase central" para organizar ventanas de herramientas complementarias.

Una **ventana de herramientas** suele mostrarse como una ventana independiente y más pequeña contraida en el borde del IDE. Puede ser visible, oculto o oculto automáticamente. Sin embargo, a veces las ventanas de herramientas se presentan dentro del documento desactivando la propiedad **Ventana/Acoplamiento** de la ventana. Esto da como resultado un mayor patrimonio, pero también una decisión de diseño común: al intentar integrar en Visual Studio, debe decidir si la característica debe mostrar una ventana de herramientas o una ventana de documento.

**No se recomiendan los diálogos** modelados en Visual Studio. La mayoría de los diálogos no modelo son, por definición, ventanas de herramientas flotantes y deben implementarse de esa manera. Los diálogos no modelo se permiten en casos en los que el tamaño de una ventana de herramientas normal acoplada al lado del shell sería demasiado limitador. También se permiten en casos en los que es probable que el usuario mueva el cuadro de diálogo a un monitor secundario.

Piense detenidamente en qué tipo de contenedor necesita. Las consideraciones de patrón de uso comunes para el diseño de la interfaz de usuario se encuentran en la tabla siguiente.

||Ventana Documento|Ventana de herramientas|Cuadro de diálogo modeless|
|-|---------------------|-----------------|---------------------|
| **Position** | Siempre se coloca dentro del documento y no se acopla alrededor de los bordes del IDE. Se puede "despegar" para que flota por separado del shell principal. | Por lo general, las pestañas se acoplan alrededor de los bordes del IDE, pero se pueden personalizar para que sean flotantes, ocultas automáticamente (desanclar) o acopladas dentro del área del documento.|Ventana flotante grande independiente del IDE. |
| **Modelo de confirmación** | *Confirmación retrasada*<br /><br /> Para guardar los datos en un documento, el usuario debe emitir los comandos Guardar archivo, Guardar **como** o **Guardar** todo. **&gt;** Una ventana de documento tiene el concepto de que los datos que contiene están "desatendrados" y, a continuación, se confirman en uno de los comandos de guardado. Al cerrar una ventana de documento, todo el contenido se guarda en el disco o se pierde. | *Confirmación inmediata*<br /><br /> No hay ningún modelo de guardado. En el caso de las ventanas de herramientas de inspector que ayudan a editar un archivo, el archivo debe estar abierto en el editor o diseñador activo, y el editor o diseñador es el propietario del archivo guardado. | *Confirmación diferido o inmediato*<br /><br /> A menudo, un cuadro de diálogo no modelo grande requiere una acción para confirmar los cambios y permite una operación "Cancelar", que revierte los cambios realizados dentro de la sesión del diálogo.  Esto diferencia un cuadro de diálogo no modelo de una ventana de herramientas en que las ventanas de herramientas siempre tienen un modelo de confirmación inmediata. |
| **Visibilidad** | *Abrir/Crear (archivo) y Cerrar*<br /><br /> La apertura de una ventana de documento se realiza abriendo un documento existente o usando una plantilla para crear un nuevo documento. No hay ningún comando \<specific editor> "Abrir". | *Ocultar y mostrar*<br /><br /> Las ventanas de herramientas de instancia única se pueden ocultar o mostrar. El contenido y los estados dentro de la ventana de herramientas persisten, ya sea en vista u ocultos. Las ventanas de herramientas de instancias múltiples se pueden cerrar y ocultar. Cuando se cierra una ventana de herramientas de varias instancias, se descarta el contenido y el estado dentro de la ventana de herramientas. | *Iniciado desde un comando*<br /><br /> Los diálogos se inician desde un comando basado en tareas. |
| **Instancias** | *Instancias múltiples*<br /><br /> Varios editores se pueden abrir al mismo tiempo y editar archivos diferentes, mientras que algunos editores también permiten que el mismo archivo esté abierto en más de un editor (mediante el comando Ventana nueva **&gt; ventana).**<br /><br /> Un único editor puede estar editando uno o varios archivos al mismo tiempo (Diseñador de proyectos). | *Instancia única o múltiple*<br /><br /> El contenido cambia para reflejar el contexto (como en el Explorador de propiedades) o inserta el foco o contexto en otras ventanas (Lista de tareas, Explorador de soluciones).<br /><br /> Las ventanas de herramientas de instancia única y de instancias múltiples deben asociarse a la ventana de documento activa, a menos que haya una razón atractiva para no hacerlo. | *Instancia única* |
| **Ejemplos** | **Editores de texto,** como el editor de código<br /><br /> **Superficies de diseño,** como un diseñador de formularios o una superficie de modelado<br /><br /> **Diseños de control similares a los diálogos,** como el Diseñador de manifiestos | El **Explorador de soluciones** proporciona una solución y proyectos incluidos en la solución.<br /><br /> El **Explorador de servidores** proporciona una vista jerárquica de los servidores y las conexiones de datos que el usuario elige abrir en la ventana. Al abrir un objeto desde la jerarquía de la base de datos, como una consulta, se abre una ventana de documento y se permite al usuario editar la consulta.<br /><br /> El **Explorador de propiedades** muestra las propiedades del objeto seleccionado en una ventana de documento u otra ventana de herramientas. Las propiedades se presentan en una vista de cuadrícula jerárquica o en controles complejos similares a diálogos y permiten al usuario establecer los valores de esas propiedades. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Ventanas de herramientas

### <a name="overview"></a>Información general
Las ventanas de herramientas admiten el trabajo del usuario que se produce en las ventanas de documentos. Se pueden usar para mostrar una jerarquía que representa un objeto raíz fundamental que Visual Studio proporciona y puede manipular.

Al considerar una nueva ventana de herramientas en el IDE, los autores deben:

- Use ventanas de herramientas existentes adecuadas para tareas y no cree otras nuevas con una funcionalidad similar. Solo se deben crear nuevas ventanas de herramientas si ofrecen una "herramienta" o funcionalidad significativamente diferente que no se puede integrar en una ventana similar, o si se convierte una ventana existente en un centro dinámico.

- Use una barra de comandos estándar, si es necesario, en la parte superior de la ventana de herramientas.

- Sea coherente con los patrones que ya están presentes en otras ventanas de herramientas para la presentación del control y la navegación con el teclado.

- Sea coherente con la presentación del control en otras ventanas de herramientas.

- Haga que las ventanas de herramientas específicas del documento sean visibles automáticamente cuando sea posible, de modo que solo aparezcan cuando se active el documento primario.

- Asegúrese de que el contenido de la ventana sea navegable mediante el teclado (teclas de dirección de soporte).

#### <a name="tool-window-states"></a>Estados de la ventana de herramientas
Visual Studio de herramientas tienen estados diferentes, algunos de los cuales están activados por el usuario (como la característica de ocultación automática). Otros estados, como el visible automáticamente, permiten que las ventanas de herramientas aparezcan en el contexto correcto y se oculte cuando no sea necesario. Hay cinco estados de ventana de herramientas en total.

- **Las ventanas de herramientas acopladas** o ancladas se pueden adjuntar a cualquiera de los cuatro lados del área del documento. El icono de chin emergente aparece en la barra de título de la ventana de herramientas. La ventana de herramientas se puede acoplar horizontal o verticalmente a lo largo del borde del shell y otras ventanas de herramientas, y también se puede vincular con tabulaciones.

- **Las ventanas de herramientas** ocultas automáticamente se desanclar. La ventana puede deslizarse fuera de la vista, dejando una pestaña (con el nombre de la ventana de herramientas y su icono) en el borde del área del documento. La ventana de herramientas se desvía cuando un usuario mantiene el puntero sobre la pestaña.

- **Las ventanas de herramientas visibles** automáticamente aparecen automáticamente cuando se inicia otra parte de la interfaz de usuario, como un editor, o bien se obtiene el foco.

- **Las ventanas** de herramientas flotantes mantienen el puntero fuera del IDE. Esto es útil para configuraciones de varios monitores.

- **Las ventanas de herramientas** de documentos con pestañas se pueden acoplar dentro del documento. Esto es útil para ventanas de herramientas de gran tamaño, como el Explorador de objetos, que necesitan más recursos que el acoplamiento a los bordes del marco.

![Estados de la ventana de herramientas en Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Estados de la ventana de herramientas en Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Instancia única y instancias múltiples
Las ventanas de herramientas son de instancia única o de instancias múltiples. Es posible que algunas ventanas de herramientas de instancia única se asocie a la ventana de documento activa, mientras que las ventanas de herramientas de varias instancias podrían no estar asociadas. Las ventanas de herramientas de varias instancias responden al **comando Ventana &gt; Nueva ventana** mediante la creación de una nueva instancia de la ventana. En la imagen siguiente se muestra una ventana de herramientas que habilita el comando Nueva ventana cuando una instancia de la ventana está activa:

![Ventana de herramientas que habilita el comando "Nueva ventana" cuando una instancia de la ventana está activa](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Ventana de herramientas que habilita el comando "Nueva ventana" cuando una instancia de la ventana está activa

Las ventanas de herramientas de instancia única se pueden ocultar o mostrar, mientras que las ventanas de herramientas de varias instancias se pueden cerrar y ocultar. Todas las ventanas de herramientas se pueden acoplar, vincular con tabulaciones, flotantes o establecerse como una ventana secundaria de interfaz Multiple-Document (MDI) (similar a una ventana de documento). Todas las ventanas de herramientas deben responder a los comandos de administración de ventanas adecuados en el menú Ventana:

![Comandos de administración de ventanas en el menú Visual Studio ventana](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandos de administración de ventanas en el menú Visual Studio ventana

#### <a name="document-specific-tool-windows"></a>Ventanas de herramientas específicas del documento
Algunas ventanas de herramientas están diseñadas para cambiar en función de un tipo determinado de documento. Estas ventanas se actualizan continuamente para reflejar la funcionalidad aplicable a la ventana de documento activa en el IDE.

Ejemplos de ventanas de herramientas cuyo contenido cambia para reflejar el editor seleccionado son el Cuadro de herramientas y el Esquema del documento. Estas ventanas muestran una marca de agua cuando un editor tiene el foco que no ofrece contexto a la ventana.

#### <a name="navigable-list-tool-windows"></a>Ventanas de herramientas de lista navegables
Algunas ventanas de herramientas muestran una lista de elementos navegables con los que el usuario puede interactuar. En este tipo de ventana, siempre debe haber comentarios sobre el elemento actual de la lista, incluso si la ventana está inactiva. La lista debe responder a los **comandos GoToNextLocation** y **GoToPrevLocation** cambiando también el elemento seleccionado actualmente en la ventana.

Algunos ejemplos de ventanas de herramientas de lista navegables son el Explorador de soluciones y la ventana Resultados de la búsqueda.

### <a name="tool-window-types"></a>Tipos de ventana de herramientas

#### <a name="common-tool-windows-and-their-functions"></a>Ventanas de herramientas comunes y sus funciones

**Ventanas de herramientas jerárquicas**

| Ventana de herramientas | Función |
| --- | --- |
| Explorador de soluciones | Árbol jerárquico que muestra una lista de documentos contenidos en proyectos, archivos varios y elementos de solución. La presentación de los elementos dentro de los proyectos se define mediante el paquete que posee el tipo de proyecto (por ejemplo, tipos basados en referencias, basados en directorios o en modo mixto). |
| Vista de clases | Árbol jerárquico de las clases y varios elementos del conjunto de trabajo de documentos, independientemente de los propios archivos. |
| Explorador de servidores | Árbol jerárquico que muestra todos los servidores y las conexiones de datos de la solución. |
| Esquema de documento | Estructura jerárquica del documento activo. |

**Ventanas de herramientas de cuadrícula**

| Ventana de herramientas | Función |
| --- | --- |
| Propiedades | Cuadrícula que muestra una lista de propiedades para el objeto seleccionado, junto con selectores de valores para editar esas propiedades. |
| Lista de tareas | Cuadrícula que permite al usuario crear, editar o eliminar tareas y comentarios. |

**Ventanas de herramientas de contenido**

| Ventana de herramientas | Función |
| --- | --- |
| Ayuda | Ventana que permite a los usuarios acceder a varios métodos para obtener ayuda, desde "¿Cómo puedo?" vídeos a foros de MSDN. |
| Ayuda dinámica | Ventana de herramientas que muestra vínculos a temas de ayuda aplicables a la selección actual. |
| Examinador de objetos | Conjunto de marcos de dos columnas con una lista de componentes de objeto jerárquicos en el panel izquierdo y las propiedades y métodos del objeto en la columna derecha. |

**Ventanas de herramientas de diálogo**

| Ventana de herramientas | Función |
| --- | --- |
| Buscar | Cuadro de diálogo que permite al usuario buscar, buscar y reemplazar en varios archivos de la solución. |
| Búsqueda avanzada | Cuadro de diálogo que permite al usuario buscar, buscar y reemplazar en varios archivos de la solución. |

**Otras ventanas de herramientas**

::: moniker range="vs-2017"

| Ventana de herramientas | Función |
| --- | --- |
| Cuadro de herramientas | Ventana de herramientas que se usa para almacenar elementos que se colocarán en superficies de diseño, lo que proporciona un origen de arrastre coherente para todos los diseñadores. |
| Página de inicio | El portal del usuario para Visual Studio, con acceso a fuentes de noticias para desarrolladores, Visual Studio ayuda y proyectos recientes. Los usuarios también pueden crear páginas de inicio personalizadas copiando el archivo StartPage.xaml desde el directorio de archivos de programa "Common7\IDE\StartPages Visual Studio en la carpeta StartPages del directorio Visual Studio documents y, a continuación, editando el XAML a mano o abriendo en Visual Studio u otro \" editor de código. |

::: moniker-end

::: moniker range=">=vs-2019"

| Ventana de herramientas | Función |
| --- | --- |
| Cuadro de herramientas | Ventana de herramientas que se usa para almacenar elementos que se colocarán en superficies de diseño, lo que proporciona un origen de arrastre coherente para todos los diseñadores. |

::: moniker-end

**Ventanas de herramientas del depurador**

| Ventana de herramientas | Función |
| --- | --- |
| Autos ||
| Inmediata ||
| Output | La ventana de salida se puede usar siempre que tenga eventos textuales o estado para declarar. |
| Memoria ||
| Puntos de interrupción ||
| En ejecución ||
| Documentos ||
| Pila de llamadas ||
| Locals ||
| Relojes ||
| Desensamblado ||
| Registros ||
| Subprocesos ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Convenciones del editor de documentos

### <a name="document-interactions"></a>Interacciones de documentos
El "documento correcto" es el espacio más grande dentro del IDE y es donde el usuario generalmente ha centrado su atención para completar sus tareas, asistidas por ventanas de herramientas complementarias. Los editores de documentos representan las unidades de trabajo fundamentales que el usuario abre y guarda en Visual Studio. Conservan una fuerte sensación de selección asociada a Explorador de soluciones u otras ventanas de jerarquía activas. El usuario debe poder apuntar a una de esas ventanas de jerarquía y saber dónde está contenido el documento y su relación con la solución, el proyecto u otro objeto raíz proporcionado por un paquete Visual Studio.

La edición de documentos requiere una experiencia de usuario coherente. Para permitir que el usuario se centre en la tarea en su mano en lugar de en la administración de ventanas y la búsqueda de comandos, seleccione una estrategia de vista de documento que se adapte mejor a las tareas del usuario para editar ese tipo de documento.

#### <a name="common-interactions-for-the-document-well"></a>Interacciones comunes para el documento

- Mantenga un modelo de interacción coherente en las **experiencias comunes De nuevo archivo** y **Abrir** archivo.

- Actualice la funcionalidad relacionada en ventanas y menús relacionados cuando se abra la ventana del documento.

- Los comandos de menú se integran correctamente en menús comunes, como los menús **Editar,** **Dar** formato **y** Ver. Si hay una cantidad considerable de comandos especializados disponibles, se puede crear un nuevo menú. Este nuevo menú solo debe estar visible cuando el documento tiene el foco.

- Se puede colocar una barra de herramientas incrustada en la parte superior del editor. Esto es preferible a tener una barra de herramientas independiente que aparezca fuera del editor.

- Mantenga siempre una selección en la ventana Explorador de soluciones una jerarquía activa similar.

- Al hacer doble clic en un documento de la Explorador de soluciones debe realizar la misma acción que **Abrir**.

- Si se puede usar más de un editor en un tipo de documento, el usuario debe  poder invalidar o restablecer la acción predeterminada en un tipo de documento determinado mediante el cuadro de diálogo Abrir con haciendo clic con el botón derecho en el archivo y **seleccionando** Abrir con en el menú contextual.

- No cree un asistente en un documento.

### <a name="user-expectations-for-specific-document-types"></a>Expectativas del usuario para tipos de documento específicos
Hay varios tipos básicos diferentes de editores de documentos y cada uno tiene un conjunto de interacciones que son coherentes con otros del mismo tipo.

- **Editor basado en texto: editor** de código, archivos de registro

- **Superficie de diseño:** Diseñador de formularios WPF, formularios Windows Forms

- **Editor de estilo diálogo:** Diseñador de manifiestos, propiedades del proyecto

- **Diseñador de modelos: diseñador** de flujo de trabajo, mapa de código, diagrama de arquitectura, progresión

También hay varios tipos que no son de editor que usan el documento. Aunque no editan documentos por sí mismos, sí deben seguir las interacciones estándar para las ventanas de documentos.

- **Informes:** Informe de IntelliTrace, informe de Hyper-V, informe del generador de perfiles

- **Panel:** Centro de diagnósticos

#### <a name="text-based-editors"></a>Editores basados en texto

- El documento participa en el modelo de pestaña de vista previa, lo que permite obtener una vista previa del documento sin abrirlo.

- La estructura del documento se puede representar dentro de una ventana de herramientas complementaria, como un esquema de documento.

- IntelliSense (si procede) se comportará de forma coherente con otros editores de código.

- Los elementos emergentes o la interfaz de usuario de asistencia siguen estilos y patrones similares para la interfaz de usuario similar existente, como CodeLens.

- Los mensajes relacionados con el estado del documento se mostrarán en un control de barra de información en la parte superior del documento o en la barra de estado.

- El usuario debe ser capaz de personalizar la apariencia de fuentes y colores mediante una página Herramientas **> Opciones,** ya sea la página Fuentes y colores compartida o una específica del editor.

#### <a name="design-surfaces"></a>Superficies de diseño

- Un diseñador vacío debe tener una marca de agua en la superficie que indique cómo empezar.

- Los mecanismos de cambio de vista seguirán los patrones existentes, como hacer doble clic para abrir un editor de código o pestañas dentro de la ventana del documento, lo que permite la interacción con ambos paneles.

- La adición de elementos a la superficie de diseño debe realizarse a través del Cuadro de herramientas, a menos que se requiera una ventana de herramientas muy específica.

- Los elementos de la superficie seguirán un modelo de selección coherente.

- Las barras de herramientas incrustadas solo contienen comandos específicos del documento, no comandos comunes como **Guardar.**

#### <a name="dialog-style-editors"></a>Editores de estilo diálogo

- El diseño del control debe seguir las convenciones de diseño de diálogo normales.

- Las pestañas del editor no deben coincidir con la apariencia de las pestañas del documento, deben coincidir con uno de los dos estilos de tabulación interiores permitidos.

- Los usuarios deben poder interactuar con los controles solo mediante el teclado. activando el editor y controlando los controles o usando mnemotécnicas estándar.

- El diseñador debe usar el modelo save común. No se deben colocar botones generales guardar o confirmar en la superficie, aunque otros botones pueden ser adecuados.

#### <a name="model-designers"></a>Diseñadores de modelos

- Un diseñador vacío debe tener una marca de agua en la superficie que indique cómo empezar.

- La adición de elementos a la superficie de diseño debe realizarse a través del cuadro de herramientas.

- Los elementos de la superficie seguirán un modelo de selección coherente.

- Las barras de herramientas incrustadas solo contienen comandos específicos del documento, no comandos comunes como **Guardar.**

- Puede aparecer una leyenda en la superficie, ya sea indicativa o una marca de agua.

- El usuario debe ser capaz de personalizar la apariencia de las fuentes y colores mediante una página Herramientas **> Opciones,** ya sea la página Fuentes y colores compartida o una específica del editor.

#### <a name="reports"></a>Informes

- Normalmente, los informes son de solo información y no participan en el modelo Guardar. Sin embargo, pueden incluir interacción, como vínculos a otra información o secciones pertinentes que se expanden y contraen.

- La mayoría de los comandos de la superficie deben ser hipervínculos, no botones.

- El diseño debe incluir un encabezado y seguir las directrices de diseño del informe estándar.

#### <a name="dashboards"></a>Paneles

- Los paneles no tienen un modelo de interacción, pero sirven como medio para ofrecer otras herramientas.

- No participan en el modelo Guardar.

- Los usuarios deben poder interactuar con los controles solo mediante el teclado, ya sea activando el editor y controlando con tabulación los controles o usando mnemotécnicas estándar.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Diálogos

### <a name="introduction"></a>Introducción
Los diálogos Visual Studio normalmente deben admitir una unidad discreta del trabajo del usuario y, a continuación, descartarse.

Si ha determinado que necesita un cuadro de diálogo, tiene tres opciones, en orden de preferencia:

1. Integre las características en uno de los diálogos compartidos de Visual Studio.

2. Cree su propio diálogo con un patrón que se encuentra en un diálogo similar existente.

3. Cree un cuadro de diálogo, siguiendo las directrices de interacción y diseño.

En esta sección se describe cómo elegir el patrón de diálogo correcto dentro Visual Studio de trabajo y las convenciones comunes para el diseño de diálogos.

### <a name="themes"></a>Temas
Los cuadros de Visual Studio siguen uno de estos dos estilos básicos:

#### <a name="standard-unthemed"></a>Estándar (sin ateso)
La mayoría de los diálogos son diálogos de utilidad estándar y deben estar sin ser desenlazados. No vuelva a crear plantillas de controles comunes ni intente crear botones o controles "modernos" con estilo. Los controles y la apariencia de chrome siguen [las directrices de interacción](/windows/desktop/uxguide/win-dialog-box)estándar de Escritorio de Windows para los cuadros de diálogo .

#### <a name="themed"></a>Temática
Los cuadros de diálogo de "firma" especializados pueden tener un estilo. Los diálogos con problemas tienen una apariencia distinta, que también tiene algunos patrones de interacción especiales asociados al estilo. Tema del cuadro de diálogo solo si cumple estos requisitos:

- El diálogo es una experiencia común que se verá y usará con frecuencia o por muchos usuarios (por ejemplo, el **cuadro de diálogo Nuevo** proyecto).

- El cuadro de diálogo contiene elementos destacados de la marca de producto (por ejemplo, el cuadro **de diálogo Configuración de** la cuenta).

- El cuadro de diálogo aparece como una parte integral de un flujo mayor que incluye otros diálogos con aspecto (por ejemplo, el cuadro de diálogo **Agregar servicio conectado).**

- El diálogo es una parte importante de una experiencia que desempeña un papel estratégico en la promoción o diferenciación de una versión del producto.

Al crear un cuadro de diálogo con tema, use los colores de entorno adecuados y siga los patrones de interacción y diseño correctos. (Vea [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)).

### <a name="dialog-design"></a>Diseño de diálogos
Los diálogos bien diseñados tienen en cuenta los siguientes elementos:

- Tarea de usuario que se admite

- Estilo, lenguaje y terminología del texto del cuadro de diálogo

- Elección de controles y convenciones de interfaz de usuario

- Especificación de diseño visual y alineación de controles

- Acceso mediante el teclado

#### <a name="content-organization"></a>Organización de contenido
Tenga en cuenta las diferencias entre estos tipos básicos de diálogos:

- [Los diálogos simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentan controles en una sola ventana modal. La presentación puede incluir variaciones de patrones de control complejos, incluido un selector de campos o una barra de iconos.

- [Los diálogos por capas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se usan para obtener el máximo partido de los recursos de pantalla cuando una sola parte de la interfaz de usuario consta de varios grupos de controles. Las agrupaciones del cuadro de diálogo están "en capas" a través de controles de pestaña, controles de lista de navegación o botones para que el usuario pueda elegir qué agrupación ver en un momento dado.

- [Los asistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) son útiles para dirigir al usuario a través de una secuencia lógica de pasos hacia la finalización de una tarea. Se ofrecen una serie de opciones en paneles secuenciales, que a veces presentan diferentes flujos de trabajo ("ramas") en función de una elección realizada en el panel anterior.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Cuadros de diálogo sencillos
Un cuadro de diálogo simple es una presentación de controles en una sola ventana modal. Esta presentación puede incluir variaciones de patrones de control complejos, como un selector de campos. Para los diálogos simples, siga el diseño general estándar, así como cualquier diseño específico necesario para agrupaciones de control complejas.

![>Crear clave de nombre fuerte es un ejemplo de un cuadro de diálogo simple en Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Crear clave de nombre fuerte es un ejemplo de un cuadro de diálogo simple en Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Cuadros de diálogo en capas
Los diálogos por capas incluyen pestañas, paneles y árboles incrustados. Se usan para maximizar el patrimonio cuando hay varios grupos de controles ofrecidos en una sola parte de la interfaz de usuario. Las agrupaciones se agrupan en capas para que el usuario pueda elegir qué agrupación ver en cualquier momento.

En el caso más sencillo, el mecanismo para cambiar entre agrupaciones es un control de tabulación. Hay varias alternativas disponibles. Consulte Priorización y capas para saber cómo elegir el estilo más adecuado.

El **cuadro de diálogo &gt; Opciones** de herramientas es un ejemplo de un diálogo en capas mediante un árbol incrustado:

![Herramientas > opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Herramientas > opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Asistentes
Los asistentes son útiles para dirigir al usuario a través de una secuencia lógica de pasos en la finalización de una tarea. Se ofrecen una serie de opciones en paneles secuenciales y el usuario debe continuar en cada paso antes de continuar con el siguiente. Una vez que haya suficientes valores predeterminados disponibles, se **habilita el** botón Finalizar.

 Los asistentes modales se usan para tareas que:

- Contener bifurcaciones, donde se ofrecen distintas rutas de acceso en función de las opciones del usuario

- Contienen dependencias entre pasos, donde los pasos posteriores dependen de la entrada del usuario de los pasos anteriores.

- Son lo suficientemente complejos que la interfaz de usuario debe usarse para explicar las opciones ofrecidas y los posibles resultados en cada paso.

- Son transaccionales, lo que requiere que se complete un conjunto de pasos en su totalidad antes de que se confirman los cambios.

### <a name="common-conventions"></a>Convenciones comunes
Para lograr un diseño y funcionalidad óptimos con los diálogos, siga estas convenciones sobre el tamaño, la posición, los estándares, la configuración y alineación del control, el texto de la interfaz de usuario, las barras de título, los botones de control y las claves de acceso.

Para obtener instrucciones específicas del diseño, vea [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Size
Los diálogos deben ajustarse a una resolución de pantalla mínima de 1024 x 768 y el tamaño inicial del diálogo no debe superar los 900 x 700 píxeles. Es posible que los diálogos se puedan cambiar de tamaño, pero no es un requisito.

Hay dos recomendaciones para los diálogos que se pueden cambiar de tamaño:

1. Que un tamaño mínimo es un valor definido para el cuadro de diálogo que se optimizará para el conjunto de controles sin recorte y se ajustará para dar cabida al crecimiento razonable de la localización.

2. Que el tamaño escalado por el usuario se conserve de sesión a sesión. Por ejemplo, si el usuario escala un diálogo al 150 %, se mostrará un inicio posterior del diálogo al 150 %.

#### <a name="position"></a>Posición
Los diálogos deben aparecer centrados en el IDE en el primer inicio. No es necesario conservar la última posición de los diálogos que no se pueden cambiar de tamaño, por lo que aparecerán centrados en los inicios posteriores.

Para los diálogos que se pueden cambiar de tamaño, el tamaño debe conservarse en los inicios posteriores. En el caso de los diálogos modales que se pueden cambiar de tamaño, no es necesario conservar la posición. Mostrarlos centrados en el IDE evita la posibilidad de que el cuadro de diálogo aparezca en una posición imprevisible o inutilizable cuando la configuración de visualización del usuario ha cambiado.

En el caso de los diálogos modelados que se pueden cambiar de posición, la posición del usuario debe mantenerse en los inicios posteriores, ya que el diálogo puede usarse con frecuencia como parte integral de un flujo de trabajo mayor.

Cuando los diálogos deben generar otros diálogos, el diálogo de nivel superior debe estar en cascada hacia la derecha y hacia abajo desde el elemento primario para que sea obvio para el usuario que ha navegado a un nuevo lugar.

#### <a name="modality"></a>Modalidad
Ser modal significa que los usuarios deben completar o cancelar el diálogo antes de continuar. Puesto que los diálogos modales bloquean que el usuario interactúe con otras partes del entorno, el flujo de tareas de la característica debe usarlos con la mayor moderación posible. Cuando se necesita una operación modal, Visual Studio varios diálogos compartidos en los que puede integrar las características. Si debe crear un diálogo nuevo, siga el patrón de interacción de un diálogo existente con una funcionalidad similar.

Cuando los usuarios necesitan realizar dos  actividades  a la vez, como Buscar y reemplazar mientras escriben código nuevo, el cuadro de diálogo debe ser modelado para que el usuario pueda cambiar fácilmente entre ellas. Visual Studio suele usar ventanas de herramientas para este tipo de tarea vinculada compatible con el editor.

#### <a name="control-configuration"></a>Configuración del control
Sea coherente con las configuraciones de control existentes que logran lo mismo en Visual Studio.

#### <a name="title-bars"></a>Barras de título

- El texto de la barra de título debe reflejar el nombre del comando que lo inició.

- No se debe usar ningún icono en las barras de título del cuadro de diálogo. En los casos en los que el sistema requiera uno, use el logotipo Visual Studio aplicación.

- Los cuadros de diálogo no deben tener botones para minimizar ni maximizar.

- Los botones de ayuda de la barra de título han quedado en desuso. No los agregue a nuevos cuadros de diálogo. Cuando existan, deben iniciar un tema de Ayuda que sea conceptualmente relevante para la tarea.

  ![Especificaciones de las guías para las barras de título en Visual Studio diálogos](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Especificaciones de las guías para las barras de título en Visual Studio diálogos

#### <a name="control-buttons"></a>Botones de control
En general, los **botones** **Aceptar,** Cancelar y Ayuda se deben organizar horizontalmente en la esquina inferior derecha del cuadro de diálogo.  La pila vertical alternativa se permite si un diálogo tiene otros botones en la parte inferior del diálogo que presentarían confusión visual con los botones de control.

![Configuraciones aceptables para botones de control en Visual Studio diálogos](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configuraciones aceptables para botones de control en Visual Studio diálogos

El cuadro de diálogo debe incluir un botón de control predeterminado. Para determinar el mejor comando para usar como valor predeterminado, elija entre las siguientes opciones (enumeradas por orden de prioridad):

- Elija el comando más seguro y más seguro como valor predeterminado. Esto significa elegir el comando más probable para evitar la pérdida de datos y evitar el acceso al sistema no deseado.

- Si la pérdida de datos y la seguridad no son factores, elija el comando predeterminado en función de la comodidad. Incluir el comando más probable como valor predeterminado mejorará el flujo de trabajo del usuario cuando el cuadro de diálogo admita tareas frecuentes o repetitivas.

Evite elegir una acción destructiva permanente para el comando predeterminado. Si este comando está presente, elija un comando más seguro como valor predeterminado en su lugar.

#### <a name="access-keys"></a>Claves de acceso
No use las claves de acceso para **los botones Aceptar,** **Cancelar** o **Ayuda.** Estos botones se asignan a las teclas de método abreviado de forma predeterminada:

| Nombre del botón | Método abreviado de teclado |
| --- | --- |
| Aceptar | Entrar |
| Cancelar | Esc |
| Ayuda | F1 |

#### <a name="imagery"></a>Imágenes
Use imágenes con moderación en los cuadros de diálogo. No use iconos grandes en los cuadros de diálogo simplemente para usar espacio. Use imágenes solo si son una parte importante de transmitir el mensaje al usuario, como iconos de advertencia o animaciones de estado.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Priorización y en capas

#### <a name="prioritizing-your-ui"></a>Priorización de la interfaz de usuario
Es posible que sea necesario poner determinados elementos de la interfaz de usuario a la vanguardia y colocar opciones y comportamientos más avanzados (incluidos comandos oscuros) en diálogos. Lleve la funcionalidad de uso frecuente a la primera línea haciendo espacio para ella y haciendo que sea visible de forma predeterminada en la interfaz de usuario con una etiqueta de texto cuando se muestra el cuadro de diálogo.

#### <a name="layering-your-ui"></a>Capas de la interfaz de usuario
Si ha determinado que un diálogo es necesario, pero la funcionalidad relacionada que desea presentar al usuario va más allá de lo que se puede mostrar en un diálogo simple, debe crear capas de la interfaz de usuario. Los métodos de capas más comunes Visual Studio usan pestañas y artículos o paneles. En algunos casos, las regiones que se pueden expandir y contraer pueden ser adecuadas. Por lo general, no se recomienda la interfaz de usuario adaptable en Visual Studio.

Existen ventajas y desventajas para los distintos métodos de capas de la interfaz de usuario a través de controles de tipo pestaña. Revise la lista siguiente para asegurarse de que está eligiendo una técnica de capas adecuada para su situación.

##### <a name="tabbing"></a>Tabulación

| Mecanismo de conmutación | Ventajas y uso adecuado | Desventajas y uso inadecuado |
| --- | --- | --- |
| Control Tab | Agrupación lógica de páginas de diálogo en conjuntos relacionados<br /><br />Resulta útil para menos de cinco páginas (o el número de pestañas que caben en una fila en el cuadro de diálogo) de controles relacionados en el cuadro de diálogo.<br /><br />Las etiquetas de tabulación deben ser cortas: una o dos palabras que puedan identificar fácilmente el contenido<br /><br />Un estilo de diálogo común del sistema<br /><br />Ejemplo: **propiedades Explorador de archivos &gt; elemento** | Crear etiquetas cortas descriptivas puede ser difícil<br /><br />Por lo general, no escala más allá de cinco pestañas en un cuadro de diálogo.<br /><br />Inadecuado si tiene demasiadas pestañas para una fila (use una técnica de capas alternativa)<br /><br />No extensible |
| Navegación lateral | Dispositivo de conmutación simple que puede dar cabida a más categorías que pestañas<br /><br />Lista plana de categorías (sin jerarquía)<br /><br />Extensible<br /><br />Ejemplo: **Personalizar... &gt; Agregar comando** | No es un buen uso del espacio horizontal si hay menos de tres grupos<br /><br />La tarea podría ser más adecuada para una lista desplegable. |
| Tree (control) | Permite categorías ilimitadas<br /><br />Permite agrupar o jerarquía de categorías<br /><br />Extensible<br /><br />Ejemplo: **Opciones de &gt; herramientas** | Las jerarquías muy anidadas pueden provocar un desplazamiento horizontal excesivo<br /><br />Visual Studio tiene una sobreabundancia de vistas de árbol |
| Asistente | Ayuda con la finalización de tareas guiando al usuario a través de pasos secuenciales basados en tareas: el asistente representa una tarea de alto nivel y los paneles individuales representan las subtareas necesarias para realizar la tarea general.<br /><br />Resulta útil cuando la tarea cruza los límites de la interfaz de usuario, como cuando el usuario tendría que usar varios editores y ventanas de herramientas para completar la tarea.<br /><br />Útil cuando la tarea requiere bifurcación<br /><br />Resulta útil cuando la tarea contiene dependencias entre pasos.<br /><br />Resulta útil cuando se pueden presentar varias tareas similares con una bifurcación de decisión en un diálogo para reducir el número de diálogos similares diferentes. | Inadecuado para cualquier tarea que no requiera un flujo de trabajo secuencial<br /><br />Los usuarios pueden sentirse sobrecargados y confusos por un asistente con demasiados pasos<br /><br />Los asistentes tienen un espacio real de pantalla inherentemente limitado |

##### <a name="hallways-or-dashboards"></a>Locales o paneles
Los paneles y los paneles son cuadros de diálogo o paneles que sirven como puntos de inicio para otros diálogos y ventanas. El "pequeño" bien diseñado muestra inmediatamente solo las opciones, comandos y configuraciones más comunes, lo que permite al usuario realizar fácilmente tareas comunes. Al igual que un vecino del mundo real proporciona puertas para acceder a las salas detrás de ellas, aquí la interfaz de usuario menos común se recopila en "salas" independientes (a menudo otros diálogos) de funcionalidad relacionada a la que se puede acceder desde el edificio principal.

Como alternativa, una interfaz de usuario que ofrece toda la funcionalidad disponible en una sola colección en lugar de refactorizar la funcionalidad menos común en ubicaciones independientes es simplemente un panel.

![Concepto básico para exponer la interfaz de usuario adicional en Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concepto básico para exponer la interfaz de usuario adicional en Outlook

##### <a name="adaptive-ui"></a>Interfaz de usuario adaptativa
Mostrar u ocultar la interfaz de usuario en función del uso o la experiencia de un usuario autodenódo es otra manera de presentar la interfaz de usuario necesaria mientras se ocultan otras partes. Esto no se recomienda en Visual Studio, ya que los algoritmos para decidir cuándo mostrar u ocultar la interfaz de usuario pueden ser complicados y las reglas siempre serán incorrectas para algún conjunto de casos.

## <a name="projects"></a><a name="BKMK_Projects"></a> Proyectos

### <a name="projects-in-the-solution-explorer"></a>Proyectos en el Explorador de soluciones
La mayoría de los proyectos se clasifican como basados en referencias, basados en directorios o mixtos. Los tres tipos de proyectos se admiten simultáneamente en el Explorador de soluciones. La raíz de la experiencia del usuario al trabajar con proyectos tiene lugar dentro de esta ventana. Aunque los distintos nodos de proyecto son proyectos de tipo de referencia, directorio o modo mixto, hay un patrón de interacción común que se debe aplicar como punto de partida antes de divergen en patrones de usuario específicos del proyecto.

Los proyectos siempre deben:

- Compatibilidad con la capacidad de agregar carpetas de proyecto para organizar el contenido del proyecto

- Mantener un modelo coherente para la persistencia del proyecto

Los proyectos también deben mantener modelos de interacción coherentes para:

- Eliminación de elementos de proyecto

- Guardar documentos

- Edición de propiedades del proyecto

- Edición del proyecto en una vista alternativa

- Operaciones de arrastrar y colocar

### <a name="drag-and-drop-interaction-model"></a>Modelo de interacción de arrastrar y colocar
Normalmente, los proyectos se clasifican como basados en referencias (solo pueden conservar referencias a elementos de proyecto en el almacenamiento), basados en directorios (pueden conservar solo los elementos de proyecto almacenados físicamente dentro de la jerarquía de un proyecto) o mixtos (capaces de conservar referencias o elementos físicos). El IDE admite los tres tipos de proyectos simultáneamente dentro del **Explorador de soluciones**.

Desde una perspectiva de arrastrar y colocar, se deben aplicar las siguientes características a cada tipo de proyecto dentro del **Explorador de soluciones**:

- **Proyecto basado en referencias:** El punto clave es que el proyecto arrastra una referencia a un elemento en el almacenamiento. Cuando un proyecto basado en referencias actúa como origen de una operación de movimiento, solo debe quitar la referencia al elemento del proyecto. El elemento no debe eliminarse realmente de la unidad de disco duro. Cuando un proyecto basado en referencias actúa como destino de una operación de movimiento (o copia), debe agregar una referencia al elemento de origen original sin realizar una copia privada del elemento.

- **Proyecto basado en directorios:** Desde un punto de vista de arrastrar y colocar, el proyecto arrastra el elemento físico en lugar de una referencia. Cuando un proyecto basado en directorios actúa como origen de una operación de movimiento, debería terminar eliminando el elemento físico de la unidad de disco duro y quitándolo del proyecto. Cuando un proyecto basado en directorios actúa como destino de una operación de movimiento (o copia), debe realizar una copia del elemento de origen en su ubicación de destino.

- **Proyecto de destino mixto:** Desde un punto de vista de arrastrar y colocar, el comportamiento de este tipo de proyecto se basa en la naturaleza del elemento que se arrastra (ya sea una referencia a un elemento en el almacenamiento o al propio elemento). El comportamiento correcto para las referencias y los elementos físicos se describe anteriormente.

Si solo hubiera un tipo de proyecto en el Explorador de soluciones **,** las operaciones de arrastrar y colocar serían sencillas. Dado que cada sistema de proyecto tiene la capacidad de definir su propio comportamiento de arrastrar y colocar, se deben seguir determinadas directrices (basadas en el comportamiento de arrastrar y colocar de Explorador de Windows) para garantizar una experiencia de usuario predecible:

- Una operación de arrastre sin modificar en el **Explorador de soluciones** (cuando no se mantiene presionada la tecla Ctrl ni mayús) debe dar lugar a una operación de movimiento.

- La operación de desplazamiento y arrastre también debe dar lugar a una operación de movimiento.

- La operación ctrl-arrastre debe dar lugar a una operación de copia.

- Los sistemas de proyectos mixtos y basados en referencias admiten la noción de agregar un vínculo (o referencia) al elemento de origen. Cuando estos proyectos son el destino de una operación de arrastrar y colocar (cuando **ctrl +** Mayús se mantiene presionado), debería dar lugar a una referencia al elemento que se agrega al proyecto.

No todas las operaciones de arrastrar y colocar son razonables en combinaciones de proyectos mixtos, basados en directorios y basados en referencias. En concreto, es problemático pretender permitir una operación de movimiento entre un proyecto de origen basado en directorios y un proyecto de destino basado en referencias porque el proyecto basado en directorio de origen tendrá que eliminar el elemento de origen al finalizar el traslado. A continuación, el proyecto basado en referencias de destino terminaría con una referencia a un elemento eliminado.

También resulta engañoso pretender permitir una operación de copia entre estos tipos de proyectos porque el proyecto basado en referencias de destino no debe realizar una copia independiente del elemento de origen. De forma similar, no se debe permitir el arrastre de Ctrl + Mayús a un proyecto de destino basado en directorio porque un proyecto basado en directorios no puede conservar las referencias. En los casos en los que no se admite la operación de arrastrar y colocar, el IDE debe no permitir la colocación y mostrar al usuario el cursor sin colocar (que se muestra en la tabla de punteros siguiente).

Para implementar correctamente el comportamiento de arrastrar y colocar, el proyecto de origen del arrastre debe comunicar su naturaleza al proyecto de destino. (Por ejemplo, ¿se basa en la referencia o en el directorio?) Esta información se indica mediante el formato del Portapapeles que ofrece el origen. Como origen de una operación de arrastrar (o de copiar el Portapapeles), un proyecto debe ofrecer o, respectivamente, dependiendo de si el proyecto se basa en referencias o `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` en directorios. Ambos formatos tienen el mismo contenido de datos, que es similar al formato de Windows, salvo que las listas de cadenas, en lugar de ser nombres de archivo, son una lista de cadenas terminada en doble terminación (como se devuelve desde o según `CF_HDROP` `NULL` `Projref` `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` corresponda).

Como destino de una operación de colocar (o pegar del Portapapeles), un proyecto debe aceptar y , aunque el control exacto de la operación de arrastrar y colocar varía en función de la naturaleza del proyecto de destino y del proyecto de `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` origen. El proyecto de origen declara su naturaleza por si ofrece `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` . El destino de la colocación entiende su propia naturaleza y, por tanto, tiene suficiente información para tomar decisiones sobre si se debe realizar un movimiento, una copia o un vínculo. El usuario también modifica qué operación de arrastrar y colocar debe realizarse presionando las teclas Ctrl, Mayús o Ctrl y Mayús. Es importante que el destino de colocación indique correctamente qué operación se realizará de antemano en sus `DragEnter` `DragOver` métodos y . El **Explorador de soluciones** automáticamente sabe si el proyecto de origen y el proyecto de destino son el mismo proyecto.

No se admite específicamente el arrastre de elementos de proyecto entre instancias de Visual Studio (por ejemplo, de una instancia de devenv.exe a otra). El **Explorador de soluciones** también deshabilita directamente esto.

El usuario siempre debe ser capaz de determinar el efecto de una operación de arrastrar y colocar seleccionando un elemento, arrastrándolo a la ubicación de destino y observando cuál de los siguientes punteros del mouse aparece antes de quitar el elemento:

| Puntero del mouse | Comando | Descripción |
| :---: | --- | --- |
| ![Icono de mouse "No colocar"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Sin colocar | El elemento no se puede descartar en la ubicación especificada. |
| ![Icono de mouse "Copiar"](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copiar | El elemento se copiará en la ubicación de destino. |
| ![Icono de mouse "Mover"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Move | El elemento se trasladará a la ubicación de destino. |
| ![Icono de mouse "Agregar referencia"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Agregar referencia | Se agregará una referencia al elemento seleccionado a la ubicación de destino. |

#### <a name="reference-based-projects"></a>Proyectos basados en referencias
 En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que se deben realizar en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino basados en referencia:

| Modificador | Category | Elemento de origen: Referencia o vínculo | Elemento de origen: elemento físico o sistema de archivos ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Sin modificador | Acción | Move | Vínculo |
| Sin modificador | Destino | Agrega referencia al elemento original | Agrega referencia al elemento original |
| Sin modificador | Origen | Elimina la referencia al elemento original. | Conserva el elemento original |
| Sin modificador | Resultado | `DROPEFFECT_MOVE` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento |
| Mayús+Arrastrar | Acción | Move | Sin colocar |
| Mayús+Arrastrar | Destino | Agrega referencia al elemento original | Sin colocar |
| Mayús+Arrastrar | Origen | Elimina la referencia al elemento original. | Sin colocar |
| Mayús+Arrastrar | Resultado | `DROPEFFECT_MOVE` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | Sin colocar |
| Ctrl+Arrastrar | Acción | Copiar | Sin colocar |
| Ctrl+Arrastrar | Destino | Agrega referencia al elemento original | Sin colocar |
| Ctrl+Arrastrar | Origen | Conserva la referencia al elemento original | Sin colocar |
| Ctrl+Arrastrar | Resultado | `DROPEFFECT_COPY` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | Sin colocar |
| Ctrl+Mayús+Arrastrar | Acción | Vínculo | Vínculo |
| Ctrl+Mayús+Arrastrar | Destino | Agrega referencia al elemento original | Agrega referencia al elemento original |
| Ctrl+Mayús+Arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| Ctrl+Mayús+Arrastrar | Resultado | `DROPEFFECT_LINK` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento |
| Ctrl+Mayús+Arrastrar | Nota | Igual que el comportamiento de arrastrar y colocar para los accesos directos en Explorador de Windows. ||
| Cortar y pegar | Acción | Move | Vínculo |
| Cortar y pegar | Destino | Agrega referencia al elemento original | Agrega referencia al elemento original |
| Cortar y pegar | Origen | Conserva la referencia al elemento original|Conserva el elemento original |
| Cortar y pegar | Resultado | El elemento permanece en la ubicación original en el almacenamiento | El elemento permanece en la ubicación original en el almacenamiento |
| Copiar y pegar | Acción | Copiar | Vínculo |
| Copiar y pegar | Origen | Agrega referencia al elemento original | Agrega referencia al elemento original |
| Copiar y pegar | Resultado | Conserva la referencia al elemento original | Conserva el elemento original |
| Copiar y pegar | Acción | El elemento permanece en la ubicación original en el almacenamiento | El elemento permanece en la ubicación original en el almacenamiento |

#### <a name="directory-based-projects"></a>Proyectos basados en directorios
En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que se deben realizar en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino basados en directorios:

| Modificador | Category | Elemento de origen: Referencia o vínculo | Elemento de origen: elemento físico o sistema de archivos ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Sin modificador | Acción | Move | Move |
| Sin modificador | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Sin modificador | Origen | Elimina la referencia al elemento original. | Elimina la referencia al elemento original. |
| Mayús+Arrastrar | Acción | Move | Move |
| Mayús+Arrastrar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Mayús+Arrastrar | Origen | Elimina la referencia al elemento original. | Elimina el elemento de la ubicación original. |
| Mayús+Arrastrar | Resultado | `DROPEFFECT_MOVE` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_MOVE` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento |
| Ctrl+Arrastrar | Acción | Copiar | Copiar |
| Ctrl+Arrastrar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Ctrl+Arrastrar | Origen | Conserva la referencia al elemento original | Conserva la referencia al elemento original |
| Ctrl+Arrastrar | Resultado | `DROPEFFECT_COPY` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_COPY` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento |
| Ctrl+Mayús+Arrastrar | | Sin colocar | Sin colocar |
| Cortar y pegar | Acción | Move | Move |
| Cortar y pegar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Cortar y pegar | Origen | Elimina la referencia al elemento original. | Elimina el elemento de la ubicación original. |
| Cortar y pegar | Resultado | El elemento permanece en la ubicación original en el almacenamiento | El elemento se elimina de la ubicación original en el almacenamiento |
| Copiar y pegar | Acción | Copiar | Copiar |
| Copiar y pegar | Destino | Agrega referencia al elemento original | Copia el elemento en la ubicación de destino |
| Copiar y pegar | Origen | Conserva el elemento original | Conserva el elemento original |
| Copiar y pegar | Resultado | El elemento permanece en la ubicación original en el almacenamiento | El elemento permanece en el almacenamiento de ubicación original |

#### <a name="mixed-target-projects"></a>Proyectos de destino mixto
En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que se deben realizar en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino mixto:

| Modificador | Category | Elemento de origen: Referencia o vínculo | Elemento de origen: elemento físico o sistema de archivos ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Sin modificador | Acción | Move | Move |
| Sin modificador | Destino | Agrega referencia al elemento original | Copia el elemento en la ubicación de destino |
| Sin modificador | Origen | Elimina la referencia al elemento original. | Elimina la referencia al elemento original. |
| Sin modificador | Resultado | `DROPEFFECT_ MOVE` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE` se devuelve como acción desde `::Drop` y el elemento se elimina de la ubicación original en el almacenamiento |
| Mayús+Arrastrar | Acción | Move | Move |
| Mayús+Arrastrar | Destino | Agrega referencia al elemento original | Copia el elemento en la ubicación de destino |
| Mayús+Arrastrar | Origen | Elimina la referencia al elemento original. | Elimina el elemento de la ubicación original. |
| Mayús+Arrastrar | Resultado | `DROPEFFECT_ MOVE` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE` se devuelve como acción desde `::Drop` y el elemento se elimina de la ubicación original en el almacenamiento |
| Ctrl+Arrastrar | Acción | Copiar | Copiar |
| Ctrl+Arrastrar | Destino | Agrega referencia al elemento original | Copia el elemento en la ubicación de destino |
| Ctrl+Arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| Ctrl+Arrastrar | Resultado | `DROPEFFECT_ COPY` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ COPY` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento |
| Ctrl+Mayús+Arrastrar | Acción | Vínculo | Vínculo |
| Ctrl+Mayús+Arrastrar | Destino | Agrega referencia al elemento original | Agrega referencia al elemento de origen original. |
| Ctrl+Mayús+Arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| Ctrl+Mayús+Arrastrar | Resultado | `DROPEFFECT_ LINK` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ LINK` se devuelve como acción desde y `::Drop` el elemento permanece en la ubicación original en el almacenamiento |
| Cortar y pegar | Acción | Move | Move |
| Cortar y pegar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Cortar y pegar | Origen | Elimina la referencia al elemento original. | Elimina el elemento de la ubicación original. |
| Cortar y pegar | Resultado | El elemento permanece en la ubicación original en el almacenamiento | El elemento se elimina de la ubicación original en el almacenamiento |
| Copiar y pegar | Acción | Copiar | Copiar |
| Copiar y pegar | Destino | Agrega referencia al elemento original | Copia el elemento en la ubicación de destino |
| Copiar y pegar | Origen | Conserva el elemento original | Conserva el elemento original |
| Copiar y pegar | Resultado | El elemento permanece en la ubicación original en el almacenamiento | El elemento permanece en la ubicación original en el almacenamiento |

Estos detalles deben tenerse en cuenta al implementar el arrastre en el **Explorador de soluciones**:

- Diseño para varios escenarios de selección.

- Los nombres de archivo (ruta de acceso completa) deben ser únicos en el proyecto de destino o no se debe permitir la colocación.

- Los nombres de carpeta deben ser únicos (sin mayúsculas de minúsculas) en el nivel en que se van a descartar.

- Hay diferencias de comportamiento entre los archivos que están abiertos o cerrados en el momento de arrastrar (no se mencionan en los escenarios anteriores).

- Los archivos de nivel superior se comportan de forma ligeramente diferente a los archivos de carpetas.

Otro problema que se debe tener en cuenta es cómo controlar las operaciones de movimiento en elementos que tienen diseñadores o editores abiertos. El comportamiento esperado es el siguiente (esto se aplica a todos los tipos de proyecto):

1. Si el editor o diseñador abierto no tiene cambios no guardados, la ventana editor/diseñador debe cerrarse de forma silenciosa.

2. Si el editor o diseñador abierto tiene cambios no guardados, el origen del arrastre debe esperar a que se produzca la colocación y, a continuación, pedir al usuario que guarde los cambios no confirmados en los documentos abiertos antes de cerrar la ventana con un mensaje similar al siguiente:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Esto ofrece al usuario la oportunidad de guardar el trabajo en curso antes de que el destino haga sus copias. Se ha agregado `IVsHierarchyDropDataSource2::OnBeforeDropNotify` un nuevo método para habilitar este control.

A continuación, el destino copiará el estado del elemento tal como está en el almacenamiento (sin incluir los cambios no guardados en el editor si el usuario eligió **No**). Una vez que el destino ha completado su copia (en ), el origen tiene la oportunidad de completar la parte de eliminación de la operación `IVsHierarchyDropDataSource::Drop` de movimiento (en `IVsHierarchyDropDataSource::OnDropNotify` ).

Todos los editores con cambios no guardados se deben dejar abiertos. En el caso de los documentos con cambios no guardados, esto significa que se realizará la parte de copia de la operación de movimiento, pero se anulará la parte de eliminación. En un escenario de selección múltiple cuando el usuario elige **No**, los documentos con cambios no guardados no deben cerrarse ni quitarse, pero los que no tienen cambios no guardados deben cerrarse y quitarse.
