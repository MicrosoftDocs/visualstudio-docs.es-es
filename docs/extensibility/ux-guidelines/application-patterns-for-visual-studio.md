---
title: Patrones de aplicación para Visual Studio ? Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 036c95951fe3dc9e65a0f3338f75ae9867d721c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698595"
---
# <a name="application-patterns-for-visual-studio"></a>Patrones de aplicaciones para Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interacciones de ventanas

### <a name="overview"></a>Información general
Los dos tipos de ventana principal utilizados en Visual Studio son editores de documentos y ventanas de herramientas. Raros, pero posibles, son grandes diálogos no iniciados. Aunque todos estos son no esmimosos en el shell, sus patrones son fundamentalmente diferentes. En esta sección se trata la diferencia entre las ventanas de documento, las ventanas de herramientas y los cuadros de diálogo no más mideteros. Los patrones de diálogo modal se tratan en [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparación de patrones de uso de ventanas
**Las ventanas** de documento casi siempre se muestran dentro del pozo del documento. Esto le da al editor de documentos un "escenario central" para organizar ventanas de herramientas suplementarias alrededor.

Una ventana de **herramientas** se muestra con mayor frecuencia como una ventana separada y más pequeña contraída contra el borde del IDE. Esto puede ser visible, oculto u auto-oculto. Sin embargo, a veces las ventanas de herramientas se presentan dentro del documento bien, desmarcando la **propiedad Ventana/Acoplamiento** en la ventana. Esto da como resultado más bienes raíces, pero también una decisión de diseño común: al intentar integrarse en Visual Studio, debe decidir si la característica debe mostrar una ventana de herramientas o una ventana de documento.

**Se desaconsejan** los cuadros de diálogo no especificados en Visual Studio. La mayoría de los cuadros de diálogo no iniciados son, por definición, ventanas de herramientas flotantes y deben implementarse de esa manera. Los cuadros de diálogo no iniciados se permiten en los casos en que el tamaño de una ventana de herramientas normal acoplada al lado del vaciado sería demasiado limitador. También se permiten en los casos en que el usuario sería probable que mueva el cuadro de diálogo a un monitor secundario.

Piense cuidadosamente en qué tipo de contenedor necesita. Las consideraciones comunes del patrón de uso para el diseño de la interfaz de usuario se encuentran en la tabla siguiente.

||Ventana del documento|Ventana de herramientas|Diálogo no midetes|
|-|---------------------|-----------------|---------------------|
| **Posición** | Siempre posicionado dentro del documento bien y no se acopla alrededor de los bordes del IDE. Se puede "tirar" para que flote por separado de la cáscara principal. | Por lo general, se acopla la pestaña alrededor de los bordes del IDE, pero se puede personalizar para que sea flotante, oculto automáticamente (sin anclar) o acoplado dentro del documento.|Ventana flotante grande separada del IDE. |
| **Confirmar modelo** | *Compromiso retrasado*<br /><br /> Para guardar los datos en un documento, el usuario debe publicar el comando **Guardar archivo &gt; **, Guardar **como**o **Guardar todo.** Una ventana de documento tiene el concepto de que los datos dentro de ella se "suciedad" y luego se compromete a uno de los comandos save. Al cerrar una ventana de documento, todo el contenido se guarda en el disco o se pierde. | *Compromiso inmediato*<br /><br /> No hay ningún modelo de guardado. Para las ventanas de herramientas del inspector que ayudan a editar un archivo, el archivo debe estar abierto en el editor o diseñador activo, y el editor o diseñador es el propietario de la salvaguardia. | *Compromiso retrasado o inmediato*<br /><br /> La mayoría de las veces, un cuadro de diálogo no es posible requiere una acción para confirmar los cambios y permite una operación "Cancelar", que revierte los cambios realizados en la sesión de diálogo.  Esto diferencia un cuadro de diálogo no quede de una ventana de herramientas en que las ventanas de herramientas siempre tienen un modelo de confirmación inmediata. |
| **Visibilidad** | *Abrir/Crear (archivo) y Cerrar*<br /><br /> La apertura de una ventana de documento se realiza abriendo un documento existente o utilizando una plantilla para crear un nuevo documento. No hay ningún \<comando "Abrir editor específico>". | *Ocultar y mostrar*<br /><br /> Las ventanas de herramientas de instancia única se pueden ocultar o mostrar. El contenido y los estados de la ventana de herramientas persisten, ya sea a la vista u ocultos. Las ventanas de herramientas de varias instancias se pueden cerrar y ocultar. Cuando se cierra una ventana de herramientas de varias instancias, se descarta el contenido y el estado de la ventana de herramientas. | *Lanzado desde un comando*<br /><br /> Los cuadros de diálogo se inician desde un comando basado en tareas. |
| **Instancias** | *Multi-instancia*<br /><br /> Varios editores pueden estar abiertos al mismo tiempo y editar diferentes archivos, mientras que algunos editores también permiten que el mismo archivo esté abierto en más de un editor (mediante el comando **Ventana &gt; Nueva ventana).**<br /><br /> Un solo editor puede estar editando uno o varios archivos al mismo tiempo (Diseñador de proyectos). | *Instancia única o múltiple*<br /><br /> El contenido cambia para reflejar el contexto (como en el Explorador de propiedades) o insertar el foco/contexto en otras ventanas (Lista de tareas, Explorador de soluciones).<br /><br /> Las ventanas de herramientas de instancia única y de varias instancias deben asociarse a la ventana de documento activa a menos que haya una razón convincente para no hacerlo. | *Instancia única* |
| **Ejemplos** | **Editores de**texto, como el editor de código<br /><br /> **Superficies**de diseño, como un diseñador de formularios o una superficie de modelado<br /><br /> Diseños de control **similares a los cuadros**de diálogo, como el Diseñador de manifiestos | El Explorador de **soluciones** proporciona una solución y proyectos contenidos en la solución<br /><br /> El **Explorador** de servidores proporciona una vista jerárquica de los servidores y las conexiones de datos que el usuario elige abrir en la ventana. Al abrir un objeto desde la jerarquía de base de datos, como una consulta, se abre una ventana de documento y se permite al usuario editar la consulta.<br /><br /> El **Navegador de** propiedades muestra las propiedades del objeto seleccionado en una ventana de documento u otra ventana de herramientas. Las propiedades se presentan en una vista de cuadrícula jerárquica o en controles complejos de tipo cuadro de diálogo y permiten al usuario establecer los valores de esas propiedades. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Ventanas de herramientas

### <a name="overview"></a>Información general
Las ventanas de herramientas admiten el trabajo del usuario que se produce en las ventanas de documento. Se pueden usar para mostrar una jerarquía que representa un objeto raíz fundamental que Visual Studio proporciona y puede manipular.

Al considerar una nueva ventana de herramientas en el IDE, los autores deben:

- Utilice ventanas de herramientas existentes apropiadas para tareas y no cree otras nuevas con una funcionalidad similar. Las nuevas ventanas de herramientas solo se deben crear si ofrecen una "herramienta" o funcionalidad significativamente diferente que no se puede integrar en una ventana similar, o convirtiendo una ventana existente en un concentrador dinámico.

- Utilice una barra de comandos estándar, si es necesario, en la parte superior de la ventana de herramientas.

- Sea coherente con los patrones ya presentes en otras ventanas de herramientas para la presentación de control y la navegación por teclado.

- Sea coherente con la presentación de control en otras ventanas de herramientas.

- Haga que las ventanas de herramientas específicas del documento sean visibles automáticamente cuando sea posible, de modo que aparezcan solo cuando se active el documento principal.

- Asegúrese de que el contenido de la ventana sea navegable por el teclado (teclas de flecha de soporte).

#### <a name="tool-window-states"></a>Estados de la ventana de herramientas
Las ventanas de herramientas de Visual Studio tienen diferentes estados, algunos de los cuales están activados por el usuario (como la característica de ocultación automática). Otros estados, como la visible automática, permiten que las ventanas de herramientas aparezcan en el contexto correcto y se oculten cuando no sea necesario. Hay cinco estados de ventana de herramientas en total.

- Las ventanas de herramientas **acopladas/ancladas** se pueden adjuntar a cualquiera de los cuatro lados del área del documento. El icono de pasador aparece en la barra de título de la ventana de herramientas. La ventana de herramientas se puede acoplar horizontal o verticalmente a lo largo del borde del vaciado y otras ventanas de herramientas, y también se puede vincular a pestañas.

- Las ventanas de herramientas **ocultas automáticamente** no están ancladas. La ventana se puede deslizar fuera de la vista, dejando una pestaña (con el nombre de la ventana de herramientas y su icono) en el borde del área del documento. La ventana de herramientas se desliza hacia fuera cuando un usuario pasa el cursor sobre la pestaña.

- Las ventanas de herramientas **visibles** automáticamente aparecen automáticamente cuando se inicia otra parte de la interfaz de usuario, como un editor, o gana el foco.

- Las ventanas de herramientas **flotantes** se sitúan fuera del IDE. Esto es útil para configuraciones de varios monitores.

- Las ventanas de herramientas de **documentos con pestañas** se pueden acoplar dentro del pozo del documento. Esto es útil para ventanas de herramientas grandes, como el Examinador de objetos, que necesitan más bienes raíces de lo que permite el acoplamiento a los bordes del marco.

![Estados de la ventana de herramientas en Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Estados de la ventana de herramientas en Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Instancia única y multiinstancia
Las ventanas de herramientas son de una sola instancia o de varias instancias. Es posible que algunas ventanas de herramientas de instancia única estén asociadas a la ventana de documento activa, mientras que las ventanas de herramientas de varias instancias podrían no estar asociadas. Las ventanas de herramientas de varias instancias responden al comando **Ventana &gt; nueva ventana** creando una nueva instancia de la ventana. La siguiente imagen ilustra una ventana de herramientas que habilita el comando Nueva ventana cuando una instancia de la ventana está activa:

![Ventana de herramientas que habilita el comando 'Nueva ventana' cuando una instancia de la ventana está activa](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Ventana de herramientas que habilita el comando 'Nueva ventana' cuando una instancia de la ventana está activa

Las ventanas de herramientas de una sola instancia se pueden ocultar o mostrar, mientras que las ventanas de herramientas de varias instancias se pueden cerrar y ocultar. Todas las ventanas de herramientas se pueden acoplar, vincular a tabulaciones, flotar o establecerse como una ventana secundaria de interfaz de varios documentos (MDI) (similar a una ventana de documento). Todas las ventanas de herramientas deben responder a los comandos de administración de ventanas adecuados en el menú Ventana:

![Comandos de administración de ventanas en el menú Ventana de Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandos de administración de ventanas en el menú Ventana de Visual Studio

#### <a name="document-specific-tool-windows"></a>Ventanas de herramientas específicas del documento
Algunas ventanas de herramientas están diseñadas para cambiar en función de un tipo determinado de documento. Estas ventanas se actualizan continuamente para reflejar la funcionalidad aplicable a la ventana de documento activa en el IDE.

Ejemplos de ventanas de herramientas cuyo contenido cambia para reflejar el editor seleccionado son el Cuadro de herramientas y el Esquema del documento. Estas ventanas muestran una marca de agua cuando un editor tiene el foco que no ofrece contexto a la ventana.

#### <a name="navigable-list-tool-windows"></a>Ventanas de herramientas de lista navegables
Algunas ventanas de herramientas muestran una lista de elementos navegables con los que el usuario puede interactuar. En este tipo de ventana, siempre debe haber comentarios para el elemento actual en la lista, incluso si la ventana está inactiva. La lista debe responder a los comandos **GoToNextLocation** y **GoToPrevLocation** cambiando también el elemento seleccionado actualmente en la ventana

Ejemplos de ventanas de herramientas de lista navegables son el Explorador de soluciones y la ventana Buscar resultados.

### <a name="tool-window-types"></a>Tipos de ventanas de herramientas

#### <a name="common-tool-windows-and-their-functions"></a>Ventanas de herramientas comunes y sus funciones

**Ventanas de herramientas jerárquicas**

| Ventana de herramientas | Función |
| --- | --- |
| Explorador de soluciones | Un árbol jerárquico que muestra una lista de documentos contenidos en proyectos, archivos varios y elementos de solución. La visualización de los elementos dentro de los proyectos se define mediante el paquete que posee el tipo de proyecto (por ejemplo, tipos basados en referencias, basados en directorios o en modo mixto). |
| Vista de clases | Un árbol jerárquico de las clases y varios elementos en el conjunto de trabajo de documentos, independientemente de los propios archivos. |
| Explorador de servidores | Un árbol jerárquico que muestra todos los servidores y conexiones de datos de la solución. |
| Esquema de documento | La estructura jerárquica del documento activo. |

**Ventanas de herramientas de cuadrícula**

| Ventana de herramientas | Función |
| --- | --- |
| Propiedades | Cuadrícula que muestra una lista de propiedades para el objeto seleccionado, junto con selectores de valor para editar esas propiedades. |
| Lista de tareas | Una cuadrícula que permite al usuario crear/editar/eliminar tareas y comentarios. |

**Ventanas de herramientas de contenido**

| Ventana de herramientas | Función |
| --- | --- |
| Ayuda | Una ventana que permite a los usuarios acceder a varios métodos para obtener ayuda, desde "¿Cómo puedo?" vídeos a foros de MSDN. |
| Ayuda dinámica | Una ventana de herramientas que muestra vínculos para ayudar a los temas aplicables a la selección actual. |
| Examinador de objetos | Conjunto de marcos de dos columnas con una lista de componentes de objetos jerárquicos en el panel izquierdo y las propiedades y métodos del objeto en la columna derecha. |

**Ventanas de herramientas de diálogo**

| Ventana de herramientas | Función |
| --- | --- |
| Buscar | Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución. |
| Búsqueda avanzada | Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución. |

**Otras ventanas de herramientas**

::: moniker range="vs-2017"

| Ventana de herramientas | Función |
| --- | --- |
| Cuadro de herramientas | La ventana de herramientas utilizada para almacenar elementos que se colocarán en superficies de diseño, lo que proporciona una fuente de arrastre coherente para todos los diseñadores. |
| Página de inicio | Portal del usuario a Visual Studio, con acceso a fuentes de noticias para desarrolladores, ayuda de Visual Studio y proyectos recientes. Los usuarios también pueden crear páginas de inicio personalizadas copiando el archivo\" StartPage.xaml desde el directorio de archivos de programa de Visual Studio "Common7-IDE-StartPages a la carpeta StartPages del directorio de documentos de Visual Studio y, a continuación, editando el XAML a mano o abriéndolo en Visual Studio u otro editor de código. |

::: moniker-end

::: moniker range=">=vs-2019"

| Ventana de herramientas | Función |
| --- | --- |
| Cuadro de herramientas | La ventana de herramientas utilizada para almacenar elementos que se colocarán en superficies de diseño, lo que proporciona una fuente de arrastre coherente para todos los diseñadores. |

::: moniker-end

**Ventanas de herramientas del depurador**

| Ventana de herramientas | Función |
| --- | --- |
| Autos ||
| Inmediata ||
| Salida | La ventana de salida se puede utilizar siempre que tenga eventos textuales o estado para declarar. |
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

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Convenciones del editor de documentos

### <a name="document-interactions"></a>Interacciones de documentos
El "documento bien" es el espacio más grande dentro del IDE y es donde el usuario generalmente ha centrado su atención con el fin de completar sus tareas, asistido por ventanas de herramientas suplementarias. Los editores de documentos representan las unidades fundamentales de trabajo que el usuario abre y guarda en Visual Studio. Conservan un fuerte sentido de selección vinculado al Explorador de soluciones u otras ventanas de jerarquía activas. El usuario debe ser capaz de apuntar a una de esas ventanas de jerarquía y saber dónde está contenido el documento y su relación con la solución, el proyecto u otro objeto raíz proporcionado por un paquete de Visual Studio.

La edición de documentos requiere una experiencia de usuario coherente. Para permitir que el usuario se centre en la tarea en cuestión en lugar de en la administración de ventanas y la búsqueda de comandos, seleccione una estrategia de vista de documento que mejor se adapte a las tareas del usuario para editar ese tipo de documento.

#### <a name="common-interactions-for-the-document-well"></a>Interacciones comunes para el documento bien

- Mantenga un modelo de interacción coherente en las experiencias comunes **de Nuevo archivo** y Abrir **archivo.**

- Actualice la funcionalidad relacionada en ventanas y menús relacionados cuando se abra la ventana del documento.

- Los comandos de menú se integran adecuadamente en menús comunes como los menús **Editar**, **Formato**y **Ver.** Si hay una cantidad sustancial de comandos especializados disponibles, se puede crear un nuevo menú. Este nuevo menú debe estar visible solo cuando el documento tiene el foco.

- Una barra de herramientas incrustada se puede colocar en la parte superior del editor. Esto es preferible a tener una barra de herramientas independiente que aparece fuera del editor.

- Mantenga siempre una selección en el Explorador de soluciones o en una ventana de jerarquía activa similar.

- Al hacer doble clic en un documento en el Explorador de soluciones, se debe realizar la misma acción que **Abrir**.

- Si se puede utilizar más de un editor en un tipo de documento, el usuario debe poder anular o restablecer la acción predeterminada en un tipo de documento determinado mediante el cuadro de diálogo **Abrir con** haciendo clic con el botón derecho en el archivo y seleccionando **Abrir con** en el menú contextual.

- No cree un asistente en un documento bien.

### <a name="user-expectations-for-specific-document-types"></a>Expectativas de usuario para tipos de documentos específicos
Hay varios tipos básicos diferentes de editores de documentos y cada uno tiene un conjunto de interacciones que son coherentes con otros del mismo tipo.

- **Editor basado en texto:** editor de código, archivos de registro

- **Superficie de diseño:** WPF WPF Forms designer, Windows Forms

- **Editor de estilo de diálogo:** Diseñador de manifiestos, propiedades del proyecto

- **Diseñador de modelos:** diseñador de flujo de trabajo, mapa de código, diagrama de arquitectura, progresión

También hay varios tipos que no son de editor que utilizan bien el documento. Aunque no editan documentos por sí mismos, sí deben seguir las interacciones estándar para las ventanas de documentos.

- **Informes:** Informe IntelliTrace, informe de Hyper-V, informe del generador de perfiles

- **Panel de control:** Centro de Diagnóstico

#### <a name="text-based-editors"></a>Editores basados en texto

- El documento participa en el modelo de pestaña de vista previa, lo que permite obtener una vista previa del documento sin abrirlo.

- La estructura del documento se puede representar dentro de una ventana de herramientas complementaria, como un esquema de documento.

- IntelliSense (si procede) se comportará de forma coherente con otros editores de código.

- Las ventanas emergentes o la interfaz de usuario de asistencia siguen estilos y patrones similares para la interfaz de usuario similar existente, como CodeLens.

- Los mensajes relativos al estado del documento se presentarán en un control de la barra de información en la parte superior del documento o en la barra de estado.

- El usuario debe ser capaz de personalizar la apariencia de las fuentes y colores mediante una página **Herramientas > Opciones,** ya sea la página Fuentes y colores compartida o una específica del editor.

#### <a name="design-surfaces"></a>Superficies de diseño

- Un diseñador vacío debe tener una marca de agua en la superficie que indique cómo empezar.

- Los mecanismos de cambio de vista seguirán los patrones existentes, como hacer doble clic para abrir un editor de código o pestañas dentro de la ventana del documento que permiten la interacción con ambos paneles.

- La adición de elementos a la superficie de diseño debe realizarse a través del cuadro de herramientas, a menos que se requiera una ventana de herramientas muy específica.

- Los elementos de la superficie seguirán un modelo de selección coherente.

- Las barras de herramientas incrustadas solo contienen comandos específicos del documento, no comandos comunes como **Guardar**.

#### <a name="dialog-style-editors"></a>Editores de estilo de diálogo

- El diseño del control debe seguir las convenciones normales del diseño del cuadro de diálogo.

- Las pestañas dentro del editor no deben coincidir con la apariencia de las pestañas del documento, deben coincidir con uno de los dos estilos de pestañas interiores permitidos.

- Los usuarios deben poder interactuar con los controles utilizando solo el teclado; ya sea activando el editor y tabulando a través de controles o usando mnemotécnicas estándar.

- El diseñador debe usar el modelo Save común. No se deben colocar botones generales Guardar o confirmar en la superficie, aunque otros botones pueden ser adecuados.

#### <a name="model-designers"></a>Diseñadores de modelos

- Un diseñador vacío debe tener una marca de agua en la superficie que indique cómo empezar.

- La adición de elementos a la superficie de diseño debe realizarse a través del cuadro de herramientas.

- Los elementos de la superficie seguirán un modelo de selección coherente.

- Las barras de herramientas incrustadas solo contienen comandos específicos del documento, no comandos comunes como **Guardar**.

- Una leyenda puede aparecer en la superficie, ya sea indicativa o una marca de agua.

- El usuario debe ser capaz de personalizar la apariencia de las fuentes/colores mediante una página **Herramientas > Opciones,** ya sea la página Fuentes y colores compartida o una específica del editor.

#### <a name="reports"></a>Informes

- Los informes suelen ser de solo información y no participan en el modelo Guardar. Sin embargo, pueden incluir interacción, como vínculos a otra información relevante o secciones que se expanden y contraen.

- La mayoría de los comandos en la superficie deben ser hipervínculos, no botones.

- El diseño debe incluir un encabezado y seguir las directrices de diseño de informe estándar.

#### <a name="dashboards"></a>Paneles

- Los paneles no tienen un modelo de interacción en sí mismos, pero sirven como un medio para ofrecer una variedad de otras herramientas.

- No participan en el modelo Guardar.

- Los usuarios deben poder interactuar con los controles utilizando solo el teclado, ya sea activando el editor y tabulando a través de los controles o utilizando mnemotécnicas estándar.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Diálogos

### <a name="introduction"></a>Introducción
Los cuadros de diálogo de Visual Studio normalmente deben admitir una unidad discreta del trabajo del usuario y, a continuación, se descartan.

Si ha determinado que necesita un diálogo, tiene tres opciones, en orden de preferencia:

1. Integre las características en uno de los cuadros de diálogo compartidos de Visual Studio.

2. Cree su propio cuadro de diálogo utilizando un patrón que se encuentra en un cuadro de diálogo similar existente.

3. Cree un nuevo cuadro de diálogo, siguiendo las directrices de interacción y diseño.

En esta sección se describe cómo elegir el patrón de cuadro de diálogo correcto en los flujos de trabajo de Visual Studio y las convenciones comunes para el diseño de cuadros de diálogo.

### <a name="themes"></a>Temas
Los cuadros de diálogo de Visual Studio siguen uno de los dos estilos básicos:

#### <a name="standard-unthemed"></a>Estándar (sin tema)
La mayoría de los cuadros de diálogo son cuadros de diálogo de utilidad estándar y deben ser destemáticos. No vuelva a crear plantillas de controles comunes ni intente crear botones o controles "modernos" estilizados. Los controles y la apariencia de chrome siguen [las directrices de interacción estándar](/windows/desktop/uxguide/win-dialog-box)de Escritorio de Windows para los cuadros de diálogo.

#### <a name="themed"></a>Temática
Los cuadros de diálogo de "firma" de especialidad pueden ser temáticos. Los cuadros de diálogo temáticos tienen una apariencia distinta, que también tiene algunos patrones de interacción especiales asociados con el estilo. Tema de su diálogo sólo si cumple con estos requisitos:

- El cuadro de diálogo es una experiencia común que se verá y usará a menudo o por muchos usuarios (por ejemplo, el cuadro de diálogo **Nuevo proyecto.**

- El cuadro de diálogo contiene elementos destacados de la marca del producto (por ejemplo, el cuadro de diálogo Configuración de la **cuenta).**

- El cuadro de diálogo aparece como una parte integral de un flujo más grande que incluye otros cuadros de diálogo temáticos (por ejemplo, el cuadro de diálogo **Agregar servicio conectado).**

- El diálogo es una parte importante de una experiencia que desempeña un papel estratégico en la promoción o diferenciación de una versión del producto.

Al crear un cuadro de diálogo temático, utilice los colores de entorno adecuados y siga los patrones de diseño e interacción correctos. (Consulte [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Diseño de cuadros de diálogo
Los cuadros de diálogo bien diseñados tienen en cuenta los siguientes elementos:

- La tarea de usuario que se admite

- El estilo de texto del cuadro de diálogo, el idioma y la terminología

- Opciones de control y convenciones de interfaz de usuario

- Especificación de diseño visual y alineación de control

- Acceso mediante el teclado

#### <a name="content-organization"></a>Organización de contenido
Considere las diferencias entre estos tipos básicos de diálogos:

- [Los cuadros de diálogo simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentan controles en una sola ventana modal. La presentación puede incluir variaciones de patrones de control complejos, incluido un selector de campos o una barra de iconos.

- Los [cuadros](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) de diálogo en capas se utilizan para aprovechar al máximo los bienes inmuebles de la pantalla cuando una sola parte de la interfaz de usuario comprende varios grupos de controles. Las agrupaciones del cuadro de diálogo se "capan" a través de controles de pestaña, controles de lista de navegación o botones para que el usuario pueda elegir qué agrupación ver en un momento dado.

- [Los asistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) son útiles para dirigir al usuario a través de una secuencia lógica de pasos hacia la finalización de una tarea. Una serie de opciones se ofrecen en paneles secuenciales, a veces introduciendo diferentes flujos de trabajo ("ramas") dependiendo de una elección realizada en el panel anterior.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Diálogos sencillos
Un cuadro de diálogo simple es una presentación de controles en una sola ventana modal. Esta presentación puede incluir variaciones de patrones de control complejos, como un selector de campos. Para cuadros de diálogo simples, siga el diseño general estándar, así como cualquier diseño específico necesario para agrupaciones de control complejas.

![>crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Diálogos en capas
Los cuadros de diálogo en capas incluyen pestañas, paneles y árboles incrustados. Se utilizan para maximizar los bienes raíces cuando hay varios grupos de controles ofrecidos en una sola parte de la interfaz de usuario. Las agrupaciones están en capas para que el usuario pueda elegir qué agrupación ver en cualquier momento.

En el caso más sencillo, el mecanismo para cambiar entre agrupaciones es un control de pestañas. Hay varias alternativas disponibles. Consulte Priorización y capas para obtener información sobre cómo elegir el estilo más adecuado.

El cuadro de diálogo ** &gt; Opciones** de herramientas es un ejemplo de un cuadro de diálogo en capas que utiliza un árbol incrustado:

![Herramientas > Opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Herramientas > Opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Asistentes
Los asistentes son útiles para dirigir al usuario a través de una secuencia lógica de pasos en la finalización de una tarea. Se ofrecen una serie de opciones en paneles secuenciales y el usuario debe continuar a través de cada paso antes de continuar con el siguiente. Una vez que hay suficientes valores predeterminados disponibles, el botón **Finalizar** está habilitado.

 Los asistentes modales se utilizan para tareas que:

- Contienen bifurcación, donde se ofrecen diferentes rutas dependiendo de las opciones del usuario

- Contienen dependencias entre pasos, donde los pasos subsiguientes dependen de la entrada del usuario de los pasos anteriores

- Son lo suficientemente complejos como para que la interfaz de usuario se use para explicar las opciones ofrecidas y los posibles resultados en cada paso

- Son transaccionales, lo que requiere un conjunto de pasos que deben completarse en su totalidad antes de que se confirmen los cambios

### <a name="common-conventions"></a>Convenciones comunes
Para lograr un diseño y funcionalidad óptimos con los cuadros de diálogo, siga estas convenciones sobre el tamaño del cuadro de diálogo, la posición, los estándares, la configuración y alineación del control, el texto de la interfaz de usuario, las barras de título, los botones de control y las teclas de acceso.

Para obtener instrucciones específicas del diseño, vea [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Tamaño
Los cuadros de diálogo deben ajustarse a una resolución de pantalla mínima de 1024 x 768, y el tamaño del cuadro de diálogo inicial no debe superar los 900 x 700 píxeles. Los cuadros de diálogo pueden ser redimensionables, pero no es un requisito.

Hay dos recomendaciones para los cuadros de diálogo redimensionables:

1. Que un tamaño mínimo es un definido para el cuadro de diálogo que optimizará para el conjunto de controles sin recorte y se ajustará para adaptarse al crecimiento razonable de la localización.

2. Que el tamaño escalado por el usuario persiste de una sesión a otra. Por ejemplo, si el usuario escala un cuadro de diálogo al 150%, se mostrará un inicio posterior del cuadro de diálogo al 150%.

#### <a name="position"></a>Posición
Los cuadros de diálogo deben aparecer centrados en el IDE en el primer lanzamiento. No es necesario conservar la última posición de los cuadros de diálogo no redimensionables, por lo que aparecerán centrados en los lanzamientos posteriores.

Para los cuadros de diálogo de tamaño variable, el tamaño debe conservarse en los lanzamientos posteriores. Para los cuadros de diálogo modales de tamaño variable, no es necesario conservar la posición. Mostrarlos centrados en el IDE evita la posibilidad de que el cuadro de diálogo aparezca en una posición impredecible o inutilizable cuando la configuración de visualización del usuario ha cambiado.

Para los cuadros de diálogo no posicionados que se pueden cambiar de posición, la posición del usuario debe mantenerse en los lanzamientos posteriores, ya que el cuadro de diálogo se puede usar con frecuencia como parte integral de un flujo de trabajo más grande.

Cuando los cuadros de diálogo deben generar otros cuadros de diálogo, el cuadro de diálogo superior debe conectarse en cascada a la derecha y hacia abajo desde el elemento primario para que sea obvio para el usuario que ha navegado a un nuevo lugar.

#### <a name="modality"></a>Modalidad
Ser modal significa que los usuarios deben completar o cancelar el cuadro de diálogo antes de continuar. Dado que los cuadros de diálogo modales impiden que el usuario interactúe con otras partes del entorno, el flujo de tareas de la entidad debe usarlos con la mayor moderación posible. Cuando es necesaria una operación modal, Visual Studio tiene una serie de cuadros de diálogo compartidos en los que puede integrar las características. Si debe crear un nuevo cuadro de diálogo, siga el patrón de interacción de un cuadro de diálogo existente con una funcionalidad similar.

Cuando los usuarios necesitan realizar dos actividades a la vez, como **Buscar** y **reemplazar** al escribir código nuevo, el cuadro de diálogo debe ser no codificador para que el usuario pueda cambiar fácilmente entre ellos. Visual Studio generalmente usa ventanas de herramientas para este tipo de tarea vinculada compatible con el editor.

#### <a name="control-configuration"></a>Configuración de control
Sea coherente con las configuraciones de control existentes que logran lo mismo en Visual Studio.

#### <a name="title-bars"></a>Barras de título

- El texto de la barra de título debe reflejar el nombre del comando que lo inició.

- No se debe utilizar ningún icono en las barras de título del cuadro de diálogo. En los casos en que el sistema lo requiera, use el logotipo de Visual Studio.

- Los cuadros de diálogo no deben tener botones de minimizar o maximizar.

- Los botones de ayuda de la barra de título han quedado obsoletos. No los agregue a nuevos cuadros de diálogo. Cuando existen, deben iniciar un tema de Ayuda que sea conceptualmente relevante para la tarea.

  ![Especificaciones de las guías de título en los cuadros de diálogo de Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Especificaciones de las guías de título en los cuadros de diálogo de Visual Studio

#### <a name="control-buttons"></a>Botones de control
En general, los botones **Aceptar**, **Cancelar**y **Ayuda** deben organizarse horizontalmente en la esquina inferior derecha del cuadro de diálogo. La pila vertical alternativa se permite si un cuadro de diálogo tiene varios otros botones en la parte inferior del cuadro de diálogo que presentarían confusión visual con los botones de control.

![Configuraciones aceptables para botones de control en los cuadros de diálogo de Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configuraciones aceptables para botones de control en los cuadros de diálogo de Visual Studio

El cuadro de diálogo debe incluir un botón de control predeterminado. Para determinar el mejor comando que se utilizará como valor predeterminado, elija una de las siguientes opciones (listadas en orden de prioridad):

- Elija el comando más seguro y seguro como valor predeterminado. Esto significa elegir el comando más probable para evitar la pérdida de datos y evitar el acceso involuntario al sistema.

- Si la pérdida de datos y la seguridad no son factores, elija el comando predeterminado en función de la comodidad. Incluir el comando más probable como predeterminado mejorará el flujo de trabajo del usuario cuando el cuadro de diálogo admita tareas frecuentes o repetitivas.

Evite elegir una acción destructiva permanente para el comando predeterminado. Si tal comando está presente, elija un comando más seguro como el valor por defecto en su lugar.

#### <a name="access-keys"></a>Claves de acceso
No utilice las teclas de acceso para los botones **Aceptar**, **Cancelar**o **Ayuda.** Estos botones se asignan a las teclas de método abreviado de forma predeterminada:

| Nombre del botón | Métodos abreviados de teclado |
| --- | --- |
| Aceptar | Escriba |
| Cancelar | Esc |
| Ayuda | F1 |

#### <a name="imagery"></a>Imágenes
Utilice imágenes con moderación en los cuadros de diálogo. No utilice iconos grandes en los cuadros de diálogo simplemente para usar espacio. Utilice imágenes solo si son una parte importante de la transmisión del mensaje al usuario, como iconos de advertencia o animaciones de estado.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Priorización y estratificación

#### <a name="prioritizing-your-ui"></a>Priorizar la interfaz de usuario
Puede ser necesario llevar ciertos elementos de la interfaz de usuario a la vanguardia y colocar un comportamiento y opciones más avanzados (incluidos los comandos oscuros) en los cuadros de diálogo. Lleve la funcionalidad de uso común a la vanguardia haciendo espacio para ella y haciéndola visible de forma predeterminada en la interfaz de usuario con una etiqueta de texto cuando se muestra el cuadro de diálogo.

#### <a name="layering-your-ui"></a>Capas de la interfaz de usuario
Si ha determinado que un cuadro de diálogo es necesario, pero la funcionalidad relacionada que desea presentar al usuario va más allá de lo que se puede mostrar en un cuadro de diálogo simple, entonces debe poner la capa de la interfaz de usuario. Los métodos de capas más comunes que usa Visual Studio son pestañas y pasillos o paneles. En algunos casos, las regiones que pueden expandirse y contraerse pueden ser adecuadas. Por lo general, no se recomienda la interfaz de usuario adaptable en Visual Studio.

Hay ventajas y desventajas para diferentes métodos de creación de capas de la interfaz de usuario a través de controles de tipo pestaña. Revise la lista siguiente para asegurarse de que está eligiendo una técnica de capas que sea adecuada a su situación.

##### <a name="tabbing"></a>Tabulación

| Mecanismo de conmutación | Ventajas y uso adecuado | Desventajas y uso inapropiado |
| --- | --- | --- |
| Control Tab | Agrupar lógicamente páginas de diálogo en conjuntos relacionados<br /><br />Es útil para menos de cinco (o el número de pestañas que caben en una fila en el cuadro de diálogo) páginas de controles relacionados en el cuadro de diálogo<br /><br />Las etiquetas de tabulación deben ser cortas: una o dos palabras que pueden identificar fácilmente el contenido<br /><br />Un estilo de diálogo común del sistema<br /><br />Ejemplo: **Propiedades &gt; ** del elemento del Explorador de archivos | Hacer etiquetas cortas descriptivas puede ser difícil<br /><br />Generalmente no escala más allá de cinco pestañas en un cuadro de diálogo<br /><br />Inapropiado si tiene demasiadas pestañas para una fila (utilice una técnica de capas alternativa)<br /><br />No extensible |
| Navegación de la barra lateral | Dispositivo de conmutación simple que puede acomodar más categorías que pestañas<br /><br />Lista plana de categorías (sin jerarquía)<br /><br />Extensible<br /><br />Ejemplo: **Personalizar... Añadir &gt; comando** | No es un buen uso del espacio horizontal si hay menos de tres grupos<br /><br />La tarea podría ser más adecuada para una lista desplegable |
| Tree (control) | Permite categorías ilimitadas<br /><br />Permite agrupar y/o jerarquíar categorías<br /><br />Extensible<br /><br />Ejemplo: ** &gt; Opciones de herramientas** | Las jerarquías muy anidadas pueden causar un desplazamiento horizontal excesivo<br /><br />Visual Studio tiene una sobreabundancia de vistas de árbol |
| Asistente | Ayuda con la finalización de tareas guiando al usuario a través de pasos secuenciales basados en tareas: el asistente representa una tarea de alto nivel y los paneles individuales representan las subtareas necesarias para realizar la tarea general<br /><br />Resulta útil cuando la tarea cruza los límites de Ui, como cuando el usuario tendría que usar varios editores y ventanas de herramientas para completar la tarea<br /><br />Resulta útil cuando la tarea requiere bifurcación<br /><br />Resulta útil cuando la tarea contiene dependencias entre pasos<br /><br />Resulta útil cuando varias tareas similares con una bifurcación de decisión se pueden presentar en un cuadro de diálogo para reducir el número de cuadros de diálogo similares diferentes | Inapropiado para cualquier tarea que no requiera un flujo de trabajo secuencial<br /><br />Los usuarios pueden sentirse abrumados y confundidos por un asistente con demasiados pasos<br /><br />Los magos han limitado intrínsecamente los bienes raíces de la pantalla |

##### <a name="hallways-or-dashboards"></a>Pasillos o tableros
Los pasillos y paneles son cuadros de diálogo o paneles que sirven como puntos de inicio a otros cuadros de diálogo y ventanas. El "hallway" bien diseñado inmediatamente expone solo las opciones, comandos y configuraciones más comunes, lo que permite al usuario realizar fácilmente tareas comunes. Al igual que un pasillo del mundo real proporciona puertas para acceder a las habitaciones detrás de ellos, aquí la interfaz de usuario menos común se recoge en "habitaciones" separadas (a menudo otros diálogos) de funcionalidad relacionada a la que se puede acceder desde el pasillo principal.

Como alternativa, una interfaz de usuario que ofrece toda la funcionalidad disponible en una sola colección en lugar de refactorizar la funcionalidad menos común en ubicaciones independientes es simplemente un panel.

![Concepto de pasillo para exponer la interfaz de usuario adicional en Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concepto de pasillo para exponer la interfaz de usuario adicional en Outlook

##### <a name="adaptive-ui"></a>Interfaz de usuario adaptativa
Mostrar u ocultar la interfaz de usuario en función del uso o de la experiencia autoinformada de un usuario es otra forma de presentar la interfaz de usuario necesaria mientras se ocultan otras partes. Esto no se recomienda en Visual Studio, ya que los algoritmos para decidir cuándo mostrar u ocultar la interfaz de usuario pueden ser complicados y las reglas siempre serán incorrectas para algún conjunto de casos.

## <a name="projects"></a><a name="BKMK_Projects"></a>Proyectos

### <a name="projects-in-the-solution-explorer"></a>Proyectos en el Explorador de soluciones
La mayoría de los proyectos se clasifican como basados en referencias, basados en directorios o mixtos. Los tres tipos de proyectos se admiten simultáneamente en el Explorador de soluciones. La raíz de la experiencia del usuario en el trabajo con proyectos tiene lugar dentro de esta ventana. Aunque los nodos de proyecto diferentes son proyectos de tipo de referencia, directorio o modo mixto, hay un patrón de interacción común que se debe aplicar como punto de partida antes de divergir en patrones de usuario específicos del proyecto.

Los proyectos siempre deben:

- Admite la capacidad de agregar carpetas de proyecto para organizar el contenido del proyecto

- Mantener un modelo coherente para la persistencia del proyecto

Los proyectos también deben mantener modelos de interacción coherentes para:

- Eliminación de elementos de proyecto

- Guardar documentos

- Edición de propiedades del proyecto

- Edición del proyecto en una vista alternativa

- Operaciones de arrastrar y soltar

### <a name="drag-and-drop-interaction-model"></a>Modelo de interacción de arrastrar y soltar
Normalmente, los proyectos se clasifican como basados en referencias (capaces de conservar solo las referencias a elementos de proyecto en el almacenamiento), basados en directorios (capaces de conservar solo los elementos del proyecto almacenados físicamente en la jerarquía de un proyecto) o mixtos (capaces de conservar referencias o elementos físicos). El IDE da cabida a los tres tipos de proyectos simultáneamente en el Explorador de **soluciones.**

Desde una perspectiva de arrastrar y colocar, las siguientes características deben aplicarse a cada tipo de proyecto en el Explorador de **soluciones:**

- **Proyecto basado en referencias:** El punto clave es que el proyecto está arrastrando alrededor de una referencia a un elemento en el almacenamiento. Cuando un proyecto basado en referencias actúa como origen para una operación de movimiento, solo debe quitar la referencia al elemento del proyecto. El elemento no debe eliminarse realmente del disco duro. Cuando un proyecto basado en referencias actúa como destino para una operación de movimiento (o copia), debe agregar una referencia al elemento de origen original sin realizar una copia privada del elemento.

- **Proyecto basado en directorios:** Desde un punto de vista de arrastrar y colocar, el proyecto se arrastra alrededor del elemento físico en lugar de una referencia. Cuando un proyecto basado en directorios actúa como origen para una operación de movimiento, debe terminar eliminando el elemento físico del disco duro, así como quitándolo del proyecto. Cuando un proyecto basado en directorios actúa como destino para una operación de movimiento (o copia), debe realizar una copia del elemento de origen en su ubicación de destino.

- **Proyecto mixto:** Desde un punto de vista de arrastrar y colocar, el comportamiento de este tipo de proyecto se basa en la naturaleza del elemento que se arrastra (ya sea una referencia a un elemento en el almacenamiento o el propio elemento). El comportamiento correcto para las referencias y los elementos físicos se describe anteriormente.

Si solo hubiera un tipo de proyecto en el **Explorador**de soluciones, las operaciones de arrastrar y colocar serían sencillas. Dado que cada sistema de proyecto tiene la capacidad de definir su propio comportamiento de arrastrar y colocar, se deben seguir ciertas directrices (basadas en el comportamiento de arrastrar y colocar del Explorador de Windows) para garantizar una experiencia de usuario predecible:

- Una operación de arrastre sin modificar en el **Explorador** de soluciones (cuando no se mantienen pulsadas las teclas Ctrl ni Mayús) debe dar lugar a una operación de movimiento.

- La operación de arrastrar y mayúsculas también debería dar lugar a una operación de movimiento.

- La operación Ctrl-arrastrar debe dar lugar a una operación de copia.

- Los sistemas de proyectos mixtos y basados en referencias admiten la noción de agregar un vínculo (o referencia) al elemento de origen. Cuando estos proyectos son el destino de una operación de arrastrar y colocar (cuando Ctrl **+ Mayús** se mantiene presionada), debe dar lugar a una referencia al elemento que se agrega al proyecto

No todas las operaciones de arrastrar y colocar son razonables en combinaciones de proyectos basados en referencias, basados en directorios y mixtos. En particular, es problemático pretender permitir una operación de movimiento entre un proyecto de origen basado en directorios y un proyecto de destino basado en referencias porque el proyecto basado en directorios de origen tendrá que eliminar el elemento de origen al finalizar el movimiento. El proyecto basado en referencias de destino terminaría con una referencia a un elemento eliminado.

También es engañoso pretender permitir una operación de copia entre estos tipos de proyectos porque el proyecto basado en referencias de destino no debe hacer una copia independiente del elemento de origen. De forma similar, No se debe permitir que se aplace Ctrl + Mayús a un proyecto de destino basado en directorios porque un proyecto basado en directorios no puede conservar las referencias. En los casos en los que no se admite la operación de arrastrar y colocar, el IDE debe no permitir la colocación y mostrar al usuario el cursor sin colocar (que se muestra en la tabla de punteros siguiente).

Para implementar correctamente el comportamiento de arrastrar y colocar, el proyecto de origen del arrastre debe comunicar su naturaleza al proyecto de destino. (Por ejemplo, ¿está basado en referencias o directorios?) Esta información se indica mediante el formato del portapapeles que ofrece el origen. Como origen de una operación de arrastrar (o `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` copia del portapapeles) un proyecto debe ofrecer uno o respectivamente, dependiendo de si el proyecto está basado en referencias o en directorios. Ambos formatos tienen el mismo contenido de datos, que es similar al formato de `CF_HDROP` Windows,`NULL` excepto que `Projref` las listas de `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` cadenas, en lugar de ser nombres de archivo, son una lista de cadenas de doble terminación (según se devuelva desde o según corresponda).

Como destino de una operación de colocación (o pegar portapapeles), un proyecto debe aceptar ambos `CF_VSREFPROJECTITEMS` y `CF_VSSTGPROJECTITEMS`, aunque el control exacto de la operación de arrastrar y colocar varía en función de la naturaleza del proyecto de destino y el proyecto de origen. El proyecto fuente declara su naturaleza `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS`por si ofrece o . El objetivo de la caída entiende su propia naturaleza y, por lo tanto, tiene suficiente información para tomar decisiones sobre si se debe realizar un movimiento, una copia o un vínculo. El usuario también modifica qué operación de arrastrar y colocar se debe realizar presionando las teclas Ctrl, Mayús o Ctrl y Mayús. Es importante que el destino de colocación indique correctamente `DragEnter` qué `DragOver` operación se realizará con antelación en sus métodos y. El **Explorador** de soluciones sabe automáticamente si el proyecto de origen y el proyecto de destino son el mismo proyecto.

No se admite específicamente arrastrar elementos de proyecto entre instancias de Visual Studio (por ejemplo, de una instancia de devenv.exe a otra). El **Explorador** de soluciones también deshabilita directamente esto.

El usuario siempre debe ser capaz de determinar el efecto de una operación de arrastrar y colocar seleccionando un elemento, arrastrándolo a la ubicación de destino y observando cuál de los siguientes punteros del mouse aparece antes de quitar el elemento:

| Puntero | Get-Help | Descripción |
| :---: | --- | --- |
| ![Icono de mouse "No colocar"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Sin caída | El elemento no se puede quitar en la ubicación especificada. |
| ![Icono de mouse "Copiar"](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copiar | El elemento se copiará en la ubicación de destino. |
| ![Icono de mouse "Mover"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Move | El elemento se moverá a la ubicación de destino. |
| ![Icono de mouse "Agregar referencia"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Agregar referencia | Se agregará una referencia al elemento seleccionado a la ubicación de destino. |

#### <a name="reference-based-projects"></a>Proyectos basados en referencias
 En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como cortar/copiar/pegar) que se deben realizar en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino basados en referencia:

| Modificador | Category | Elemento fuente: Referencia/Enlace | Elemento de origen: Elemento`CF_HDROP`físico o sistema de archivos ( ) |
| --- | --- | --- | --- |
| Sin modificador | Acción | Move | Vínculo |
| Sin modificador | Destino | Añade referencia al elemento original | Añade referencia al elemento original |
| Sin modificador | Source | Elimina la referencia al elemento original | Conserva el artículo original |
| Sin modificador | Resultado | `DROPEFFECT_MOVE`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento |
| Mayús+Arrastrar | Acción | Move | Sin caída |
| Mayús+Arrastrar | Destino | Añade referencia al elemento original | Sin caída |
| Mayús+Arrastrar | Source | Elimina la referencia al elemento original | Sin caída |
| Mayús+Arrastrar | Resultado | `DROPEFFECT_MOVE`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | Sin caída |
| Ctrl+Arrastrar | Acción | Copiar | Sin caída |
| Ctrl+Arrastrar | Destino | Añade referencia al elemento original | Sin caída |
| Ctrl+Arrastrar | Source | Conserva la referencia al artículo original | Sin caída |
| Ctrl+Arrastrar | Resultado | `DROPEFFECT_COPY`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | Sin caída |
| Ctrl+Mayús+Arrastrar | Acción | Vínculo | Vínculo |
| Ctrl+Mayús+Arrastrar | Destino | Añade referencia al elemento original | Añade referencia al elemento original |
| Ctrl+Mayús+Arrastrar | Source | Conserva la referencia al artículo original | Conserva el artículo original |
| Ctrl+Mayús+Arrastrar | Resultado | `DROPEFFECT_LINK`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento |
| Ctrl+Mayús+Arrastrar | Nota: | Igual que el comportamiento de arrastrar y colocar para los accesos directos en el Explorador de Windows. ||
| Cortar/Pegar | Acción | Move | Vínculo |
| Cortar/Pegar | Destino | Añade referencia al elemento original | Añade referencia al elemento original |
| Cortar/Pegar | Source | Conserva la referencia al artículo original|Conserva el artículo original |
| Cortar/Pegar | Resultado | El artículo permanece en la ubicación original en el almacenamiento | El artículo permanece en la ubicación original en el almacenamiento |
| Copiar/Pegar | Acción | Copiar | Vínculo |
| Copiar/Pegar | Source | Añade referencia al elemento original | Añade referencia al elemento original |
| Copiar/Pegar | Resultado | Conserva la referencia al artículo original | Conserva el artículo original |
| Copiar/Pegar | Acción | El artículo permanece en la ubicación original en el almacenamiento | El artículo permanece en la ubicación original en el almacenamiento |

#### <a name="directory-based-projects"></a>Proyectos basados en directorios
En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como cortar/copiar/pegar) que se deben realizar en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para los proyectos de destino basados en directorios:

| Modificador | Category | Elemento fuente: Referencia/Enlace | Elemento de origen: Elemento`CF_HDROP`físico o sistema de archivos ( ) |
|-----------------|----------| - | - |
| Sin modificador | Acción | Move | Move |
| Sin modificador | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Sin modificador | Source | Elimina la referencia al elemento original | Elimina la referencia al elemento original |
| Mayús+Arrastrar | Acción | Move | Move |
| Mayús+Arrastrar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Mayús+Arrastrar | Source | Elimina la referencia al elemento original | Elimina el elemento de la ubicación original |
| Mayús+Arrastrar | Resultado | `DROPEFFECT_MOVE`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_MOVE`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento |
| Ctrl+Arrastrar | Acción | Copiar | Copiar |
| Ctrl+Arrastrar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Ctrl+Arrastrar | Source | Conserva la referencia al artículo original | Conserva la referencia al artículo original |
| Ctrl+Arrastrar | Resultado | `DROPEFFECT_COPY`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_COPY`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento |
| Ctrl+Mayús+Arrastrar | | Sin caída | Sin caída |
| Cortar/Pegar | Acción | Move | Move |
| Cortar/Pegar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Cortar/Pegar | Source | Elimina la referencia al elemento original | Elimina el elemento de la ubicación original |
| Cortar/Pegar | Resultado | El artículo permanece en la ubicación original en el almacenamiento | El artículo se elimina de la ubicación original en el almacenamiento |
| Copiar/Pegar | Acción | Copiar | Copiar |
| Copiar/Pegar | Destino | Añade referencia al elemento original | Copia el elemento en la ubicación de destino |
| Copiar/Pegar | Source | Conserva el artículo original | Conserva el artículo original |
| Copiar/Pegar | Resultado | El artículo permanece en la ubicación original en el almacenamiento | El artículo permanece en el almacenamiento original de ins de ubicación |

#### <a name="mixed-target-projects"></a>Proyectos mixtos
En la tabla siguiente se resumen las operaciones de arrastrar y colocar (así como cortar/copiar/pegar) que se deben realizar en función de la naturaleza del elemento de origen y las teclas modificadoras presionadas para proyectos de destino mixto:

| Modificador | Category | Elemento fuente: Referencia/Enlace | Elemento de origen: Elemento`CF_HDROP`físico o sistema de archivos ( ) |
| --- | --- | --- | --- |
| Sin modificador | Acción | Move | Move |
| Sin modificador | Destino | Añade referencia al elemento original | Copia el elemento en la ubicación de destino |
| Sin modificador | Source | Elimina la referencia al elemento original | Elimina la referencia al elemento original |
| Sin modificador | Resultado | `DROPEFFECT_ MOVE`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE`se devuelve como `::Drop` acción y el elemento se elimina de la ubicación original en el almacenamiento |
| Mayús+Arrastrar | Acción | Move | Move |
| Mayús+Arrastrar | Destino | Añade referencia al elemento original | Copia el elemento en la ubicación de destino |
| Mayús+Arrastrar | Source | Elimina la referencia al elemento original | Elimina el elemento de la ubicación original |
| Mayús+Arrastrar | Resultado | `DROPEFFECT_ MOVE`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE`se devuelve como `::Drop` acción y el elemento se elimina de la ubicación original en el almacenamiento |
| Ctrl+Arrastrar | Acción | Copiar | Copiar |
| Ctrl+Arrastrar | Destino | Añade referencia al elemento original | Copia el elemento en la ubicación de destino |
| Ctrl+Arrastrar | Source | Conserva la referencia al artículo original | Conserva el artículo original |
| Ctrl+Arrastrar | Resultado | `DROPEFFECT_ COPY`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ COPY`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento |
| Ctrl+Mayús+Arrastrar | Acción | Vínculo | Vínculo |
| Ctrl+Mayús+Arrastrar | Destino | Añade referencia al elemento original | Agrega referencia al elemento de origen original |
| Ctrl+Mayús+Arrastrar | Source | Conserva la referencia al artículo original | Conserva el artículo original |
| Ctrl+Mayús+Arrastrar | Resultado | `DROPEFFECT_ LINK`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ LINK`se devuelve como `::Drop` acción y el artículo permanece en la ubicación original en el almacenamiento |
| Cortar/Pegar | Acción | Move | Move |
| Cortar/Pegar | Destino | Copia el elemento en la ubicación de destino | Copia el elemento en la ubicación de destino |
| Cortar/Pegar | Source | Elimina la referencia al elemento original | Elimina el elemento de la ubicación original |
| Cortar/Pegar | Resultado | El artículo permanece en la ubicación original en el almacenamiento | El artículo se elimina de la ubicación original en el almacenamiento |
| Copiar/Pegar | Acción | Copiar | Copiar |
| Copiar/Pegar | Destino | Añade referencia al elemento original | Copia el elemento en la ubicación de destino |
| Copiar/Pegar | Source | Conserva el artículo original | Conserva el artículo original |
| Copiar/Pegar | Resultado | El artículo permanece en la ubicación original en el almacenamiento | El artículo permanece en la ubicación original en el almacenamiento |

Estos detalles deben tenerse en cuenta al implementar el arrastre en el Explorador de **soluciones:**

- Diseño para varios escenarios de selección.

- Los nombres de archivo (ruta de acceso completa) deben ser únicos en todo el proyecto de destino o no se debe permitir la colocación.

- Los nombres de carpeta deben ser únicos (sin distinción entre mayúsculas y minúsculas) en el nivel en el que se quitan.

- Hay diferencias de comportamiento entre los archivos que están abiertos o cerrados en el momento de arrastrar (no se menciona en los escenarios anteriores).

- Los archivos de nivel superior se comportan de forma ligeramente diferente que los archivos de las carpetas.

Otro problema a tener en cuenta es cómo controlar las operaciones de movimiento en elementos que tienen diseñadores o editores abiertos. El comportamiento esperado es el siguiente (esto se aplica a todos los tipos de proyecto):

1. Si el editor/diseñador abierto no tiene ningún cambio no guardado, la ventana del editor/diseñador debe cerrarse silenciosamente.

2. Si el editor/diseñador abierto tiene cambios no guardados, el origen del arrastre debe esperar a que se produzca la colocación y, a continuación, pedir al usuario que guarde los cambios no confirmados en los documentos abiertos antes de cerrar la ventana con un mensaje similar al siguiente:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Esto da al usuario la oportunidad de guardar el trabajo en curso antes de que el destino realice sus copias. Se ha `IVsHierarchyDropDataSource2::OnBeforeDropNotify` agregado un nuevo método para habilitar este control.

A continuación, el destino copiará el estado del elemento tal como está en el almacenamiento (sin incluir los cambios no guardados en el editor si el usuario eligió **No**). Una vez que el destino `IVsHierarchyDropDataSource::Drop`ha completado su copia (en ), el origen tiene `IVsHierarchyDropDataSource::OnDropNotify`la oportunidad de completar la parte de eliminación de la operación de movimiento (en ).

Los editores con cambios no guardados deben dejarse abiertos. Para aquellos documentos con cambios no guardados, esto significa que se realizará la parte de copia de la operación de movimiento, pero se anulará la parte de eliminación. En un escenario de selección múltiple cuando el usuario elige **No**, los documentos con cambios no guardados no deben cerrarse ni quitarse, pero los que no tienen cambios no guardados deben cerrarse y quitarse.
