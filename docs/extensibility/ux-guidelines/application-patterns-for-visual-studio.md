---
title: Patrones de aplicación para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0bd7ad3434f854a66ce3cd966afbaf25c089efc8
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513392"
---
# <a name="application-patterns-for-visual-studio"></a>Patrones de aplicación para Visual Studio
##  <a name="BKMK_WindowInteractions"></a> Interacciones de ventana  
  
### <a name="overview"></a>Información general  
Los dos tipos de ventana principal que se usan en Visual Studio son editores de documentos y ventanas de herramientas. Raras, pero es posible, es grandes cuadros de diálogo no modales. Aunque estos son todos no modales en el shell, sus patrones son fundamentalmente distintas. Esta sección trata la diferencia entre las ventanas de documento, las ventanas de herramientas y cuadros de diálogo no modales. Patrones de cuadro de diálogo modal se tratan en [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Comparación de patrones de uso de la ventana  
**Las ventanas de documento** casi siempre se muestran también en el documento. Esto proporciona el editor del documento "fase center" para organizar las ventanas de herramienta complementaria alrededor.  
  
Un **ventana de herramientas** más a menudo se muestra como una ventana independiente, menor contraída en el borde del IDE. Esto puede ser visible, oculto u ocultación automática. Sin embargo, en ocasiones, se presentan las ventanas de herramientas dentro del documento bien, para ello, desactive la **ventana/acoplamiento** propiedad en la ventana. Esto da como resultado más realistas, pero también decisión de diseño común: cuando se intenta integrar en Visual Studio, debe decidir si la característica debe mostrar una ventana de herramientas o una ventana de documento.  
  
**Los cuadros de diálogo no modales** se desaconseja en Visual Studio. Los cuadros de diálogo no modales más son, por definición, las ventanas de herramientas flotantes y deben implementarse de este modo. Los cuadros de diálogo no modales se permiten en los casos donde el tamaño de una ventana de herramientas normal Anclar al lado del shell podría ser demasiado limitado. También se permiten en los casos donde el usuario es probable que mover el cuadro de diálogo a un monitor secundario.  
  
Cree cuidadosamente sobre qué tipo de contenedor que necesita. Consideraciones de patrón de uso común para el diseño de interfaz de usuario están en la tabla siguiente.  
  
||Ventana de documento|Ventana de herramientas|Cuadro de diálogo no modal|  
|-|---------------------|-----------------|---------------------|  
| **Posición** | Siempre colocan bien dentro del documento y no acoplar alrededor de los bordes del IDE. Se puede "extraer" para que flote por separado desde el shell principal. | Acopla pestaña generalmente alrededor de los bordes del IDE, pero pueden ser personalizadas que flota y oculta automáticamente (desanclado) o acoplar dentro del documento también.|Ventana flotante grande independiente desde el IDE. |  
| **Confirmar el modelo** | *Confirmación retardada*<br /><br /> Para guardar los datos en un documento, el usuario debe emitir el **archivo &gt; guardar**, **Guardar como**, o **guardar todo** comando. Una ventana de documento tiene el concepto de los datos que contiene "sucia", a continuación, se compromete a uno de la operación de guardar los comandos. Al cerrar una ventana de documento, todo el contenido guardado en el disco o perdido. | *Confirmación inmediata*<br /><br /> No hay ningún Guardar modelo. Para las ventanas de herramientas del inspector que asisten en la edición de un archivo, el archivo debe estar abierto en el editor o diseñador activo y el diseñador o editor posee la operación de guardar. | *Confirmación demorada o inmediata*<br /><br /> A menudo, un cuadro de diálogo no modal grande requiere una acción para confirmar los cambios y permite una operación "Cancelar", que se reviertan los cambios realizados en la sesión de diálogo.  Esto diferencia un cuadro de diálogo no modal de una ventana de herramientas en que las ventanas de herramientas siempre tienen un modelo de confirmación inmediata. |  
| **Visibilidad** | *Abrir/crear (archivo) y cierre*<br /><br /> Abrir una base de datos de windows se realiza a través de abrir un documento existente o mediante una plantilla para crear un nuevo documento. No hay ningún "abrir \<específica del editor >" comando. | *Ocultar y mostrar*<br /><br /> Ventanas de herramientas de instancia única se pueden ocultas o se muestra. Si en la vista se conservan contenido y los Estados dentro de la ventana de herramientas u oculto. Ventanas de herramientas de varias instancias pueden estar cerradas así como ocultadas. Cuando se cierra una ventana de herramientas de instancias múltiples, se descarta el contenido y el estado dentro de la ventana de herramientas. | *Iniciar desde un comando*<br /><br /> Los cuadros de diálogo se inician desde un comando basado en tareas. |  
| **Instancias** | *Instancias múltiples*<br /><br /> Varios editores pueden estar abiertos al mismo tiempo y edición de archivos diferentes, mientras que algunos editores también permiten el mismo archivo esté abierto en más de un editor (mediante la **ventana &gt; nueva ventana** comando).<br /><br /> Un único editor puede estar editando uno o varios archivos al mismo tiempo (Diseñador de proyectos). | *Única o varias instancias*<br /><br /> Contenido cambia para reflejar el contexto (como se muestra en el Explorador de propiedades) o el foco y contexto de inserción a otras ventanas (lista de tareas, el Explorador de soluciones).<br /><br /> Instancia única e instancias múltiples ventanas de herramientas se deben asociadas con la ventana de documento activo a menos que haya una razón de peso no a. | *Instancia única* |  
| **Ejemplos** | **Editores de texto**, al igual que el editor de código<br /><br /> **Superficies de diseño**, como un diseñador de formularios o una superficie de modelado<br /><br /> **Controlar los diseños similares a los cuadros de diálogo**, al igual que el Diseñador de manifiestos | El **el Explorador de soluciones** proporciona una solución y proyectos dentro de la solución<br /><br /> El **Explorador de servidores** proporciona una vista jerárquica de los servidores y conexiones de datos que el usuario elige abrir en la ventana. Abrir un objeto de la jerarquía de la base de datos, como una consulta, abre una ventana de documento y permite al usuario editar la consulta.<br /><br /> El **Examinador de propiedades** muestra las propiedades para el objeto seleccionado en una ventana de documento o en otra ventana de herramientas. Las propiedades se presentan en una vista jerárquica de cuadrícula o en los controles de cuadro de diálogo similar a complejos y permitir que el usuario establecer los valores de esas propiedades. | |  
  
##  <a name="BKMK_ToolWindows"></a> Ventanas de herramientas  
  
### <a name="overview"></a>Información general  
Ventanas de herramientas admiten el trabajo del usuario que se produce en las ventanas de documento. Se puede usar para mostrar una jerarquía que representa un objeto raíz fundamentales que proporciona Visual Studio y que puede manipular.  
  
Al considerar una nueva ventana de herramientas en el IDE, los autores deben:  
  
-   Usar ventanas de herramientas existente adecuado para la tarea y no crear nuevos con una funcionalidad similar. Solo se deben crear nuevas ventanas de herramientas si ofrecen una "herramienta" significativamente diferente o funcionalidad que no se puede integrar en una ventana similar o convirtiendo una ventana existente en un centro de dinamización.  
  
-   Use una barra de comandos estándar, si es necesario, en la parte superior de la ventana de herramientas.  
  
-   Ser coherente con los modelos ya está presentes en otras ventanas de herramientas para la navegación de presentación y el teclado de control.  
  
-   Ser coherente con la presentación del control en otras ventanas de herramientas.  
  
-   Asegúrese de ventanas de herramientas específica del documento visibles automáticamente cuando sea posible, para que aparezcan solo cuando se activa el documento primario.  
  
-   Asegúrese de que su contenido de la ventana es navegable mediante el teclado (teclas de dirección de soporte técnico).  
  
#### <a name="tool-window-states"></a>Estados de la ventana de herramienta  
Ventanas de herramientas de Visual Studio tienen distintos Estados, algunos de los cuales están activados en el usuario (por ejemplo, la característica Ocultar automáticamente). Otros Estados, como visibles automáticamente, que permita las ventanas de herramienta que aparezcan en el contexto correcto y ocultar cuando no sea necesario. Hay cinco estados de la ventana de herramienta en total.  
  
-   **Acoplar o anclado** ventanas de herramientas se pueden conectar a cualquiera de los cuatro lados del área del documento. Aparece el icono de alfiler en la barra de título de ventana de herramientas. La ventana de herramientas se puede acoplar horizontal o verticalmente a lo largo del borde de la shell y otras ventanas de herramientas y también se pueden vincular mediante pestañas.  
  
-   **Oculta automáticamente** se desanclan ventanas de herramientas. La ventana puede deslizarse fuera de la vista, dejando una pestaña (con el nombre de la ventana de herramientas y en el icono) en el borde del área del documento. La ventana de herramientas se desliza cuando un usuario se desplaza a través de la pestaña.  
  
-   **Visibles automáticamente** ventanas de herramientas aparecen automáticamente cuando se inicia otra parte de la interfaz de usuario, como un editor, o recibe el foco.  
  
-   **Flotante** ventanas de herramientas mantenga el mouse fuera del IDE. Esto es útil para las configuraciones de varios monitores.  
  
-   **Documento con pestañas** ventanas de herramientas se pueden acoplar dentro del documento también. Esto es útil para grandes ventanas de herramientas, como el Examinador de objetos, que se necesita más espacio que permite a los bordes del marco de acoplamiento.  
  
![Herramienta de Estados de la ventana en Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 01_ToolWindowStates")<br />Estados de la ventana de herramientas en Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Instancia única e instancias múltiples  
Ventanas de herramientas son la única instancia o instancias múltiples. Algunas ventanas de herramientas de instancia única podrían estar asociados con la ventana de documento activo, mientras que las ventanas de herramientas de varias instancias, es posible que no. Ventanas de herramientas de instancias múltiples responden a la **ventana &gt; nueva ventana** comando mediante la creación de una nueva instancia de la ventana. La siguiente imagen ilustra una ventana de herramienta que permite el comando nueva ventana cuando se activa una instancia de la ventana:  
  
![Habilitar comando de "Nueva ventana" cuando una instancia de la ventana de ventana de herramientas está activa](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")<br />Habilitar comando de "Nueva ventana" cuando se activa una instancia de la ventana de ventana de herramientas  
  
Ventanas de herramientas de instancia única se pueden ocultas o muestran, mientras que ventanas de herramientas de varias instancias pueden cerradas, así como ocultadas. Pueden acoplar todas las ventanas de herramientas, establezca como una ventana secundaria de interfaz de múltiples documentos (MDI) (similar a una ventana de documento), flotante o vinculada por ficha. Todas las ventanas de herramientas deben responder a los comandos de administración de la ventana correspondiente en el menú Ventana:  
  
![Comandos de administración de la ventana en el menú de la ventana de Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 03_WindowManagementControls")<br />Comandos de administración de la ventana en el menú de la ventana de Visual Studio
  
#### <a name="document-specific-tool-windows"></a>Ventanas de herramientas específica del documento  
Algunas ventanas de herramientas están diseñadas para cambiar en función de un determinado tipo de documento. Estas ventanas continuamente se actualizan para reflejar funciones aplicables a la ventana de documento activo en el IDE.  
  
Ejemplos de ventanas de herramientas cuyo contenido cambia para reflejar el editor seleccionado son el cuadro de herramientas y el esquema del documento. Estas ventanas muestran una marca de agua cuando un editor tiene el foco que no ofrece el contexto de la ventana.  
  
#### <a name="navigable-list-tool-windows"></a>Ventanas de herramientas de lista navegable  
Algunas ventanas de herramientas muestran una lista de elementos navegables, con que el usuario puede interactuar. En este tipo de ventana, siempre debe haber comentarios para el elemento actual en la lista, incluso si la ventana está inactiva. La lista debe responder a la **GoToNextLocation** y **GoToPrevLocation** comandos, cambie también el elemento actualmente seleccionado en la ventana  
  
Ejemplos de ventanas de herramientas de lista navegable son el Explorador de soluciones y la ventana de resultados de la búsqueda.  
  
### <a name="tool-window-types"></a>Tipos de ventana de herramientas  
  
#### <a name="common-tool-windows-and-their-functions"></a>Ventanas de herramientas comunes y sus funciones

**Ventanas de herramientas jerárquicas**
| Ventana de herramientas | Función | 
| --- | --- | 
| Explorador de soluciones | Un árbol jerárquico que muestra una lista de los documentos contenidos en elementos de la solución, proyectos y archivos varios. La visualización de los elementos dentro de los proyectos se define mediante el paquete al que pertenece el tipo de proyecto (por ejemplo, los tipos de basada en referencias, basado en el directorio o en modo mixto). | 
| Vista de clases | Un árbol jerárquico de las clases y los diversos elementos del conjunto de trabajo de documentos, independientemente de los propios archivos. | 
| Explorador de servidores | Un árbol jerárquico que muestra todas las conexiones de datos y servidores de la solución. | 
| Esquema del documento | La estructura jerárquica del documento activo. | 

**Ventanas de herramientas de cuadrícula**
| Ventana de herramientas | Función | 
| --- | --- | 
| Propiedades | Una cuadrícula que muestra una lista de propiedades para el objeto seleccionado, junto con los selectores de valor pueden editar dichas propiedades. | 
| Lista de tareas | Una cuadrícula que permite al usuario crear, editar o eliminar tareas y los comentarios. | 

**Ventanas de herramientas de contenido**
| Ventana de herramientas | Función | 
| --- | --- | 
| Ayuda | Una ventana que permite a los usuarios acceso a los distintos métodos de obtención de Ayuda de "¿cómo?" vídeos a los foros MSDN. | 
| Ayuda dinámica | Una ventana de herramientas que muestra vínculos a temas que se aplica a la selección actual de ayuda. | 
| Examinador de objetos | Un conjunto de marcos de dos columnas con una lista de componentes de objetos jerárquico en el panel izquierdo y el objeto propiedades y métodos en la columna derecha. | 

**Ventanas de herramientas del cuadro de diálogo**
| Ventana de herramientas | Función | 
| --- | --- | 
| Find | Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución. |
| Búsqueda avanzada | Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución. | 

**Otras ventanas de herramientas**
| Ventana de herramientas | Función | 
| --- | --- | 
| Cuadro de herramientas | La ventana de herramientas que se utiliza para almacenar los elementos que se van a quitar en superficies de diseño, que proporciona un origen de arrastre coherente para todos los diseñadores. |
| Página de inicio | El portal del usuario a Visual Studio, con acceso a las fuentes de noticias para desarrolladores, la Ayuda de Visual Studio y proyectos recientes. Los usuarios también pueden crear páginas de inicio personalizada copiando el archivo StartPage.xaml desde el "Common7\IDE\StartPages\" directorio y, a continuación, edite el XAML documenta directorio de archivos de programa de Visual Studio a la carpeta StartPages en Visual Studio a mano o ábralo en Visual Studio u otro editor de código. | 

**Ventanas de herramientas del depurador**
| Ventana de herramientas | Función | 
| --- | --- |
| Automático ||  
| Inmediato ||  
| Salida | La ventana de salida puede usarse siempre que tenga eventos textuales o estado para declarar. |  
| Memoria ||  
| Puntos de interrupción ||  
| En ejecución ||  
| Documentos ||  
| Pila de llamadas ||  
| Locals ||  
| Inspecciones ||  
| Desensamblado ||  
| Registros ||  
| Subprocesos ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a> Convenciones del editor de documentos  
  
### <a name="document-interactions"></a>Interacciones de objetos de documento  
"Bien document" es el mayor espacio en el IDE y es donde el usuario generalmente centra su atención para completar sus tareas, asistidas por las ventanas de herramientas adicionales. Editores de documentos representan las unidades fundamentales de trabajo que el usuario abre y se guarda dentro de Visual Studio. Conservan un sentido fuerte de selección asociada al explorador de soluciones o en otras ventanas de la jerarquía activa. El usuario debería poder para que apunte a una de estas ventanas de la jerarquía y saber dónde se encuentra el documento y su relación para la solución, proyecto u otro objeto raíz proporcionado por un paquete de Visual Studio.  
  
Edición de documentos, requiere una experiencia de usuario coherente. Para permitir al usuario centrarse en la tarea en cuestión en lugar de en la administración de ventanas y buscar comandos, seleccione una estrategia de vista de documento que mejor se adapte a las tareas de usuario para la edición de ese tipo de documento.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interacciones habituales para el cuadro de documento  
  
-   Mantener un modelo de interacción coherente en el común **nuevo archivo** y **abrir archivo** experiencias.  
  
-   Actualizar la funcionalidad relacionada en los menús y ventanas relacionadas cuando se abre la ventana de documento.  
  
-   Comandos de menú se integran correctamente en menús más comunes, como **editar**, **formato**, y **vista** menús. Si hay una cantidad considerable de los comandos especializadas, a continuación, se puede crear un nuevo menú. Este nuevo menú debe aparecer solo cuando el documento tiene el foco.  
  
-   En la parte superior del editor se puede colocar una barra de herramientas incrustada. Esto es preferible a tener una barra de herramientas independiente que aparece fuera del editor.  
  
-   Siempre mantienen una selección en el Explorador de soluciones o similar active ventana de jerarquía.  
  
-   Haga doble clic en un documento en el Explorador de soluciones debe realizar la misma acción que **abierto**.  
  
-   Si más de un editor puede usarse en un tipo de documento, el usuario debería poder invalidar o restablecer la acción predeterminada en un tipo de documento determinado mediante la **abrir con** cuadro de diálogo con el botón secundario en el archivo y seleccionando **abierto Con** en el menú contextual.  
  
-   No cree a un asistente en un documento bien.  
  
### <a name="user-expectations-for-specific-document-types"></a>Expectativas del usuario para los tipos de documento específico  
Hay varios tipos básicos distintos de los editores de documento y cada uno tiene un conjunto de interacciones que sean coherentes con otras personas del mismo tipo.  
  
-   **Editor de texto:** editor de código, archivos de registro  
  
-   **Superficie de diseño:** WPF diseñador, Windows forms de  
  
-   **Editor de estilo de cuadro de diálogo:** Diseñador de manifiestos, las propiedades del proyecto  
  
-   **Diseñador de modelos:** Diseñador de flujo de trabajo, codemap, diagrama de arquitectura, progresión  
  
También hay varios tipos de no editor que use también el documento. Mientras no edita documentos en Sí, es necesario seguir interacciones estándar para las ventanas de documento.  
  
-   **Informes:** informar de IntelliTrace, el informe de Hyper-V, informe del generador de perfiles  
  
-   **Panel:** concentrador de diagnósticos  
  
#### <a name="text-based-editors"></a>Editores de texto  
  
-   El documento participa en el modelo de pestaña de vista previa, lo que permite obtener una vista previa del documento sin necesidad de abrirlo.  
  
-   La estructura del documento se puede representar dentro de una ventana de herramientas complementarias, por ejemplo, un esquema de documento.  
  
-   IntelliSense (si procede) se comportará de forma coherente con otros editores de código.  
  
-   Los elementos emergentes o la interfaz de usuario asistencia siga estilos y patrones similares para la interfaz de usuario similar existente, por ejemplo, CodeLens.  
  
-   Le mostrará mensajes relacionados con el estado del documento en un control de barra de información en la parte superior del documento o en la barra de estado.  
  
-   El usuario debe poder personalizar la apariencia de las fuentes y colores mediante una **Herramientas > opciones** página, la página fuentes y colores compartida o una específica para el editor.  
  
#### <a name="design-surfaces"></a>Superficies de diseño  
  
-   Un diseñador vacío debe tener una marca de agua en la superficie que indica cómo empezar a trabajar.  
  
-   Cambiar de vista mecanismos siguen patrones existentes, por ejemplo, haga doble clic para abrir un editor de código o tabulaciones en la ventana de documento, lo que permite la interacción con los paneles.  
  
-   Agregar elementos a la superficie de diseño debe realizarse mediante el cuadro de herramientas, a menos que se requiere una ventana de herramientas muy específicos.  
  
-   Los elementos en la superficie siguen un modelo coherente de selección.  
  
-   Las barras de herramientas incrustadas contienen comandos únicamente, no es común de comandos específicos del documento como **guardar**.  
  
#### <a name="dialog-style-editors"></a>Editores de estilo de cuadro de diálogo  
  
-   Diseño de controles debe seguir las convenciones de diseño de cuadro de diálogo normal.  
  
-   Las pestañas en el editor no deberían coincidir con la apariencia de las pestañas del documento, debe coincidir con uno de los dos estilos de pestaña interiores permitidos.  
  
-   Los usuarios deben poder interactuar con los controles mediante el teclado solo; ya sea mediante el editor de activación y tabulación a través de los controles o mediante el uso de las teclas de acceso estándar.  
  
-   El diseñador debe utilizar Guardar modelo común. No guardar general o los botones de la confirmación deben colocarse en la superficie, aunque otros botones pueden ser apropiados.  
  
#### <a name="model-designers"></a>Diseñadores de modelos  
  
-   Un diseñador vacío debe tener una marca de agua en la superficie que indica cómo empezar a trabajar.  
  
-   Agregar elementos a la superficie de diseño debe realizarse mediante el cuadro de herramientas.  
  
-   Los elementos en la superficie siguen un modelo coherente de selección.  
  
-   Las barras de herramientas incrustadas contienen comandos únicamente, no es común de comandos específicos del documento como **guardar**.  
  
-   Una leyenda puede aparecer en la superficie, indicativa o una marca de agua.  
  
-   El usuario debe poder personalizar la apariencia de las fuentes o colores con una **Herramientas > opciones** página, la página fuentes y colores compartida o una específica para el editor.  
  
#### <a name="reports"></a>Informes  
  
-   Los informes son normalmente solo información y no participan en el modelo de guardar. Sin embargo, pueden incluir una interacción como vínculos a otra información pertinente o expandir y contraer secciones.  
  
-   En la superficie de la mayoría de los comandos debe ser hipervínculos, botones no.  
  
-   Diseño debe incluir un encabezado y siga las instrucciones de diseño de informe estándar.  
  
#### <a name="dashboards"></a>Paneles  
  
-   Los paneles no tienen un modelo de interacción a sí mismos, pero servir como un medio para ofrecen una variedad de otras herramientas.  
  
-   No participan en el modelo de guardar.  
  
-   Los usuarios deben poder interactuar con los controles mediante el teclado, activando el editor y desplazarse a través de los controles o mediante el uso de las teclas de acceso estándar.  
  
##  <a name="BKMK_Dialogs"></a> Cuadros de diálogo  
  
### <a name="introduction"></a>Introducción  
Cuadros de diálogo en Visual Studio normalmente deben admitir una unidad discreta de trabajo del usuario y, a continuación, se puede descartadas.  
  
Si ha determinado que necesita un cuadro de diálogo, tiene tres opciones, en orden de preferencia:  
  
1.  Integrar características en uno de los cuadros de diálogo compartidos en Visual Studio.  
  
2.  Cree su propio cuadro de diálogo con un patrón que se encuentra en un cuadro de diálogo similar existente.  
  
3.  Cree un nuevo cuadro de diálogo, la interacción siguiente y directrices de diseño.  
  
En esta sección se describe cómo elegir el patrón de cuadro de diálogo correcto dentro de los flujos de trabajo de Visual Studio y las convenciones comunes para el diseño del cuadro de diálogo.  
  
### <a name="themes"></a>Temas  
Cuadros de diálogo en Visual Studio siguen uno de los dos estilos básicos:  
  
#### <a name="standard-unthemed"></a>Estándar (unthemed)  
La mayoría de los cuadros de diálogo son los cuadros de diálogo utilidad estándar y debe ser unthemed. No no controles comunes de re-template ni intentar crear botones "modernos" estilizados o controles. Los controles y la apariencia de chrome siga [las directrices de interacción de escritorio de Windows estándar para cuadros de diálogo](/windows/desktop/uxguide/win-dialog-box).  
  
#### <a name="themed"></a>Con temas  
Cuadros de diálogo de Especialidad "firma" pueden ser temáticas. Los cuadros de diálogo con temas tienen una apariencia diferente, que también tiene algunos patrones de interacción especiales asociados con el estilo. Tema de su cuadro de diálogo si cumple estos requisitos:  
  
-   El cuadro de diálogo es una experiencia común que se ven y se usará con frecuencia o muchos usuarios (por ejemplo, el **nuevo proyecto** cuadro de diálogo.  
  
-   El cuadro de diálogo contiene los elementos de la marca de producto prominente (por ejemplo, el **configuración de la cuenta** cuadro de diálogo).  
  
-   El cuadro de diálogo aparece como una parte integral de un flujo mayor que incluye otros cuadros de diálogo con temas (por ejemplo, el **Agregar servicio conectado** cuadro de diálogo).  
  
-   El cuadro de diálogo es una parte importante de una experiencia que desempeña un papel estratégico en promocionar o diferenciar una versión del producto.  
  
Al crear un cuadro de diálogo con temas, use los colores de entorno adecuadas y siga el diseño correcto y patrones de interacción. (Consulte [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Diseño del cuadro de diálogo  
Los cuadros de diálogo bien diseñadas tendrá los siguientes elementos en consideración:  
  
-   La tarea de usuario que se admita  
  
-   El estilo de texto del cuadro de diálogo, el idioma y la terminología  
  
-   Opciones de control y las convenciones de la interfaz de usuario  
  
-   Alineación de especificación y control de diseño Visual  
  
-   Acceso mediante el teclado  
  
#### <a name="content-organization"></a>Organización de contenido  
Tenga en cuenta las diferencias entre estos tipos básicos de los cuadros de diálogo:  
  
-   [Los cuadros de diálogo simple](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentar los controles en una sola ventana modal. La presentación es posible que incluyen las variaciones de patrones de control complejo, incluyendo un selector de campo o una barra de iconos.  
  
-   [En capas los cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) sirven para aprovechar al máximo de espacio en pantalla cuando un único fragmento de la interfaz de usuario consta de varios grupos de controles. Agrupaciones del cuadro de diálogo son "capas" a través de los botones, controles de lista de navegación o controles de ficha para que el usuario puede elegir que la agrupación para ver en cualquier momento determinado.  
  
-   [Asistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) son útiles para dirigir al usuario a través de una secuencia de pasos hacia la finalización de una tarea lógica. Se ofrecen una serie de opciones en los paneles secuenciales, en ocasiones, introducción a diferentes flujos de trabajo ("ramas") depende de una selección realizada en el panel anterior.  
  
####  <a name="BKMK_SimpleDialogs"></a> Cuadros de diálogo simple  
Un cuadro de diálogo simple es una presentación de controles en una sola ventana modal. Esta presentación es posible que incluyen las variaciones de patrones de control complejo, como un selector de campo. Para los cuadros de diálogo simple, siga el diseño general estándar, así como cualquier diseño específico necesario para las agrupaciones de control complejo.
  
![> Crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 01_CreateStrongNameKey")<br />Crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a> Cuadros de diálogo en capas  
Los cuadros de diálogo con capas incluyen fichas, paneles y los árboles incrustados. Se utilizan para maximizar el espacio cuando hay varios grupos de controles que se ofrecen en una única parte de la interfaz de usuario. Las agrupaciones se superponen para que el usuario puede elegir que la agrupación para ver en cualquier momento.  
  
En el caso más sencillo, el mecanismo para cambiar entre las agrupaciones es un control de ficha. Hay varias alternativas. Consulte dar prioridad a y disposición en capas para saber cómo elegir el estilo más adecuado.  
  
El **herramientas &gt; opciones** cuadro de diálogo es un ejemplo de un cuadro de diálogo con capas mediante un árbol incrustado:  
  
![Herramientas > opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 02_ToolsOptions")<br />Herramientas > opciones es un ejemplo de un cuadro de diálogo en capas en Visual Studio.
  
####  <a name="BKMK_Wizards"></a> Asistentes  
Los asistentes son útiles para dirigir al usuario a través de una secuencia lógica de pasos en la finalización de una tarea. Se ofrecen una serie de opciones en los paneles secuenciales, y el usuario debe seguir cada paso antes de continuar al siguiente. Una vez que están disponibles, los valores predeterminados de suficientes la **finalizar** botón está habilitado.  
  
 Modales asistentes se utilizan para las tareas que:  
  
-   Contienen la bifurcación, que se ofrecen diferentes rutas de acceso según las opciones del usuario  
  
-   Contiene las dependencias entre los pasos, donde los pasos siguientes dependen de entrada del usuario en los pasos anteriores  
  
-   Son bastante complejas que se debe usar la interfaz de usuario para explicar las opciones y los posibles resultados en cada paso  
  
-   Son transaccionales, que requieren un conjunto de pasos para completarse en su totalidad antes de confirmados los cambios  
  
### <a name="common-conventions"></a>Convenciones comunes  
Para lograr un diseño óptimo y funcionalidad con los cuadros de diálogo, siga estas convenciones en el tamaño del cuadro de diálogo, posición, estándares, configuración de control y alineación, la interfaz de usuario texto, barras de título, botones de control y las claves de acceso.  
  
Para obtener instrucciones específicas del diseño, vea [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Tamaño  
Cuadros de diálogo deben ajustarse a una resolución mínima de pantalla de 1024 x 768, y el tamaño inicial del cuadro de diálogo no debe superar los 900 x 700 píxeles. Los cuadros de diálogo pueden ser de tamaño variable, pero no es un requisito.  
  
Hay dos recomendaciones para los diálogos redimensionables:  
  
1.  Que está definido para el cuadro de diálogo que se optimizará para el control de un tamaño mínimo establecido sin recortes y se ajusta para adaptarse al crecimiento de localización razonable.  
  
2.  Que el tamaño de la escala del usuario se conserve entre sesiones. Por ejemplo, si el usuario escala a un cuadro de diálogo al 150%, se mostrará un inicio posterior del cuadro de diálogo al 150%.  
  
#### <a name="position"></a>Posición  
Los cuadros de diálogo deben aparecer centrados en el IDE de iniciarse por primera vez. La última posición de los cuadros de diálogo invariable no necesita conservar, por lo que aparecen centrados en los lanzamientos posteriores. 

Para los cuadros de diálogo puede cambiar el tamaño, el tamaño debe conservarse en lanzamientos posteriores. Para los cuadros de diálogo modales puede cambiar el tamaño, la posición no deba conservarse. Mostrarlos centrado en el IDE evita la posibilidad de que el cuadro de diálogo que aparece en una posición impredecible o inutilizable cuando ha cambiado la configuración de pantalla del usuario. 

Cuadros de diálogo no modales que se pueden mover, la posición del usuario debe mantenerse en lanzamientos subsiguientes, el cuadro de diálogo puede utilizarse con frecuencia como una parte integral de un flujo de trabajo más grande.  
  
Cuando los cuadros de diálogo deben generar otros cuadros de diálogo, debe actuar en cascada en el cuadro de diálogo superior a la derecha y hacia abajo desde el elemento primario para que resulte evidente para el usuario que ha navegado a un nuevo lugar.  
  
#### <a name="modality"></a>Modalidad  
Modal que se va a significa que los usuarios son necesarios para completar o cancelar el cuadro de diálogo antes de continuar. Puesto que los cuadros de diálogo modales bloquear al usuario interactuar con otras partes del entorno, flujo de tareas de la característica debe usarlos como con moderación como sea posible. Cuando una operación modal es necesaria, Visual Studio tiene una serie de cuadros de diálogo compartidos en que puede integrar características. Si tiene que crear un nuevo cuadro de diálogo, siga el patrón de interacción de un cuadro de diálogo existente con una funcionalidad similar.  
  
Cuando los usuarios necesitan realizar actividades de dos a la vez, como **buscar** y **reemplazar** al escribir código nuevo, el cuadro de diálogo debe ser no modal para que el usuario puede cambiar fácilmente entre ellos. Por lo general, Visual Studio usa las ventanas de herramientas para este tipo de compatibilidad con el editor de la tarea vinculada.  
  
#### <a name="control-configuration"></a>Configuración de control  
Ser coherente con las configuraciones de control existentes que consiguen lo mismo en Visual Studio.  
  
#### <a name="title-bars"></a>Barras de título  
  
-   El texto en la barra de título debe reflejar el nombre del comando que se inició.  
  
-   Icono no debe usarse en las barras de título del cuadro de diálogo. En los casos donde el sistema requiere uno, use el logotipo de Visual Studio.  
  
-   Los cuadros de diálogo no debe minimizar o maximizar los botones.  
  
-   Botones de ayuda en la barra de título han quedado desusados. No se agregan a los cuadros de diálogo nuevo. Cuando existen, debe iniciar un tema de ayuda es conceptualmente relevante para la tarea.  
  
 ![Especificaciones de directrices para las barras de título en los cuadros de diálogo de Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 03_TitleBarSpecs")<br />Especificaciones de directrices para las barras de título en los cuadros de diálogo de Visual Studio
  
#### <a name="control-buttons"></a>Botones de control  
En general, **Aceptar**, **cancelar**, y **ayuda** se deben organizar botones horizontalmente en la esquina inferior derecha del cuadro de diálogo. Si un cuadro de diálogo tiene varios otros botones en la parte inferior del cuadro de diálogo que presentaría visual confusión con los botones de control, se permite la pila vertical alternativa.  
  
![Configuraciones aceptables para los botones de control en los cuadros de diálogo de Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 04_ControlButtonConfig")<br />Configuraciones aceptables para los botones de control en los cuadros de diálogo de Visual Studio
  
El cuadro de diálogo debe incluir un botón de control predeterminado. Para determinar el mejor comando que se usará como el valor predeterminado, elija entre las siguientes opciones (que se muestran en orden de prioridad):  
  
-   Elija el comando más seguro y más seguro como el valor predeterminado. Esto significa que se elige el comando más probable evitar la pérdida de datos y evitar el acceso al sistema no deseados.  
  
-   Si la seguridad y pérdida de datos no son factores, a continuación, elija el comando predeterminado en función de comodidad. Incluido el comando como el valor predeterminado es más probable que mejorará el flujo de trabajo del usuario cuando el cuadro de diálogo admite tareas repetitivas o frecuentes.  
  
Evite elegir una acción destructiva permanentemente para el comando predeterminado. Si hay un comando de ese tipo, elija un comando más seguro en su lugar, como el valor predeterminado.  
  
#### <a name="access-keys"></a>Teclas de acceso  
No utilice las teclas de acceso para **Aceptar**, **cancelar**, o **ayuda** botones. Estos botones se asignan a teclas de método abreviado de forma predeterminada:  
  
| Nombre del botón | Método abreviado de teclado |  
| --- | --- |  
| Aceptar | Entrar |  
| Cancelar | Esc |  
| Ayuda | F1 |  
  
#### <a name="imagery"></a>Imágenes  
Usar imágenes con moderación en los cuadros de diálogo. No utilizar iconos grandes en los cuadros de diálogo simplemente para usar un espacio. Usar imágenes solo si son una parte importante de transmitir el mensaje al usuario, como iconos de advertencia o animaciones de estado.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a> Establecer prioridades y la creación de capas  
  
#### <a name="prioritizing-your-ui"></a>Dar prioridad a la interfaz de usuario  
Podría ser necesaria Traer determinados elementos de interfaz de usuario a la vanguardia y coloque un comportamiento más avanzado y opciones (incluidos los comandos oscuros) en los cuadros de diálogo. Incorpore la funcionalidad frecuente a la vanguardia dejar lugar para ella y hacerlo visible de forma predeterminada en la interfaz de usuario con una etiqueta de texto cuando se muestra el cuadro de diálogo.  
  
#### <a name="layering-your-ui"></a>La interfaz de usuario de la creación de capas  
Si ha determinado que es necesario un cuadro de diálogo, pero la funcionalidad relacionada que desee para presentar al usuario que se va más allá de lo que se pueden mostrar en un cuadro de diálogo simple, necesita la interfaz de usuario de la capa. Visual Studio usa los métodos de distribución en capas más comunes son las pestañas y vestíbulos o paneles. En algunos casos, las regiones que se pueden expandir y contraer podrían ser adecuadas. UI adaptable por lo general no se recomienda en Visual Studio.  
  
Hay ventajas e inconvenientes a diferentes métodos de creación por capas de interfaz de usuario a través de los controles de ficha similares. Revise la lista siguiente para asegurarse de que ha elegido una técnica de distribución en capas que se ajuste a su situación.  
  
##### <a name="tabbing"></a>Tabulación  
  
| Mecanismo de conmutación | Ventajas y el uso apropiado | Uso inadecuado y desventajas |  
| --- | --- | --- |  
| Control Tab | Agrupar lógicamente las páginas del cuadro de diálogo en conjuntos relacionados<br /><br />Útil para menos de cinco (o el número de fichas que caben en una fila en el cuadro de diálogo) las páginas de controles relacionados en el cuadro de diálogo<br /><br />Pestaña etiquetas deben ser corto: una o dos palabras que se puedan identificar fácilmente el contenido<br /><br />Un estilo de cuadro de diálogo comunes del sistema<br /><br />Ejemplo: **Explorador de archivos &gt; propiedades de los elementos** | Hacer etiquetas descriptivas de corto puede ser difícil<br /><br />Por lo general no escala más allá de las cinco pestañas en un cuadro de diálogo<br /><br />Inadecuado si tiene demasiados pestañas para una fila (use una técnica alternativa de distribución en capas)<br /><br />No extensible |  
| Exploración de la barra lateral | Dispositivo de conmutación simple que puede dar cabida a más categorías de pestañas<br /><br />Lista plana de categorías (sin jerarquía)<br /><br />Extensible<br /><br />Ejemplo: **personalizar... &gt; Agregar comando** | No es un buen uso de espacio horizontal si hay menos de tres grupos<br /><br />Podrían ser tareas más adecuadas para una lista desplegable |  
| Tree (control) | Permite que las categorías ilimitadas<br /><br />Permite la agrupación o la jerarquía de categorías<br /><br />Extensible<br /><br />Ejemplo: **herramientas &gt; opciones** | Las jerarquías anidadas en gran medida pueden provocar excesivo de desplazamiento horizontal<br /><br />Visual Studio tiene una abundancia de vistas de árbol |  
| Asistente | Ayuda con la finalización de la tarea por guiar al usuario a través de los pasos secuenciales, basado en tareas: el Asistente representa una tarea de alto nivel y los paneles individuales representan las subtareas que necesita para realizar la tarea general<br /><br />Resulta útil cuando la tarea cruza los límites de la interfaz de usuario, como cuando el usuario lo contrario tendría que usar varios editores y las ventanas para completar la tarea<br /><br />Resulta útil cuando la tarea requiere la creación de ramas<br /><br />Resulta útil cuando la tarea contiene las dependencias entre pasos<br /><br />Resulta útil cuando varias tareas similares con la bifurcación de una decisión que se pueden presentar en un cuadro de diálogo para reducir el número de cuadros de diálogo similar diferentes | Inadecuado para cualquier tarea que no requiere un flujo de trabajo secuencial<br /><br />Los usuarios pueden convertirse en abrumado y confunde con un asistente con demasiados pasos<br /><br />Asistentes inherentemente tienen limitado el espacio en pantalla |  
  
##### <a name="hallways-or-dashboards"></a>Vestíbulos o paneles  
Los vestíbulos y los paneles son cuadros de diálogo o paneles que actúan como puntos a otros cuadros de diálogo y ventanas de inicio. El "vestíbulo" bien diseñado inmediatamente presenta solo los más comunes opciones, comandos y configuración, que permite al usuario realizar fácilmente tareas comunes. Como un pasillo reales proporciona entradas para tener acceso a las salas de detrás de ellos, aquí la interfaz de usuario menos comunes se recopila en independientes "salas" (a menudo otros cuadros de diálogo) de funcionalidad relacionada que se puede acceder desde el vestíbulo principal.  
  
Como alternativa, una interfaz de usuario que ofrece toda la funcionalidad disponible en una sola colección, en lugar de la funcionalidad de menos comunes en ubicaciones independientes de refactorización es simplemente un panel.  
  
![El concepto de vestíbulo para exponer la interfaz de usuario adicional en Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 08_Hallway")<br />Concepto de vestíbulo para exponer la interfaz de usuario adicional en Outlook
  
##### <a name="adaptive-ui"></a>UI adaptable  
Mostrar u ocultar la interfaz de usuario en función del uso o una experiencia de usuario automático notificadas es otra manera de presentar la interfaz de usuario necesario al ocultar otras partes. No se recomienda en Visual Studio, como los algoritmos para decidir cuándo se debe mostrar u ocultar la interfaz de usuario pueden ser complicados, y las reglas siempre será incorrecta para un conjunto de casos.  
  
##  <a name="BKMK_Projects"></a> Proyectos  
  
### <a name="projects-in-the-solution-explorer"></a>Proyectos en el Explorador de soluciones  
La mayoría de los proyectos se clasifican como basada en referencias, basado en el directorio o mixto. Los tres tipos de proyectos se admiten simultáneamente en el Explorador de soluciones. La raíz de la experiencia del usuario para trabajar con proyectos tiene lugar dentro de esta ventana. Aunque los nodos de proyecto diferentes son proyectos de tipo de modo mixto, directorio o referencia, hay un patrón de interacción común que debe aplicarse como un punto de partida antes divergentes en patrones de usuario específicos del proyecto.  
  
Los proyectos siempre deben:  
  
-   Compatibilidad con la capacidad para agregar carpetas de proyecto para organizar el contenido del proyecto  
  
-   Mantener un modelo coherente para la persistencia de un proyecto  
  
Los proyectos también deben mantener los modelos de interacción coherente para:  
  
-   Quitar elementos del proyecto  
  
-   Guardar documentos  
  
-   Edición de propiedades de proyecto  
  
-   Editar el proyecto en una vista alternativa  
  
-   Operaciones de arrastrar y colocar  
  
### <a name="drag-and-drop-interaction-model"></a>Modelo de interacción de arrastrar y colocar  
Los proyectos suelen clasificación a sí mismos como basada en referencias (posibilidad de persistir únicamente referencias a elementos de proyecto de almacenamiento), (posibilidad de persistir solo elementos de proyecto físicamente almacenado dentro de la jerarquía de un proyecto), basada en Active o mixto (posibilidad de persistir referencias o elementos físicos). El IDE admite los tres tipos de proyectos simultáneamente en el **el Explorador de soluciones**.  
  
Desde una perspectiva de arrastrar y colocar, deben aplicar las siguientes características para cada tipo de proyecto dentro de la **el Explorador de soluciones**:  
  
-   **Proyecto de referencia:** el punto clave es que el proyecto se está arrastrando en torno a una referencia a un elemento en el almacenamiento. Cuando un proyecto basado en referencias actúa como origen para una operación de movimiento, sólo debe quitar la referencia al elemento del proyecto. El elemento no debe eliminarse realmente desde el disco duro. Cuando un proyecto basado en referencias actúa como un destino de una operación de mover (o copiar), debe agregar una referencia al elemento de origen original sin tener que realizar una copia privada del elemento.  
  
-   **Proyecto basado en el directorio:** desde un punto de vista de arrastrar y colocar, el proyecto arrastrando el elemento físico en lugar de una referencia. Cuando un proyecto basado en el directorio actúa como origen para una operación de movimiento, debe terminar al eliminar el elemento físico desde el disco duro, así como para quitarlo del proyecto. Cuando un proyecto basado en el directorio actúa como un destino de una operación de mover (o copiar), debe realizar una copia del elemento de origen en su ubicación de destino.  
  
-   **Proyecto de destino mixto:** desde un punto de vista de arrastrar y colocar, el comportamiento de este tipo de proyecto se basa en la naturaleza del elemento que se está arrastrando (una referencia a un elemento en el almacenamiento) o el propio elemento. El comportamiento correcto para las referencias y los elementos físicos se han descrito anteriormente.  
  
Si hubiera un único tipo de proyecto en el **el Explorador de soluciones**, entonces serían sencillas operaciones de arrastrar y colocar. Dado que cada sistema del proyecto tiene la capacidad para definir su propio comportamiento de arrastrar y colocar, se deben seguir ciertas instrucciones (según el comportamiento de arrastrar y colocar del explorador de Windows) para garantizar una experiencia de usuario predecible:  
  
-   Arrastre una sin modificar de operación en el **el Explorador de soluciones** (cuando Ctrl ni teclas MAYÚS se mantiene presionado) debe tener como resultado de una operación de movimiento.  
  
-   Operación de arrastre también debería producir una operación de movimiento.  
  
-   Operación de arrastre de CTRL debería producir una operación de copia.  
  
-   Los sistemas de proyectos basada en referencias y mixto admiten la noción de agregar un vínculo (o referencia) al elemento de origen. Cuando estos proyectos son el destino de una operación de arrastrar y colocar (cuando **Ctrl + Mayús** se mantiene presionado), debe dar como resultado una referencia al elemento que se agrega al proyecto  
  
No todas las operaciones de arrastrar y colocar son razonables en combinaciones de proyectos basada en referencias, basada en Active y mixtos. En particular, resulta problemático fingir permitir que una operación de movimiento entre un proyecto basado en el directorio de origen y destino basada en referencias porque el proyecto basado en el directorio de origen tendrá que eliminar el elemento de origen tras la finalización de la migración. El proyecto de destino basado en referencias, a continuación, Baton Rouge acabaría con una referencia a un elemento eliminado.  
  
También es engañoso para fingir permitir que una operación de copia entre estos tipos de proyecto porque el proyecto de destino en función de referencia no debe realizar una copia independiente del elemento de origen. De forma similar, Ctrl + Mayús al arrastrar a un proyecto basado en el directorio de destino no deben permitirse porque no puede conservar las referencias de un proyecto basado en el directorio. En casos donde no se admite la operación de arrastrar y colocar, el IDE debe impedir la colocación y mostrar al usuario el cursor de acción (que se muestra en la siguiente tabla de puntero).  
  
Para implementar correctamente el comportamiento de arrastrar y colocar, el proyecto de origen de la operación de arrastrar debe comunicar su naturaleza al proyecto de destino. (Por ejemplo, es en función de referencia o directorio?) Esta información se indica mediante el formato del Portapapeles que se ofrece por el origen. Como el origen de un arrastre (o la operación de copia del Portapapeles) debe ofrecer un proyecto cualquiera `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` respectivamente, dependiendo de si el proyecto está basado en el directorio o referencia. Ambos formatos de tienen el mismo contenido de datos, que es similar a la Windows `CF_HDROP` formato excepto en que las listas de cadenas, en lugar de nombres de archivo, un doble -`NULL` terminó la lista de `Projref` cadenas (tal como lo devuelve `IVsSolution::GetProjrefOfItem`o `::GetProjrefOfProject` según corresponda).  
  
Como el destino de una lista (o pegar del Portapapeles) y un proyecto debe aceptar ambos `CF_VSREFPROJECTITEMS` y `CF_VSSTGPROJECTITEMS`, aunque el control exacto de la operación de arrastrar y colocar varía según la naturaleza del proyecto de destino y el proyecto de origen. El proyecto de origen declara su naturaleza por si ofrece `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS`. El destino de la operación de colocar comprende su propia naturaleza y, por tanto, tiene información suficiente para tomar decisiones a si un movimiento, copie o vínculo debe realizarse. El usuario modifica también debe realizarse la operación de arrastrar y colocar presionando las teclas Ctrl, MAYÚS, o tanto Ctrl y MAYÚS. Es importante para el destino de colocación indicar correctamente qué operación se realizará de antemano en su `DragEnter` y `DragOver` métodos. El **el Explorador de soluciones** sabe automáticamente si el proyecto de origen y el proyecto de destino son el mismo proyecto.  
  
En concreto no se admite arrastrar los elementos de proyecto a través de las instancias de Visual Studio (por ejemplo, desde una instancia de devenv.exe a otro). El **el Explorador de soluciones** deshabilita también directamente esto.  
  
El usuario siempre debe ser capaz de determinar el efecto de una operación de arrastrar y colocar mediante la selección de un elemento, arrástrelo a la ubicación de destino y observando cuál de los siguientes punteros del mouse aparece antes de que se quita el elemento:  
  
| Puntero del mouse | Comando | Descripción |  
| :---: | --- | --- |  
| ![Mueva el mouse el icono de "no colocar"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | No colocar | No se puede quitar el elemento a la ubicación especificada. |  
| ![Icono de mouse "Copiar"](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | Copiar | Elemento se copiará en la ubicación de destino. |  
| ![Icono de mouse "mover"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Mover | Elemento se moverá a la ubicación de destino. |  
| ![Icono de mouse "Agregar referencia"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Agregar referencia | Se agregará una referencia al elemento seleccionado en la ubicación de destino. |

#### <a name="reference-based-projects"></a>Proyectos basados en la referencia  
 En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar/copiar/pegar) que deben realizarse según la naturaleza de las claves de elemento y el modificador de origen presionado para proyectos de destino basado en hace referencia:  
  
| Modificador | Categoría | Elemento de origen: / vínculo de referencia | Elemento de origen: sistema de elemento o el archivo físico (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Ningún modificador | Acción | Mover | Vínculo |  
| Ningún modificador | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento original |  
| Ningún modificador | Origen | Referencia de eliminaciones al elemento original | Conserva el elemento original |  
| Ningún modificador | Resultado | `DROPEFFECT_MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Mayús + arrastrar | Acción | Mover | No colocar |  
| Mayús + arrastrar | Destino | Agrega la referencia al elemento original | No colocar |  
| Mayús + arrastrar | Origen | Referencia de eliminaciones al elemento original | No colocar |  
| Mayús + arrastrar | Resultado | `DROPEFFECT_MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | No colocar |  
| CTRL + arrastrar | Acción | Copiar | No colocar |  
| CTRL + arrastrar | Destino | Agrega la referencia al elemento original | No colocar |  
| CTRL + arrastrar | Origen | Conserva la referencia al elemento original | No colocar |  
| CTRL + arrastrar | Resultado | `DROPEFFECT_COPY` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | No colocar |  
| Ctrl + Mayús + arrastrar | Acción | Vínculo | Vínculo |  
| Ctrl + Mayús + arrastrar | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento original |  
| Ctrl + Mayús + arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |  
| Ctrl + Mayús + arrastrar | Resultado | `DROPEFFECT_LINK` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Ctrl + Mayús + arrastrar | Nota | Igual que el comportamiento de arrastrar y colocar para los accesos directos en el Explorador de Windows. ||  
| Cortar y pegar | Acción | Mover | Vínculo |  
| Cortar y pegar | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento original |  
| Cortar y pegar | Origen | Conserva la referencia al elemento original|Conserva el elemento original |  
| Cortar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento permanece en la ubicación original en el almacenamiento |  
| Copiar y pegar | Acción | Copiar | Vínculo |  
| Copiar y pegar | Origen | Agrega la referencia al elemento original | Agrega la referencia al elemento original |  
| Copiar y pegar | Resultado | Conserva la referencia al elemento original | Conserva el elemento original |  
| Copiar y pegar | Acción | Elemento permanece en la ubicación original en el almacenamiento | Elemento permanece en la ubicación original en el almacenamiento |  
  
#### <a name="directory-based-projects"></a>Proyectos basados en el directorio  
En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar/copiar/pegar) que deben realizarse según la naturaleza de las claves de elemento y el modificador de origen presionado para proyectos de destino basado en el directorio:  
  
| Modificador | Categoría | Elemento de origen: / vínculo de referencia | Elemento de origen: sistema de elemento o el archivo físico (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Ningún modificador | Acción | Mover | Mover |  
| Ningún modificador | Destino | Elemento de copia a la ubicación de destino | Elemento de copia a la ubicación de destino |  
| Ningún modificador | Origen | Referencia de eliminaciones al elemento original | Referencia de eliminaciones al elemento original | | Ningún modificador | Resultado | `DROPEFFECT_MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Mayús + arrastrar | Acción | Mover | Mover |  
| Mayús + arrastrar | Destino | Elemento de copia a la ubicación de destino | Elemento de copia a la ubicación de destino |  
| Mayús + arrastrar | Origen | Referencia de eliminaciones al elemento original | Elimina el elemento de ubicación original |
| Mayús + arrastrar | Resultado | `DROPEFFECT_MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| CTRL + arrastrar | Acción | Copiar | Copiar |  
| CTRL + arrastrar | Destino | Elemento de copia a la ubicación de destino | Elemento de copia a la ubicación de destino |  
| CTRL + arrastrar | Origen | Conserva la referencia al elemento original | Conserva la referencia al elemento original |  
| CTRL + arrastrar | Resultado | `DROPEFFECT_COPY` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_COPY` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Ctrl + Mayús + arrastrar | | No colocar | No colocar |  
| Cortar y pegar | Acción | Mover | Mover |  
| Cortar y pegar | Destino | Elemento de copia a la ubicación de destino | Elemento de copia a la ubicación de destino |  
| Cortar y pegar | Origen | Referencia de eliminaciones al elemento original | Elimina el elemento de ubicación original |  
| Cortar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento se elimina de la ubicación original en el almacenamiento |  
| Copiar y pegar | Acción | Copiar | Copiar |  
| Copiar y pegar | Destino | Agrega la referencia al elemento original | Elemento de copia a la ubicación de destino |  
| Copiar y pegar | Origen | Conserva el elemento original | Conserva el elemento original |  
| Copiar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento permanece en el almacenamiento de inicios de ubicación original |
  
#### <a name="mixed-target-projects"></a>Proyectos destino mixto  
En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar/copiar/pegar) que deben realizarse según la naturaleza de las claves de elemento y el modificador de origen presionado para proyectos destino mixto:  
  
| Modificador | Categoría | Elemento de origen: / vínculo de referencia | Elemento de origen: sistema de elemento o el archivo físico (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Ningún modificador | Acción | Mover | Mover |
| Ningún modificador | Destino | Agrega la referencia al elemento original | Elemento de copia a la ubicación de destino |
| Ningún modificador | Origen | Referencia de eliminaciones al elemento original | Referencia de eliminaciones al elemento original |
| Ningún modificador | Resultado | `DROPEFFECT_ MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE` se devuelve como acción de `::Drop` y elemento se elimina de la ubicación original en el almacenamiento |
| Mayús + arrastrar | Acción | Mover | Mover |
| Mayús + arrastrar | Destino | Agrega la referencia al elemento original | Elemento de copia a la ubicación de destino |
| Mayús + arrastrar | Origen | Referencia de eliminaciones al elemento original | Elimina el elemento de ubicación original | 
| Mayús + arrastrar | Resultado | `DROPEFFECT_ MOVE` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE` se devuelve como acción de `::Drop` y elemento se elimina de la ubicación original en el almacenamiento |
| CTRL + arrastrar | Acción | Copiar | Copiar |
| CTRL + arrastrar | Destino | Agrega la referencia al elemento original | Elemento de copia a la ubicación de destino |
| CTRL + arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| CTRL + arrastrar | Resultado | `DROPEFFECT_ COPY` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ COPY` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |
| Ctrl + Mayús + arrastrar | Acción | Vínculo | Vínculo |
| Ctrl + Mayús + arrastrar | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento de origen original |
| Ctrl + Mayús + arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| Ctrl + Mayús + arrastrar | Resultado | `DROPEFFECT_ LINK` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ LINK` se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |
| Cortar y pegar | Acción | Mover | Mover |
| Cortar y pegar | Destino | Elemento de copia a la ubicación de destino | Elemento de copia a la ubicación de destino |
| Cortar y pegar | Origen | Referencia de eliminaciones al elemento original | Elimina el elemento de ubicación original |
| Cortar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento se elimina de la ubicación original en el almacenamiento |
| Copiar y pegar | Acción | Copiar | Copiar |
| Copiar y pegar | Destino | Agrega la referencia al elemento original | Elemento de copia a la ubicación de destino |
| Copiar y pegar | Origen | Conserva el elemento original | Conserva el elemento original |
| Copiar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento permanece en la ubicación original en el almacenamiento |
  
Estos detalles deben tenerse en cuenta al implementar arrastrar en el **el Explorador de soluciones**:  
  
-   Diseño para varios escenarios de selección.  
  
-   Los nombres de archivo (ruta de acceso completa) deben ser únicos en el proyecto de destino o no se debe permitir la operación de colocar.  
  
-   Los nombres de carpeta deben ser únicos (mayúsculas y minúsculas) en el nivel que se van a quitar.  
  
-   Hay diferencias de comportamiento entre los archivos abiertos o cerrados en tiempo de arrastre (no se menciona en los escenarios anteriores).  
  
-   Archivos de nivel superior se comportan de manera ligeramente diferente a los archivos en carpetas.  
  
Otro problema que hay que tener en cuenta es cómo controlar las operaciones de movimiento de los elementos que tienen editores o diseñadores abiertos. El comportamiento esperado es como sigue (se aplica a todos los tipos de proyecto):  
  
1.  Si el diseñador o editor abierto no tiene los cambios no guardados, a continuación, la ventana del editor o diseñador debe estar en modo silencioso cerrada.  
  
2.  Si el diseñador o editor abierto tiene cambios no guardados, el origen de la operación de arrastrar debe esperar para que la eliminación se producen y, a continuación, pida al usuario que guarde los cambios no confirmados en los documentos abiertos antes de cerrar la ventana con un mensaje similar al siguiente :  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Esto proporciona al usuario la oportunidad de guardar el trabajo en curso antes de que el destino hace que sus copias. Un nuevo método `IVsHierarchyDropDataSource2::OnBeforeDropNotify` agregada para habilitar este control.  
  
El destino, a continuación, copiará el estado del elemento como en el almacenamiento de información (sin incluir los cambios no guardados en el editor si el usuario eligió **n**). Después de que el destino ha completado su copia (en `IVsHierarchyDropDataSource::Drop`), el origen tiene la oportunidad de completar la parte de la eliminación de la operación de movimiento (en `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Los editores con los cambios no guardados se deben dejar abiertos. Para aquellos documentos con los cambios no guardados, esto significa que se realizará la parte de la copia de la operación de mover, pero se anulará la parte de la eliminación. En un escenario de selección múltiple cuando el usuario elige **No**, esos documentos con los cambios no guardados no se cierra o quitados, pero los que no tienen cambios no guardados se deben cerrar y quitar.