---
title: "Patrones de aplicación para Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 7c2612cb537a6f3197cf9f99a0dc11981dfc73e1
ms.contentlocale: es-es
ms.lasthandoff: 05/04/2017

---
# <a name="application-patterns-for-visual-studio"></a>Patrones de aplicación para Visual Studio
##  <a name="BKMK_WindowInteractions"></a>Interacciones de ventana  
  
### <a name="overview"></a>Información general  
Los dos tipos de ventana principal que se usa en Visual Studio son editores de documento y ventanas de herramientas. Raras, pero posible, es grandes cuadros de diálogo no modales. Aunque se trata todas las no modal en el shell, sus modelos son fundamentalmente diferentes. En esta sección se explica la diferencia entre las ventanas de documento, las ventanas de herramientas y cuadros de diálogo no modales. Patrones de cuadro de diálogo modal se tratan en [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Comparación de patrones de uso de ventana  
**Las ventanas de documento** casi siempre se muestran correctamente en el documento. Esto ofrece al editor el documento "fase center" para organizar las ventanas de herramienta complementaria alrededor.  
  
A **ventana de herramientas** más a menudo se muestra como una ventana independiente, menor contraída en el borde del IDE. Esto puede ser visible, oculto u oculta automáticamente. Sin embargo, en ocasiones, se presentan las ventanas de herramientas dentro del documento y, para ello, desactive la **ventana/acoplamiento** propiedad en la ventana. Esto da como resultado más inmobiliaria, pero también decisión de diseño común: al intentar integrar en Visual Studio, debe decidir si la característica debe mostrar una ventana de herramientas o una ventana de documento.  
  
**Los cuadros de diálogo no modales** se desaconseja en Visual Studio. Los cuadros de diálogo no modales más son, por definición, las ventanas de herramientas flotantes y de este modo se deben haber implementado. Los cuadros de diálogo no modales se permiten en casos donde el tamaño de una ventana de herramientas normal acoplada a un lado del shell podría ser demasiado limitado. También se permiten en casos donde los usuarios puedan deducir fácilmente mover el cuadro de diálogo a un monitor secundario.  
  
Cree cuidadosamente sobre qué tipo de contenedor que necesita. Consideraciones de patrón de uso común para el diseño de la interfaz de usuario están en la tabla siguiente.  
  
||Ventana de documento|Ventana de herramientas|Cuadro de diálogo no modal|  
|-|---------------------|-----------------|---------------------|  
| **Posición** | Situada en el documento bien siempre y no acoplar alrededor de los bordes del IDE. Se pueden "extraerse" para que flote hasta llegar por separado desde el shell principal. | Generalmente acopladas mediante fichas alrededor de los bordes del IDE, pero puede ser personalizada puede observarse, oculta automáticamente (unpinned) o acoplar dentro del documento también.|Ventana flotante grande independiente desde el IDE. |  
| **Confirmar modelo** | *Confirmación diferida*<br /><br /> Para guardar los datos en un documento, el usuario debe emitir el **archivo &gt; guardar**, **Guardar como**, o **guardar todo** comando. Una ventana de documento tiene el concepto de los datos que contiene "sucia", a continuación, se confirma en uno de la operación de guardar comandos. Al cerrar una ventana de documento, todo el contenido se guarda en el disco o perdido. | *Confirmación inmediata*<br /><br /> No hay ningún Guardar modelo. Para ventanas de herramientas del inspector que ayudan en la edición de un archivo, el archivo debe estar abierto en el editor o diseñador activo y el editor o diseñador posee la operación de guardar. | *Confirmación demorada o inmediata*<br /><br /> A menudo, un cuadro de diálogo no modal grande requiere una acción para confirmar los cambios y permite una operación "Cancelar", que se reviertan los cambios realizados en la sesión de diálogo.  Esta diferencia de un cuadro de diálogo no modal de una ventana de herramientas en que las ventanas de herramientas siempre tienen un modelo de confirmación inmediata. |  
| **Visibilidad** | *Abrir/crear (archivo) y cerrar*<br /><br /> Abrir una ventana de documento se realiza a través de abrir un documento existente o usar una plantilla para crear un nuevo documento. No hay ninguna "abrir \<específica del editor >" comando. | *Ocultar y mostrar*<br /><br /> Las ventanas de herramientas de instancia única se oculta o se muestra. Contenido y los Estados dentro de la ventana de herramientas conservan si visible u oculto. Ventanas de herramientas de varias instancias pueden ser cerradas así como ocultos. Cuando se cierra una ventana de herramientas de varias instancias, se descarta el contenido y el estado de la ventana de herramientas. | *Iniciar desde un comando*<br /><br /> Los cuadros de diálogo se inician desde un comando basado en tareas. |  
| **Instancias** | *Varias instancias*<br /><br /> Varios editores pueden estar abiertos al mismo tiempo y edición de archivos diferente, mientras que algunos editores permiten también el mismo archivo esté abierto en más de un editor (mediante la **ventana &gt; nueva ventana** comando).<br /><br /> Un único editor puede modificar uno o varios archivos al mismo tiempo (Diseñador de proyectos). | *Instance único o varios*<br /><br /> Contenido cambia para reflejar el contexto (como en el Explorador de propiedades) o error de inserción y contexto de foco en otras ventanas (lista de tareas, el Explorador de soluciones).<br /><br /> Ventanas de herramientas de instancia única y varias instancias deben estar asociadas a la ventana del documento activo a menos que haya una razón de peso no a. | *Instancia única* |  
| **Ejemplos** | **Editores de texto**, al igual que el editor de código<br /><br /> **Superficies de diseño**, como un diseñador de formularios o una superficie de modelado<br /><br /> **Controlar diseños similares a los cuadros de diálogo**, al igual que el Diseñador de manifiestos | El **el Explorador de soluciones** proporciona una solución y proyectos dentro de la solución<br /><br /> El **Explorador de servidores** proporciona una vista jerárquica de las conexiones de servidores y los datos que el usuario elige abrir en la ventana. Abrir un objeto de la jerarquía de la base de datos, como una consulta, abre una ventana de documento y permite al usuario editar la consulta.<br /><br /> El **Examinador de propiedades** muestra las propiedades para el objeto seleccionado en una ventana de documento o en otra ventana de herramientas. Las propiedades se presentan en una vista de cuadrícula jerárquica o en los controles de tipo cuadro de diálogo complejos y permiten al usuario establecer los valores de esas propiedades. | |  
  
##  <a name="BKMK_ToolWindows"></a>Ventanas de herramientas  
  
### <a name="overview"></a>Información general  
Ventanas de herramientas admiten el trabajo del usuario que se produce en las ventanas de documento. Puede utilizar para mostrar una jerarquía que representa un objeto raíz fundamentales que proporciona Visual Studio y se puede manipular.  
  
Cuando piense en una nueva ventana de herramientas en el IDE, los autores deben:  
  
-   Utilizar ventanas de herramientas existente adecuado para la tarea y no crear nuevos con una funcionalidad similar. Solo deben crearse nuevas ventanas de herramientas si ofrecen una significativamente diferente "herramienta" o la funcionalidad que no se puede integrar en una ventana similar, o mediante la activación de una ventana existente a un concentrador de dinamización.  
  
-   Usar una barra de comandos estándar, si es necesario, en la parte superior de la ventana de herramientas.  
  
-   Ser coherente con patrones ya está presentes en otras ventanas de herramientas de exploración de presentación y el teclado de control.  
  
-   Ser coherente con la presentación del control en otras ventanas de herramientas.  
  
-   Asegúrese de ventanas de herramientas específicas del documento visibles automáticamente cuando sea posible, para que aparezcan solo cuando se activa el documento principal.  
  
-   Asegúrese de que su contenido de la ventana es navegable mediante el teclado (teclas de dirección de soporte técnico).  
  
#### <a name="tool-window-states"></a>Estados de la ventana de herramienta  
Ventanas de herramientas de Visual Studio tienen distintos Estados, algunos de los cuales están activados en el usuario (por ejemplo, la característica Ocultar automáticamente). Otros Estados, como visibles automáticamente, permitir que las ventanas de herramientas que aparezcan en el contexto correcto y ocultar cuando no sea necesario. Hay cinco estados de la ventana de herramienta en total.  
  
-   **Acoplar/anclado** las ventanas de herramientas se pueden adjuntar a cualquiera de los cuatro lados del área del documento. Aparece el icono de alfiler en la barra de título de ventana de herramientas. La ventana de herramientas se puede acoplar horizontal o verticalmente a lo largo del borde de shell y otras ventanas de herramientas y también se pueden vincular a la pestaña.  
  
-   **Oculta automáticamente** ventanas de herramientas son liberadas. La ventana puede deslizar fuera de la vista, dejando una pestaña (con el nombre de la ventana de herramientas y su icono) en el borde del área del documento. La ventana de herramientas se desliza hacia afuera cuando un usuario mantiene el mouse sobre la pestaña.  
  
-   **Visibles automáticamente** las ventanas de herramientas aparecen automáticamente al otro elemento de interfaz de usuario, como un editor, se inicia o recibe el foco.  
  
-   **Flotante** las ventanas de herramientas mantenga el mouse fuera del IDE. Esto es útil para las configuraciones de varios monitores.  
  
-   **Fichas** las ventanas de herramientas se pueden acoplar dentro del documento también. Esto es útil para las ventanas de herramientas de gran tamaño, como el Explorador de objetos, que necesitan más inmobiliaria de acoplamiento con los bordes del marco que permite.  
  
![Estados de la ventana de herramientas en Visual Studio](~/docs/extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Estados de la ventana de herramientas en Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Instancia única y varias instancias  
Las ventanas de herramientas son la única instancia o varias instancias. Algunas ventanas de herramientas de instancia única podrían estar asociados con la ventana de documento activo, mientras que las ventanas de herramientas de varias instancias pueden no tenerlos. Ventanas de herramientas de varias instancias responden a la **ventana &gt; nueva ventana** comando mediante la creación de una nueva instancia de la ventana. La siguiente imagen ilustra una ventana de herramienta que permite el comando nueva ventana cuando se active una instancia de la ventana:  
  
![Habilitar comando 'Nueva ventana' cuando está activa una instancia de la ventana de ventana de herramientas](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Habilitar comando 'Nueva ventana' cuando está activa una instancia de la ventana de ventana de herramientas  
  
Las ventanas de herramientas de instancia única se pueden ocultas o muestran, mientras que las ventanas de herramientas de varias instancias pueden cerradas, así como ocultos. Todas las ventanas de herramientas se pueden acoplar, vinculada a la ficha, flotante o establecer como una ventana secundaria de interfaz de múltiples documentos (MDI) (similar a una ventana de documento). Todas las ventanas de herramienta deben responder a los comandos de administración de la ventana correspondiente en el menú de ventana:  
  
![Comandos de administración de la ventana en el menú de la ventana de Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandos de administración de la ventana en el menú de la ventana de Visual Studio
  
#### <a name="document-specific-tool-windows"></a>Ventanas de herramientas específicas del documento  
Algunas ventanas de herramientas están diseñadas para cambian en función de un determinado tipo de documento. Estas ventanas se actualizan continuamente para reflejar funciones aplicables a la ventana de documento activo en el IDE.  
  
El cuadro de herramientas y el esquema del documento, son ejemplos de las ventanas de herramientas cuyo contenido cambia para reflejar el editor seleccionado. Estas ventanas muestran una marca de agua cuando un editor tiene el foco que no proporciona el contexto de la ventana.  
  
#### <a name="navigable-list-tool-windows"></a>Ventanas de herramientas de lista navegable  
Algunas ventanas de herramientas muestran una lista de elementos navegables, con que el usuario puede interactuar. En este tipo de ventana, siempre debería haber comentarios para el elemento actual en la lista, incluso si la ventana está inactiva. La lista debe responder a la **GoToNextLocation** y **GoToPrevLocation** comandos cambiando también el elemento seleccionado actualmente en la ventana  
  
Ejemplos de ventanas de herramientas de lista navegable son el Explorador de soluciones y la ventana de resultados de la búsqueda.  
  
### <a name="tool-window-types"></a>Tipos de ventana de herramienta  
  
#### <a name="common-tool-windows-and-their-functions"></a>Ventanas de herramientas comunes y sus funciones

**Ventanas de herramientas jerárquica**
| Ventana de herramientas | Función | 
| --- | --- | 
| Explorador de soluciones | Árbol jerárquico que muestra una lista de los documentos contenidos en los elementos de la solución, proyectos y archivos varios. La presentación de los elementos dentro de los proyectos se define mediante el paquete al que pertenece el tipo de proyecto (por ejemplo, los tipos de basada en referencias, directorio o en modo mixto). | 
| Vista de clases | Un árbol jerárquico de las clases y los diversos elementos del espacio de trabajo de documentos, independientemente de los propios archivos. | 
| Explorador de servidores | Árbol jerárquico que muestra todas las conexiones de servidores y los datos en la solución. | 
| Esquema del documento | La estructura jerárquica del documento activo. | 

**Ventanas de herramientas de cuadrícula**
| Ventana de herramientas | Función | 
| --- | --- | 
| Propiedades | Una cuadrícula que muestra una lista de propiedades para el objeto seleccionado, junto con los selectores de valor pueden editar dichas propiedades. | 
| Lista de tareas | Una cuadrícula que permite al usuario crear, editar o eliminar tareas y comentarios. | 

**Ventanas de herramientas de contenido**
| Ventana de herramientas | Función | 
| --- | --- | 
| Ayuda | Una ventana que permite a los usuarios acceso a los distintos métodos de obtención de ayuda, en "¿cómo?" vídeos a los foros MSDN. | 
| Ayuda dinámica | Una ventana de herramientas que muestra vínculos a temas aplicables a la selección actual de ayuda. | 
| Examinador de objetos | Un conjunto de marcos de dos columnas con una lista de componentes de objetos jerárquico en el panel izquierdo y el objeto propiedades y métodos en la columna derecha. | 

**Ventanas de herramientas del cuadro de diálogo**
| Ventana de herramientas | Función | 
| --- | --- | 
| Find | Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución. |
| Búsqueda avanzada | Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución. | 

**Otras ventanas de herramientas**
| Ventana de herramientas | Función | 
| --- | --- | 
| Cuadro de herramientas | La ventana de herramientas que se utiliza para almacenar los elementos que se van a quitar en superficies de diseño, proporcionando un origen de arrastre coherente para todos los diseñadores. |
| Página de inicio | Portal del usuario a Visual Studio, con acceso a las fuentes de noticias de los desarrolladores, la Ayuda de Visual Studio y proyectos recientes. Los usuarios también pueden crear páginas de inicio personalizada copiando el archivo StartPage.xaml desde el "Common7\IDE\StartPages\" directorio de archivos de programa de Visual Studio a la carpeta StartPages en el directorio de documentos de Visual Studio y, a continuación, modificando el código XAML a mano o ábralo en Visual Studio u otro editor de código. | 

**Las ventanas de herramientas del depurador**
| Ventana de herramientas | Función | 
| --- | --- |
| Automático ||  
| Inmediato ||  
| Salida | La ventana de salida se pueden usar cuando tiene eventos textuales o estado a declarar. |  
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
  
##  <a name="BKMK_DocumentEditorConventions"></a>Convenciones de editor de documentos  
  
### <a name="document-interactions"></a>Interacciones de documento  
"Document bien" es el mayor espacio en el IDE y es donde el usuario generalmente centra su atención para completar sus tareas, asistidas por las ventanas de herramientas adicionales. Editores de documento representan las unidades fundamentales de trabajo que el usuario se abre y se guarda dentro de Visual Studio. Conservan un sentido sólido de selección vinculada a un explorador de soluciones o en otras ventanas de la jerarquía activa. El usuario debería poder apuntar a una de las ventanas de la jerarquía y saber dónde se encuentra el documento y su relación a la solución, el proyecto u otro objeto de raíz proporcionado por un paquete de Visual Studio.  
  
Edición de documentos, requiere una experiencia de usuario coherente. Para permitir al usuario centrarse en la tarea en cuestión en lugar de en la administración de ventanas y buscar comandos, seleccione una estrategia de vista de documento que mejor se adapte a las tareas de usuario para la edición de ese tipo de documento.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interacciones habituales para el cuadro de documento  
  
-   Mantener un modelo coherente de interacción en common **nuevo archivo** y **archivos abiertos** experiencias.  
  
-   Actualizar la funcionalidad relacionada en los menús y ventanas relacionadas cuando se abre la ventana de documento.  
  
-   Comandos de menú se integran correctamente en menús comunes como **editar**, **formato**, y **vista** menús. Si hay una cantidad considerable de comandos especializadas, puede crearse un nuevo menú. Este menú nuevo debe ser visible solo cuando el documento tiene el foco.  
  
-   Una barra de herramientas incrustada se puede colocar en la parte superior del editor. Esto es preferible a tener una barra de herramientas independiente que aparece fuera del editor.  
  
-   Mantenga siempre una selección en el Explorador de soluciones o activo similar ventana jerarquía.  
  
-   Haga doble clic en un documento en el Explorador de soluciones debe realizar la misma acción que **abiertos**.  
  
-   Si más de un editor puede utilizarse en un tipo de documento, el usuario debería poder invalidar o restablecer la acción predeterminada en un tipo de documento determinado mediante la **abrir con** cuadro de diálogo, haga doble clic en el archivo y seleccione **abrir con** en el menú contextual.  
  
-   No, un asistente en un documento se compilan correctamente.  
  
### <a name="user-expectations-for-specific-document-types"></a>Expectativas del usuario para los tipos de documento específico  
Hay varios tipos básicos de editores de documento y cada uno tiene un conjunto de interacciones que sean coherentes con otros usuarios del mismo tipo.  
  
-   **Editor de texto:** editor de código, archivos de registro  
  
-   **Superficie de diseño:** WPF forms diseñadores, formularios Windows forms  
  
-   **Editor de estilo de cuadro de diálogo:** Diseñador de manifiestos, propiedades del proyecto  
  
-   **Diseñador de modelos:** el Diseñador de flujo de trabajo, codemap, diagrama de arquitectura, progresión  
  
También hay varios tipos de no sean del editor que se utiliza también el documento. Mientras que no edición documentos en Sí, que es necesario que siga interacciones estándar para las ventanas de documento.  
  
-   **Informes:** IntelliTrace informe, Hyper-V, informe del generador de perfiles  
  
-   **Panel:** concentrador de diagnósticos  
  
#### <a name="text-based-editors"></a>Editores basados en texto  
  
-   El documento participa en el modelo de pestaña de vista previa, lo que permite obtener una vista previa del documento sin necesidad de abrirlo.  
  
-   La estructura del documento se puede representar dentro de una ventana de herramientas complementarias, por ejemplo, un esquema de documento.  
  
-   IntelliSense (si procede) se comportará de forma coherente con otros editores de código.  
  
-   Elementos emergentes o asistencia UI siga estilos y patrones similares para la interfaz de usuario similar existente, como CodeLens.  
  
-   Mensajes relacionados con el estado del documento se presentará en un control de barra de información en la parte superior del documento o en la barra de estado.  
  
-   El usuario debe poder personalizar la apariencia de las fuentes y colores mediante un **Herramientas > opciones** página, la página fuentes y colores compartida o uno específico para el editor.  
  
#### <a name="design-surfaces"></a>Superficies de diseño  
  
-   Un diseñador vacío debe tener una marca de agua en la superficie que indica cómo empezar a trabajar.  
  
-   Cambiar de vista mecanismos seguirá patrones existentes como haga doble clic para abrir un editor de código o pestañas en la ventana de documento que permite la interacción con dos paneles.  
  
-   Agregar elementos a la superficie de diseño debe hacerse a través del cuadro de herramientas, a menos que sea necesaria una ventana de herramientas muy específico.  
  
-   Elementos en la superficie sigue un modelo coherente de selección.  
  
-   Barras de herramientas incrustadas contienen comandos únicamente, no es común de los comandos específicos del documento como **guardar**.  
  
#### <a name="dialog-style-editors"></a>Editores de estilo de cuadro de diálogo  
  
-   El diseño de controles debería seguir las convenciones de diseño de cuadro de diálogo normal.  
  
-   Tabulaciones en el editor no deberían coincidir con la apariencia de las pestañas del documento, debe coincidir con uno de los dos estilos de pestaña interiores permitidos.  
  
-   Los usuarios deben poder interactuar con los controles mediante el teclado ya sea mediante el editor de activación y tabulación a través de controles o mediante el uso de teclas de acceso estándar.  
  
-   El diseñador debe usar common Guardar modelo. No guardar general o botones de confirmación deben colocarse en la superficie, aunque otros botones que pueden ser apropiado.  
  
#### <a name="model-designers"></a>Diseñadores de modelos  
  
-   Un diseñador vacío debe tener una marca de agua en la superficie que indica cómo empezar a trabajar.  
  
-   Agregar elementos a la superficie de diseño debe hacerse a través del cuadro de herramientas.  
  
-   Elementos en la superficie sigue un modelo coherente de selección.  
  
-   Barras de herramientas incrustadas contienen comandos únicamente, no es común de los comandos específicos del documento como **guardar**.  
  
-   Una leyenda puede aparecer en la superficie, indicativa o una marca de agua.  
  
-   El usuario debe poder personalizar la apariencia de las fuentes o colores con una **Herramientas > opciones** página, la página fuentes y colores compartida o uno específico para el editor.  
  
#### <a name="reports"></a>Informes  
  
-   Los informes son normalmente de solo información y no participan en el modelo de guardar. Sin embargo, pueden incluir interacción como vínculos a otras secciones que expanden y contraen o información relevante.  
  
-   Mayoría de los comandos en la superficie de debe ser hipervínculos, botones no.  
  
-   Diseño debe incluir un encabezado y siga las instrucciones de diseño de informe estándar.  
  
#### <a name="dashboards"></a>Paneles  
  
-   Paneles no tienen un modelo de interacción por sí mismos, pero actúan como un medio para ofrecen una variedad de otras herramientas.  
  
-   No participan en el modelo de guardar.  
  
-   Los usuarios deben poder interactuar con los controles mediante el teclado, activando el editor y desplazarse a través de controles o mediante el uso de teclas de acceso estándar.  
  
##  <a name="BKMK_Dialogs"></a>Cuadros de diálogo  
  
### <a name="introduction"></a>Introducción  
Los cuadros de diálogo en Visual Studio normalmente deben admitir una unidad discreta de trabajo del usuario y, a continuación, se descarta.  
  
Si ha determinado que tiene un cuadro de diálogo, tiene tres opciones, en orden de preferencia:  
  
1.  Integrar características en uno de los cuadros de diálogo compartidos en Visual Studio.  
  
2.  Crear su propio cuadro de diálogo con un patrón que se encuentra en un cuadro de diálogo similar existente.  
  
3.  Crear un nuevo cuadro de diálogo, interacción siguiente y directrices de diseño.  
  
En esta sección se describe cómo elegir el patrón de diálogo correctos dentro de los flujos de trabajo de Visual Studio y las convenciones comunes para el diseño del cuadro de diálogo.  
  
### <a name="themes"></a>Temas  
Los cuadros de diálogo en Visual Studio siguen uno de estos dos estilos básicos:  
  
#### <a name="standard-unthemed"></a>Estándar (unthemed)  
La mayoría de los cuadros de diálogo son los cuadros de diálogo de la utilidad estándar y debe ser unthemed. No no controles comunes de plantilla nuevo o intenta crear botones "moderno" estilizados o controles. Controles y el aspecto de chrome siga [instrucciones de interacción de escritorio de Windows estándar para cuadros de diálogo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Con temas  
Los cuadros de diálogo de Especialidad "firma" pueden ser con temas. Cuadros de diálogo con temas tienen un aspecto distinto, que también tiene algunos patrones de interacción especiales asociados con el estilo. Tema de su cuadro de diálogo solo si cumple estos requisitos:  
  
-   El cuadro de diálogo es una experiencia común que se pueden ver y utilizar con frecuencia o varios usuarios (por ejemplo, el **nuevo proyecto** cuadro de diálogo.  
  
-   El cuadro de diálogo contiene los elementos de la marca de producto destacado (por ejemplo, el **configuración de la cuenta** cuadro de diálogo).  
  
-   El cuadro de diálogo aparece como una parte integral de un flujo mayor que incluye otros cuadros de diálogo con temas (por ejemplo, el **Agregar servicio conectado** cuadro de diálogo).  
  
-   El cuadro de diálogo es una parte importante de una experiencia que desempeña un papel estratégico de promocionar o diferenciar una versión del producto.  
  
Al crear un cuadro de diálogo con temas, utilice los colores de entorno adecuadas y siga el diseño correcto y los patrones de interacción. (Consulte [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Diseño del cuadro de diálogo  
Los cuadros de diálogo bien diseñadas tendrá los siguientes elementos en cuenta:  
  
-   La tarea de usuario que se admita  
  
-   El estilo de texto del cuadro de diálogo, el idioma y la terminología  
  
-   Elección de control y convenciones de la interfaz de usuario  
  
-   Alineación de especificación y el control de diseño Visual  
  
-   Acceso mediante el teclado  
  
#### <a name="content-organization"></a>Organización del contenido  
Tenga en cuenta las diferencias entre estos tipos básicos de los cuadros de diálogo:  
  
-   [Los cuadros de diálogo simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentar controles en una sola ventana modal. La presentación podría incluir variaciones de patrones de control complejo, como un selector de campo o una barra de iconos.  
  
-   [Capas de los cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se utilizan para realizar el máximo de espacio en pantalla cuando un único fragmento de la interfaz de usuario consta de varios grupos de controles. Agrupaciones de cuadro de diálogo se "capas" a través de controles de fichas, controles de lista de navegación o botones para que el usuario puede elegir que la agrupación para ver en un momento dado.  
  
-   [Asistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) son útiles para dirigir al usuario a través de una secuencia lógica de pasos hacia la finalización de una tarea. Se ofrecen una serie de opciones en paneles secuenciales, a veces, introducción a diferentes flujos de trabajo ("ramas") depende de una elección realizada en el panel anterior.  
  
####  <a name="BKMK_SimpleDialogs"></a>Cuadros de diálogo simples  
Un cuadro de diálogo simple es una presentación de controles en una sola ventana modal. Esta presentación podría incluir variaciones de patrones de control complejo, como un selector de campo. Para los cuadros de diálogo simples, siga el diseño general estándar, así como cualquier diseño específico necesarios para las agrupaciones de control complejo.
  
![> Crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Crear clave de nombre seguro es un ejemplo de un cuadro de diálogo simple en Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a>Cuadros de diálogo en capas  
Los cuadros de diálogo superpuestas incluyen pestañas, paneles y los árboles incrustados. Se utilizan para maximizar el estado real cuando hay varios grupos de controles que se ofrecen en un único fragmento de la interfaz de usuario. Las agrupaciones se disponen en capa para que el usuario puede elegir que la agrupación para ver en cualquier momento.  
  
En el caso más sencillo, el mecanismo para cambiar entre las agrupaciones es un control de pestaña. Hay varias alternativas disponibles. Consulte dar prioridad a y capas de cómo elegir el estilo más adecuado.  
  
El **herramientas &gt; opciones** cuadro de diálogo es un ejemplo de un cuadro de diálogo en capas con un árbol incrustado:  
  
![Herramientas > opciones es un ejemplo de un cuadro de diálogo por capas en Visual Studio.](~/docs/extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Herramientas > opciones es un ejemplo de un cuadro de diálogo por capas en Visual Studio.
  
####  <a name="BKMK_Wizards"></a>Asistentes  
Asistentes son útiles para dirigir al usuario a través de una secuencia lógica de pasos en la realización de una tarea. Se ofrecen una serie de opciones en paneles secuenciales y el usuario debe seguir a través de cada paso antes de continuar con la siguiente. Una vez que existen suficientes valores predeterminados, el **finalizar** botón está habilitado.  
  
 Modales asistentes se utilizan para tareas que:  
  
-   Contienen bifurcaciones, donde se ofrecen diferentes rutas de acceso según las opciones de usuario  
  
-   Contiene las dependencias entre los pasos, donde los pasos subsiguientes dependen proporcionados por el usuario de los pasos anteriores  
  
-   Son lo suficientemente compleja que se debe usar la interfaz de usuario para explicar las opciones disponibles y los posibles resultados de cada paso  
  
-   Son transaccionales, que requieren un conjunto de pasos para completar en su totalidad antes de confirmados los cambios  
  
### <a name="common-conventions"></a>Convenciones comunes  
Para lograr un diseño óptimo y funcionalidad con los cuadros de diálogo, siga estas convenciones de tamaño del cuadro de diálogo, posición, estándares, configuración de control y alineación, interfaz de usuario texto, barras de título, botones de control y las teclas de acceso.  
  
Para obtener instrucciones específicas del diseño, vea [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Tamaño  
Los cuadros de diálogo deben ajustarse a una resolución mínima de pantalla de 1024 x 768 y tamaño inicial del cuadro de diálogo no debe superar los 900 x 700 píxeles. Los cuadros de diálogo que puede cambiar el tamaño, pero no es un requisito.  
  
Hay dos recomendaciones para los cuadros de diálogo puede cambiar el tamaño:  
  
1.  Que está definido para el cuadro de diálogo que se optimizan para el conjunto de controles sin recortes y se ajusta para adaptarse al crecimiento de localización razonable un tamaño mínimo.  
  
2.  Que el tamaño de la escala de usuario se conserva entre sesiones. Por ejemplo, si el usuario cambia un cuadro de diálogo a 150%, vuelva a iniciarse el cuadro de diálogo se mostrará en 150%.  
  
#### <a name="position"></a>Posición  
Los cuadros de diálogo deben aparecer centrados en el IDE en el primer inicio. La última posición de los cuadros de diálogo invariable no tiene que sea persistente, por lo que aparecerán centrados en las versiones posteriores. 

Para los cuadros de diálogo puede cambiar el tamaño, el tamaño debe conservarse en las versiones posteriores. Para cambiar el tamaño cuadros de diálogo modales, no necesita la posición que se deben conservar. Mostrarlos centrado en el IDE, evita la posibilidad de que el cuadro de diálogo que aparece en una posición imprevisible o inutilizable cuando ha cambiado la configuración de pantalla del usuario. 

Cuadros de diálogo no modales que pueden cambiar de posición, la posición del usuario debe mantenerse en las versiones posteriores, en el cuadro de diálogo puede utilizarse con frecuencia como una parte integral de un flujo de trabajo mayor.  
  
Cuando los cuadros de diálogo deben generar otros cuadros de diálogo, debe actuar en cascada en el cuadro de diálogo superior a la derecha y en profundidad desde el elemento primario para que resulte obvio para el usuario que ha navegado a un nuevo sitio.  
  
#### <a name="modality"></a>Modalidad  
Modal está significa que los usuarios son necesarios para completar o cancelar el cuadro de diálogo antes de continuar. Puesto que los cuadros de diálogo modales impiden al usuario interactuar con otras partes del entorno, flujo de tareas de la característica debe utilizarlos como con moderación como sea posible. Cuando una operación modal es necesaria, Visual Studio tiene un número de cuadros de diálogo compartidos en que puede integrar características. Si tiene que crear un nuevo cuadro de diálogo, siga el patrón de interacción de un cuadro de diálogo existente con una funcionalidad similar.  
  
Cuando los usuarios necesitan realizar dos actividades al mismo tiempo, como puede ser **buscar** y **reemplazar** al escribir código nuevo, el cuadro de diálogo debe ser no modal para que el usuario puede cambiar fácilmente entre ellos. Por lo general, Visual Studio utiliza las ventanas de herramientas para este tipo de compatibilidad con el editor de la tarea vinculada.  
  
#### <a name="control-configuration"></a>Configuración de control  
Sea coherente con las configuraciones existentes de control que llevan a cabo lo mismo en Visual Studio.  
  
#### <a name="title-bars"></a>Barras de título  
  
-   El texto en la barra de título debe reflejar el nombre del comando que se inició.  
  
-   Icono de que no debe usarse en barras de título del cuadro de diálogo. En casos donde el sistema requiere que uno, usar el logotipo de Visual Studio.  
  
-   Los cuadros de diálogo no es necesario minimizar o maximizar botones.  
  
-   Botones de ayuda en la barra de título han quedado en desuso. No se agregan a los cuadros de diálogo nuevo. Cuando existen, debe iniciar un tema de ayuda es conceptualmente relevante para la tarea.  
  
 ![Especificaciones de guía para las barras de título en los cuadros de diálogo de Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Especificaciones de guía para las barras de título en los cuadros de diálogo de Visual Studio
  
#### <a name="control-buttons"></a>Botones de control  
En general, **Aceptar**, **cancelar**, y **ayuda** botones deberían estar organizados horizontalmente en la esquina inferior derecha del cuadro de diálogo. Si un cuadro de diálogo tiene varios otros botones en la parte inferior del cuadro de diálogo que se presenta visual confusión con los botones de control, se permite la pila vertical alternativa.  
  
![Configuraciones aceptables para los botones de control en los cuadros de diálogo de Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configuraciones aceptables para los botones de control en los cuadros de diálogo de Visual Studio
  
El cuadro de diálogo debe incluir un botón del control de forma predeterminada. Para determinar el comando recomendado para usar como predeterminado, elija una de las siguientes opciones (que se muestran en orden de prioridad):  
  
-   Elija el comando más seguro y más seguro como el valor predeterminado. Esto significa que se elige el comando más probable evitar una pérdida de datos y acceso al sistema no deseadas.  
  
-   Si la seguridad y la pérdida de datos no están factores, a continuación, elija el comando predeterminado en función de su comodidad. Incluyendo el comando como el valor predeterminado es más probable que mejorará el flujo de trabajo del usuario cuando el cuadro de diálogo admite tareas repetitivas o frecuentes.  
  
Evite elegir una acción destructiva permanentemente para el comando predeterminado. Si hay un comando de ese tipo, elija un comando más seguro como el valor predeterminado en su lugar.  
  
#### <a name="access-keys"></a>Teclas de acceso  
No utilice las teclas de acceso para **Aceptar**, **cancelar**, o **ayuda** botones. Estos botones se asignan a teclas de método abreviado de forma predeterminada:  
  
| Nombre del botón | Método abreviado de teclado |  
| --- | --- |  
| Aceptar | Entrar |  
| Cancelar | Esc |  
| Ayuda | F1 |  
  
#### <a name="imagery"></a>Imágenes  
Usar imágenes con moderación en los cuadros de diálogo. No usar iconos grandes en los cuadros de diálogo simplemente para usar un espacio. Usar imágenes sólo si son una parte importante de transmisión del mensaje para el usuario, como los iconos de advertencia o animaciones de estado.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a>Establecer prioridades y disponer en capas  
  
#### <a name="prioritizing-your-ui"></a>Dar prioridad a la interfaz de usuario  
Puede que sea necesario suponen ciertos elementos de interfaz de usuario a la vanguardia y comportamiento más avanzada y opciones de (incluidos los comandos oscuros) en los cuadros de diálogo. Incorpore la funcionalidad de uso frecuente a la vanguardia crear espacio para él y hacerlo visible de forma predeterminada en la interfaz de usuario con una etiqueta de texto cuando se muestre el cuadro de diálogo.  
  
#### <a name="layering-your-ui"></a>Capas de la interfaz de usuario  
Si ha determinado que un cuadro de diálogo es necesario, pero las funciones relacionadas que desea presentar al usuario va más allá de lo que se pueden mostrar en un cuadro de diálogo simple, debe disponer en capas de la interfaz de usuario. Visual Studio utiliza los métodos de capas más comunes son las pestañas y vestíbulos o paneles. En algunos casos, las regiones que se pueden expandir y contraer podrían ser adecuadas. Interfaz de usuario adaptable por lo general no se recomienda en Visual Studio.  
  
Hay ventajas y desventajas a diferentes métodos de capas de interfaz de usuario a través de los controles de ficha similar. Revise la lista siguiente para asegurarse de que ha elegido una técnica de distribución en capas que se ajuste a su situación.  
  
##### <a name="tabbing"></a>Tabulación  
  
| Mecanismo de cambio | Ventajas y el uso apropiado | Uso inadecuado y desventajas |  
| --- | --- | --- |  
| Control Tab | Agrupar lógicamente páginas de diálogo en conjuntos relacionados<br /><br />Útil para menos de cinco (o el número de etiquetas que caben en una fila en el cuadro de diálogo) páginas de controles relacionados en el cuadro de diálogo<br /><br />Pestaña etiquetas deben ser cortas: una o dos palabras que pueden identificar con facilidad el contenido<br /><br />Un estilo de cuadro de diálogo común de sistema<br /><br />Ejemplo: **Explorador de archivos &gt; propiedades de los elementos** | Hacer etiquetas descriptivas de cortas puede ser difícil<br /><br />Por lo general no se escala más allá de las cinco pestañas en un cuadro de diálogo<br /><br />Inadecuado si tiene demasiados pestañas para una fila (utilice una técnica de distribución en capas alternativo)<br /><br />No extensible |  
| Exploración en barra lateral | Dispositivo de conmutación simple que puede dar cabida a más categorías de pestañas<br /><br />Lista plana de categorías (sin jerarquía)<br /><br />Extensible<br /><br />Ejemplo: **personalizar... &gt; Agregar (comando)** | No es un buen uso del espacio horizontal si hay menos de tres grupos<br /><br />Podría ser tarea más adecuada para una lista desplegable |  
| Tree (control) | Permite categorías ilimitados<br /><br />Permite la agrupación o la jerarquía de categorías<br /><br />Extensible<br /><br />Ejemplo: **herramientas &gt; opciones** | Jerarquías muy anidadas pueden provocar excesivo de desplazamiento horizontal<br /><br />Visual Studio tiene una sobreabundancia de vistas de árbol |  
| Asistente | Ayuda con la finalización de la tarea por guiar al usuario por pasos basado en tareas y secuenciales: el Asistente representa una tarea de alto nivel y los paneles individuales representan subtareas necesarias para realizar la tarea general<br /><br />Resulta útil cuando la tarea cruza los límites de la interfaz de usuario, como cuando el usuario en caso contrario tendría que usar varios editores y herramientas de windows para completar la tarea<br /><br />Resulta útil cuando la tarea requiere la bifurcación<br /><br />Resulta útil cuando la tarea contiene dependencias entre los pasos<br /><br />Resulta útil cuando varias tareas similares con la bifurcación de una decisión se pueden presentar en un cuadro de diálogo para reducir el número de cuadros de diálogo similar diferentes | Apropiado para cualquier tarea que no requiere un flujo de trabajo secuencial<br /><br />Los usuarios pueden ser abrumado y confunde con un asistente con demasiados pasos<br /><br />Asistentes inherentemente tenga limitado el espacio real en pantalla |  
  
##### <a name="hallways-or-dashboards"></a>Vestíbulos o paneles  
Vestíbulos y los paneles son cuadros de diálogo o paneles que actúan como iniciar otros cuadros de diálogo y ventanas de destino. El "vestíbulo" bien diseñado inmediatamente superficies sólo los más comunes opciones, comandos y configuración, que permite al usuario realizar con rapidez las tareas habituales. Aquí como un vestíbulo reales proporciona entradas para tener acceso a los centros de detrás de ellos, la interfaz de usuario de menos común se recopila en salas separadas a"" (a menudo otros cuadros de diálogo) de funciones relacionadas con la que puede tener acceso desde el vestíbulo principal.  
  
O bien, una interfaz de usuario que ofrece toda la funcionalidad disponible en una sola colección en lugar de la funcionalidad de menos común en ubicaciones independientes la refactorización es simplemente un panel.  
  
![Concepto de vestíbulo para exponer la interfaz de usuario adicional en Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concepto de vestíbulo para exponer la interfaz de usuario adicional en Outlook
  
##### <a name="adaptive-ui"></a>Interfaz de usuario adaptable  
Mostrar u ocultar la interfaz de usuario basada en uso o una experiencia de usuario incluido en sí mismo es otra manera de presentar la interfaz de usuario es necesario al tiempo que oculta otros componentes. No se recomienda en Visual Studio, como los algoritmos para decidir cuándo se debe mostrar u ocultar la interfaz de usuario pueden ser complicados y las reglas siempre será incorrecta para algún conjunto de casos.  
  
##  <a name="BKMK_Projects"></a>Proyectos  
  
### <a name="projects-in-the-solution-explorer"></a>Proyectos en el Explorador de soluciones  
Mayoría de los proyectos se clasifica como basada en referencias, basado en el directorio o mixto. Los tres tipos de proyectos se admiten simultáneamente en el Explorador de soluciones. La raíz de la experiencia del usuario cuando se trabaja con proyectos tiene lugar dentro de esta ventana. Aunque los nodos de proyectos diferentes son referencia, directorio o proyectos de tipos de modo mixto, hay un patrón de interacción común que se debe aplicar como punto de partida antes divergentes en patrones de usuario específica del proyecto.  
  
Siempre deben proyectos:  
  
-   Compatibilidad con la capacidad de agregar las carpetas de proyecto para organizar el contenido del proyecto  
  
-   Mantener un modelo coherente de persistencia de un proyecto  
  
Los proyectos también deben mantener los modelos de interacción coherente para:  
  
-   Quitar elementos de proyecto  
  
-   Guardar documentos  
  
-   Edición de propiedades de proyecto  
  
-   Editar el proyecto en una vista alternativa  
  
-   Operaciones de arrastrar y colocar  
  
### <a name="drag-and-drop-interaction-model"></a>Modelo de interacción de arrastrar y colocar  
Proyectos normalmente clasificación por sí mismos como basada en referencias (puede conservar sólo hace referencia a los elementos de proyecto de almacenamiento), (puede conservar los elementos de proyecto solo físicamente almacenado en la jerarquía del proyecto), basada en directorios o mixto (puede conservar las referencias o elementos físicos). El IDE admite los tres tipos de proyectos al mismo tiempo en el **el Explorador de soluciones**.  
  
Desde una perspectiva de arrastrar y colocar, deben aplicar las siguientes características para cada tipo de proyecto dentro de la **el Explorador de soluciones**:  
  
-   **Proyecto de referencia:** el punto clave es que el proyecto está arrastrando alrededor de una referencia a un elemento de almacenamiento. Cuando un proyecto basado en la referencia actúa como origen para una operación de movimiento, sólo debe quitar la referencia al elemento del proyecto. El elemento no debe eliminarse realmente desde el disco duro. Cuando un proyecto basado en la referencia actúa como un destino de una operación de mover (o copiar), debe agregar una referencia al elemento de origen original sin realizar una copia privada del elemento.  
  
-   **Proyecto basado en el directorio:** desde un punto de vista de arrastrar y colocar, el proyecto arrastrando el elemento físico en lugar de una referencia. Cuando un proyecto basado en el directorio actúa como origen para una operación de movimiento, debe terminar eliminando el elemento físico de la unidad de disco duro, así como para quitarlo del proyecto. Cuando un proyecto basado en el directorio actúa como un destino de una operación de mover (o copiar), debe realizar una copia del elemento de origen en su ubicación de destino.  
  
-   **Proyecto de destino mixto:** desde un punto de vista de arrastrar y colocar, el comportamiento de este tipo de proyecto se basa en la naturaleza del elemento que se está arrastrando (una referencia a un elemento de almacenamiento) o el propio elemento. El comportamiento correcto para referencias y los elementos físicos descritos anteriormente.  
  
Si hubiera un solo tipo de proyecto en el **el Explorador de soluciones**, entonces se sencillo operaciones de arrastrar y colocar. Dado que cada sistema de proyecto tiene la capacidad para definir su propio comportamiento de arrastrar y colocar, se deben seguir ciertas instrucciones (en función del comportamiento de arrastrar y colocar el Explorador de Windows) para asegurar una experiencia de usuario predecible:  
  
-   Un sin modificar la operación de arrastrar la **el Explorador de soluciones** (cuando Ctrl ni Mayús se presionaba) debe tener como resultado de una operación de movimiento.  
  
-   También debe provocar la operación de arrastre de desplazamiento en una operación de movimiento.  
  
-   Operación de arrastre CTRL debe dar como resultado de una operación de copia.  
  
-   Sistemas del proyecto basada en referencias y mixto admiten la noción de agregar un vínculo (o referencia) al elemento de origen. Cuando estos proyectos son el destino de una operación de arrastrar y colocar (cuando **Ctrl + Mayús** se mantiene presionado), debe dar como resultado una referencia al elemento que se agrega al proyecto  
  
No todas las operaciones de arrastrar y colocar son razonables en combinaciones de proyectos basada en referencias, basado en el directorio y mixtos. En particular, es problemático para hacerse pasar por una operación de movimiento entre un proyecto basado en el directorio de origen y destino basada en referencias de permiso porque el proyecto basado en el directorio de origen tendrá que eliminar el elemento de origen cuando se complete el movimiento. El proyecto de referencia en función de destino, a continuación, podría acabar con una referencia a un elemento eliminado.  
  
También es dar lugar a confusión Finjan permitir que una operación de copia entre estos tipos de proyecto porque el proyecto de referencia en función de destino no debe realizar una copia independiente del elemento de origen. De forma similar, Ctrl + Mayús al arrastrar a un proyecto basado en el directorio de destino no deberían estar permitido porque no puede conservar las referencias de un proyecto basado en el directorio. En casos donde no se admite la operación de arrastrar y colocar, el IDE debe impedir la eliminación y mostrar al usuario el cursor no colocar (se muestra en la tabla de puntero siguiente).  
  
Para implementar correctamente el comportamiento de arrastrar y colocar, el proyecto de origen de la operación de arrastrar debe comunicar su naturaleza en el proyecto de destino. (Por ejemplo, es en función de referencia o de directorio?) Esta información se indica mediante el formato del Portapapeles que ofrece el origen. Como el origen de un arrastre (o la operación de copia del Portapapeles) un proyecto debe ofrecer una `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` respectivamente, dependiendo de si el proyecto está basado en el directorio o referencia. Ambos formatos de tienen el mismo contenido de datos, que es similar a las ventanas `CF_HDROP` formato salvo que haya listas de cadenas, en lugar de nombres de archivo, un doble -`NULL` terminada en lista de `Projref` cadenas (tal como lo devuelve `IVsSolution::GetProjrefOfItem` o `::GetProjrefOfProject` según corresponda).  
  
Como el destino de una lista (o la operación Pegar del Portapapeles.), un proyecto debe aceptar ambos `CF_VSREFPROJECTITEMS` y `CF_VSSTGPROJECTITEMS`, aunque el tratamiento de la operación de arrastrar y colocar exacto varía según la naturaleza del proyecto de destino y el proyecto de origen. El proyecto de origen declara su naturaleza por si ofrece `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS`. El destino de la operación de colocar comprende su propia naturaleza y, por tanto, tiene información suficiente para tomar decisiones a si un movimiento, copie o vínculo que debe realizarse. El usuario modifica también qué operación de arrastrar y colocar debe realizarse presionando la tecla Ctrl, MAYÚS, o tanto teclas Ctrl y MAYÚS. Es importante para el destino de colocación indicar correctamente la operación que se realizará de antemano en su `DragEnter` y `DragOver` métodos. El **el Explorador de soluciones** automáticamente sabe si el proyecto de origen y el proyecto de destino son el mismo proyecto.  
  
En concreto no se admite al arrastrar elementos de proyecto en todas las instancias de Visual Studio (por ejemplo, desde una instancia de devenv.exe a otro). El **el Explorador de soluciones** directamente deshabilita esto.  
  
El usuario siempre debe ser capaz de determinar el efecto de una operación de arrastrar y colocar seleccionando un elemento, arrástrela hasta la ubicación de destino y observando cuál de los siguientes punteros del mouse aparece antes de que se quita el elemento:  
  
| Puntero del mouse | Comando | Descripción |  
| :---: | --- | --- |  
| ![Icono de mouse "no colocar"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | No colocar | No se puede quitar el elemento a la ubicación especificada. |  
| ![Icono de mouse "Copiar"](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | Copiar | Se copiará el elemento a la ubicación de destino. |  
| ![Icono de mouse "mover"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Mover | Elemento se moverán a la ubicación de destino. |  
| ![Icono de mouse "Agregar referencia"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Agregar referencia | Una referencia al elemento seleccionado se agregará a la ubicación de destino. |

#### <a name="reference-based-projects"></a>Proyectos basados en la referencia  
 En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que deben realizarse en función de la naturaleza de las claves de producto y el modificador de origen le presionada con los proyectos de destino basado en la referencia:  
  
| Modificador | Categoría | Elemento de origen: / vínculo de referencia | Elemento de origen: sistema de elemento o el archivo físico (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Ningún modificador | Acción | Mover | Vínculo |  
| Ningún modificador | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento original |  
| Ningún modificador | Origen | Referencia de las eliminaciones al elemento original | Conserva el elemento original |  
| Ningún modificador | Resultado | `DROPEFFECT_MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Mayús + arrastrar | Acción | Mover | No colocar |  
| Mayús + arrastrar | Destino | Agrega la referencia al elemento original | No colocar |  
| Mayús + arrastrar | Origen | Referencia de las eliminaciones al elemento original | No colocar |  
| Mayús + arrastrar | Resultado | `DROPEFFECT_MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | No colocar |  
| CTRL + arrastrar | Acción | Copiar | No colocar |  
| CTRL + arrastrar | Destino | Agrega la referencia al elemento original | No colocar |  
| CTRL + arrastrar | Origen | Conserva la referencia al elemento original | No colocar |  
| CTRL + arrastrar | Resultado | `DROPEFFECT_COPY`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | No colocar |  
| Ctrl + Mayús + arrastrar | Acción | Vínculo | Vínculo |  
| Ctrl + Mayús + arrastrar | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento original |  
| Ctrl + Mayús + arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |  
| Ctrl + Mayús + arrastrar | Resultado | `DROPEFFECT_LINK`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_LINK`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
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
En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que deben realizarse en función de la naturaleza de las claves de producto y el modificador de origen le presionada con los proyectos de destino basado en el directorio:  
  
| Modificador | Categoría | Elemento de origen: / vínculo de referencia | Elemento de origen: sistema de elemento o el archivo físico (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Ningún modificador | Acción | Mover | Mover |  
| Ningún modificador | Destino | Elemento de copias para la ubicación de destino | Elemento de copias para la ubicación de destino |  
| Ningún modificador | Origen | Referencia de las eliminaciones al elemento original | Referencia de las eliminaciones al elemento original | | Ningún modificador | Resultado | `DROPEFFECT_MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Mayús + arrastrar | Acción | Mover | Mover |  
| Mayús + arrastrar | Destino | Elemento de copias para la ubicación de destino | Elemento de copias para la ubicación de destino |  
| Mayús + arrastrar | Origen | Referencia de las eliminaciones al elemento original | Elimina el elemento de ubicación original |
| Mayús + arrastrar | Resultado | `DROPEFFECT_MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| CTRL + arrastrar | Acción | Copiar | Copiar |  
| CTRL + arrastrar | Destino | Elemento de copias para la ubicación de destino | Elemento de copias para la ubicación de destino |  
| CTRL + arrastrar | Origen | Conserva la referencia al elemento original | Conserva la referencia al elemento original |  
| CTRL + arrastrar | Resultado | `DROPEFFECT_COPY`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_COPY`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |  
| Ctrl + Mayús + arrastrar | | No colocar | No colocar |  
| Cortar y pegar | Acción | Mover | Mover |  
| Cortar y pegar | Destino | Elemento de copias para la ubicación de destino | Elemento de copias para la ubicación de destino |  
| Cortar y pegar | Origen | Referencia de las eliminaciones al elemento original | Elimina el elemento de ubicación original |  
| Cortar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento se elimina de la ubicación original en el almacenamiento |  
| Copiar y pegar | Acción | Copiar | Copiar |  
| Copiar y pegar | Destino | Agrega la referencia al elemento original | Elemento de copias para la ubicación de destino |  
| Copiar y pegar | Origen | Conserva el elemento original | Conserva el elemento original |  
| Copiar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento permanece en el almacenamiento de inicios de ubicación original |
  
#### <a name="mixed-target-projects"></a>Proyectos de destino mixto  
En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que deben realizarse en función de la naturaleza de las claves de producto y el modificador de origen le presionada con los proyectos de destino mixto:  
  
| Modificador | Categoría | Elemento de origen: / vínculo de referencia | Elemento de origen: sistema de elemento o el archivo físico (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Ningún modificador | Acción | Mover | Mover |
| Ningún modificador | Destino | Agrega la referencia al elemento original | Elemento de copias para la ubicación de destino |
| Ningún modificador | Origen | Referencia de las eliminaciones al elemento original | Referencia de las eliminaciones al elemento original |
| Ningún modificador | Resultado | `DROPEFFECT_ MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE`se devuelve como acción de `::Drop` y se elimina el elemento de la ubicación original en el almacenamiento |
| Mayús + arrastrar | Acción | Mover | Mover |
| Mayús + arrastrar | Destino | Agrega la referencia al elemento original | Elemento de copias para la ubicación de destino |
| Mayús + arrastrar | Origen | Referencia de las eliminaciones al elemento original | Elimina el elemento de ubicación original | 
| Mayús + arrastrar | Resultado | `DROPEFFECT_ MOVE`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ MOVE`se devuelve como acción de `::Drop` y se elimina el elemento de la ubicación original en el almacenamiento |
| CTRL + arrastrar | Acción | Copiar | Copiar |
| CTRL + arrastrar | Destino | Agrega la referencia al elemento original | Elemento de copias para la ubicación de destino |
| CTRL + arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| CTRL + arrastrar | Resultado | `DROPEFFECT_ COPY`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ COPY`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |
| Ctrl + Mayús + arrastrar | Acción | Vínculo | Vínculo |
| Ctrl + Mayús + arrastrar | Destino | Agrega la referencia al elemento original | Agrega la referencia al elemento de origen original |
| Ctrl + Mayús + arrastrar | Origen | Conserva la referencia al elemento original | Conserva el elemento original |
| Ctrl + Mayús + arrastrar | Resultado | `DROPEFFECT_ LINK`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento | `DROPEFFECT_ LINK`se devuelve como acción de `::Drop` y elemento permanece en la ubicación original en el almacenamiento |
| Cortar y pegar | Acción | Mover | Mover |
| Cortar y pegar | Destino | Elemento de copias para la ubicación de destino | Elemento de copias para la ubicación de destino |
| Cortar y pegar | Origen | Referencia de las eliminaciones al elemento original | Elimina el elemento de ubicación original |
| Cortar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento se elimina de la ubicación original en el almacenamiento |
| Copiar y pegar | Acción | Copiar | Copiar |
| Copiar y pegar | Destino | Agrega la referencia al elemento original | Elemento de copias para la ubicación de destino |
| Copiar y pegar | Origen | Conserva el elemento original | Conserva el elemento original |
| Copiar y pegar | Resultado | Elemento permanece en la ubicación original en el almacenamiento | Elemento permanece en la ubicación original en el almacenamiento |
  
Estos detalles deben tenerse en cuenta al implementar arrastrar la **el Explorador de soluciones**:  
  
-   Diseño de varios escenarios de selección.  
  
-   Nombres de archivo (ruta de acceso completa) deben ser únicos en el proyecto de destino o la línea de unión no debería estar permitido.  
  
-   Nombres de carpeta deben ser únicos (entre mayúsculas y minúsculas) en el nivel que se van a quitar.  
  
-   Hay diferencias de comportamiento entre los archivos que están abiertos o cerrados al tiempo de arrastre (no mencionada en los escenarios anteriores).  
  
-   Archivos de nivel superior se comportan de forma ligeramente diferente a archivos en carpetas.  
  
Otro problema a tener en cuenta es cómo controlar las operaciones de movimiento en los elementos que tienen editores o diseñadores abiertos. El comportamiento esperado es como se indica a continuación (se aplica a todos los tipos de proyecto):  
  
1.  Si el diseñador o editor abierto no tiene los cambios no guardados, a continuación, la ventana del editor o diseñador debe estar en modo silencioso cerrada.  
  
2.  Si el diseñador o editor abierto tiene cambios no guardados, el origen de la operación de arrastrar debe esperar para que la eliminación se producen y, a continuación, pida al usuario guardar los cambios sin confirmar en los documentos abiertos antes de cerrar la ventana con un mensaje similar al siguiente:  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Esto proporciona al usuario la oportunidad de guardar el trabajo en curso antes de que el destino haga sus copias. Un nuevo método `IVsHierarchyDropDataSource2::OnBeforeDropNotify` se ha agregado al habilitar este control.  
  
El destino, a continuación, copiará el estado del elemento porque está en almacenamiento de información (sin incluir los cambios no guardados en el editor de si el usuario decidió **n**). Después de que el destino ha completado su copia (en `IVsHierarchyDropDataSource::Drop`), el origen tiene la oportunidad de completar la parte de la eliminación de la operación de desplazamiento (en `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Los editores sin guardar los cambios, deben dejarse abiertos. Para aquellos documentos que tengan los cambios no guardados, esto significa que se llevará a cabo la parte de la copia de la operación de movimiento, pero se anulará la parte de eliminación. En un escenario de selección múltiple cuando el usuario elige **n**, esos documentos sin guardar los cambios no se deberían cerrarse o quitarse, pero las que no tienen cambios no guardados se deben cerrar y quitar.
